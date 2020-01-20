---
title: リモートのデバイスとアプリのコマンド実行 (Android)
description: このガイドでは、リモートのデバイスやアプリを検出してから、アプリを起動したり、アプリ サービスと対話したりする方法について説明します。
ms.topic: article
keywords: microsoft, windows, project rome, コマンド実行, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: bb58b8340dcd8158a201ce670ef0b69ba0272b6f
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115566"
---
# <a name="implementing-device-relay-for-android"></a><span data-ttu-id="46125-104">Android のデバイス リレーの実装</span><span class="sxs-lookup"><span data-stu-id="46125-104">Implementing device relay for Android</span></span>

<span data-ttu-id="46125-105">Project Rome のデバイス リレー機能は、2 つの主な機能であるリモート起動 (コマンド実行とも呼びます) とアプリ サービスをサポートする一連の API で構成されています。</span><span class="sxs-lookup"><span data-stu-id="46125-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="46125-106">リモート起動 API は、リモート デバイス上のプロセスがローカル デバイスから開始されるシナリオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="46125-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="46125-107">たとえば、ユーザーが車に乗りながら電話でラジオを聴きますが、帰宅したらホーム ステレオに接続した Xbox に電話を使用して再生を転送することがあります。</span><span class="sxs-lookup"><span data-stu-id="46125-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="46125-108">アプリケーションは App Services API を使用して 2 つのデバイス間に永続的なパイプラインを確立し、任意の内容を含むメッセージをこのパイプライン経由で送信することができます。</span><span class="sxs-lookup"><span data-stu-id="46125-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="46125-109">たとえば、モバイル デバイス上で実行されている写真共有アプリが、写真を取得するためにユーザーの PC との接続を確立することができます。</span><span class="sxs-lookup"><span data-stu-id="46125-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="46125-110">Project Rome の機能は、Connected Devices Platform と呼ばれる基盤プラットフォームによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="46125-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="46125-111">このガイドでは、Connected Devices Platform を初めて使用するために必要な手順と、このプラットフォームを使用してデバイス リレー関連機能を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="46125-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement Device Relay related features.</span></span>

<span data-ttu-id="46125-112">この手順では、[Project Rome Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)のコードを参照します。</span><span class="sxs-lookup"><span data-stu-id="46125-112">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="46125-113">プラットフォームの使用</span><span class="sxs-lookup"><span data-stu-id="46125-113">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="46125-114">リモートのデバイスとアプリの検出</span><span class="sxs-lookup"><span data-stu-id="46125-114">Discover remote devices and apps</span></span>

<span data-ttu-id="46125-115">**RemoteSystemWatcher** インスタンスは、このセクションのコア機能を処理します。</span><span class="sxs-lookup"><span data-stu-id="46125-115">A **RemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="46125-116">これは、リモート システムを検出するクラスの中で宣言します。</span><span class="sxs-lookup"><span data-stu-id="46125-116">Declare it in the class which is to discover remote systems.</span></span>

```Java
private RemoteSystemWatcher mWatcher = null;
```

<span data-ttu-id="46125-117">ウォッチャーを作成してデバイスの検出を開始する前に、検出フィルターを追加して、どのような種類のデバイスをアプリでターゲットにするかを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="46125-117">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="46125-118">ユース ケースに応じて、これらはユーザーの入力によって決定、またはアプリにハードコードすることができます。</span><span class="sxs-lookup"><span data-stu-id="46125-118">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

```Java
private void onStartWatcherClicked() {
    // RemoteSystemWatcher cannot be started unless the platform is 
    // initialized and the user is logged in. It may be helpful to use
    // methods like these to track the state of the application.
    // See the sample app for their implementations.
    if (!getMainActivity().isSignedIn()) {
        return;
    }
    if (!getMainActivity().isPlatformInitialized()) {
        return;
    }

    // create and populate a list of filters. The filter choices below are arbitrary.
    ArrayList<RemoteSystemFilter> filters = new ArrayList<>();

    /*  RemoteSystemDiscoveryType filters can be used to filter the types of Remote Systems you discover.
    Possible values:
        ANY(0),
        PROXIMAL(1),
        CLOUD(2),
        SPATIALLY_PROXIMAL(3)
    */
    filters.add(new RemoteSystemDiscoveryTypeFilter(RemoteSystemDiscoveryType.ANY));

    /*  RemoteSystemStatusType filters can be used to filter the status of Remote Systems you discover.
    Possible values:
        ANY(0),
        AVAILABLE(1)
    */
    filters.add(new RemoteSystemStatusTypeFilter(RemoteSystemStatusType.AVAILABLE));


    /*  RemoteSystemKindFilter can filter the types of devices you want to discover.
    Possible values are members of the RemoteSystemKinds class.
    */
    String[] kinds = new String[] { RemoteSystemKinds.Phone(), RemoteSystemKinds.Tablet() };

    RemoteSystemKindFilter kindFilter = new RemoteSystemKindFilter(kinds);
    filters.add(kindFilter);

    /*  RemoteSystemAuthorizationKind determines the category of user whose system(s) you want to discover.
    Possible values:
        SAME_USER(0),
        ANONYMOUS(1)
    */
    filters.add(new RemoteSystemAuthorizationKindFilter(RemoteSystemAuthorizationKind.SAME_USER)); 
    // ...
```

<span data-ttu-id="46125-119">この時点で、アプリはウォッチャー オブジェクトを初期化できます。これによって、検出されたデバイスをアプリで解析する方法、またそれらのデバイスとアプリが対話する方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="46125-119">At this point, the app can initialize the watcher object which determine how your app will parse and interact with devices that are discovered.</span></span>

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

<span data-ttu-id="46125-120">(**RemoteSystem** インスタンスで表される) 検出されたデバイスのセットをアプリで管理し、利用可能なデバイスとそのアプリについての情報 (表示名やデバイスの種類など) を UI に表示することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="46125-120">It is recommended that your app maintain a set of discovered devices (represented by **RemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="46125-121">次のクラス スタブは、ウォッチャー インスタンスのイベント リスナーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="46125-121">The following class stubs can be used as event listeners for the watcher instance.</span></span>

```Java
private class RemoteSystemAddedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // add instance "remoteSystem" to program memory. See sample for full implementation.
    }
}

private class RemoteSystemUpdatedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // update instance "remoteSystem" in program memory. See sample for full implementation.
    }
}

private class RemoteSystemRemovedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // remove instance "remoteSystem" from program memory. See sample for full implementation.
    }
}

private class RemoteSystemWatcherErrorOccurredListener implements EventListener<RemoteSystemWatcher, RemoteSystemWatcherError> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystemWatcherError remoteSystemWatcherError) {
        // handle the error
    }
}
```

<span data-ttu-id="46125-122">`mWatcher.start` が呼び出されると、リモート システムのアクティビティの監視が始まります。デバイスが検出、更新、または検出済みデバイスのセットから削除されると、イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="46125-122">Once `mWatcher.start` is called, it will begin watching for remote system activity and will raise events when devices are discovered, updated, or removed from the set of discovered devices.</span></span> <span data-ttu-id="46125-123">バックグラウンドで継続的にスキャンされるため、不必要なネットワーク通信やバッテリの消耗を避けるために、不要になったらウォッチャーを停止することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="46125-123">It will scan continuously in the background, so it is recommended that you stop the watcher when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

```Java
// if you call this from the activity's onPause method, you ensure that
// it will stop when the activity exits the foreground.
public void stopWatcher() {
    if (mWatcher == null) {
        return;
    }
    mWatcher.stop();
}
```
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="46125-124">ユース ケースの例: リモート起動とリモート アプリ サービスの実装</span><span class="sxs-lookup"><span data-stu-id="46125-124">Example use case: implementing remote launching and remote app services</span></span>

<span data-ttu-id="46125-125">コードのこの時点で、利用可能なデバイスを参照する **RemoteSystem** オブジェクトの有効な一覧があるはずです。</span><span class="sxs-lookup"><span data-stu-id="46125-125">At this point in your code, you should have a working list of **RemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="46125-126">これらのデバイスに対して何をするかは、アプリの機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="46125-126">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="46125-127">主な種類の対話は、リモート起動とリモート アプリ サービスです。</span><span class="sxs-lookup"><span data-stu-id="46125-127">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="46125-128">これらについては、以降のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="46125-128">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="46125-129">A) リモート起動</span><span class="sxs-lookup"><span data-stu-id="46125-129">A) Remote launching</span></span>

<span data-ttu-id="46125-130">次のコードは、これらのデバイスのいずれかを選択し (UI コントロールを使って行われるのが理想的です)、**RemoteLauncher** を使用して、アプリと互換性のある URI を渡してそのデバイス上でアプリを起動する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="46125-130">The following code shows how to select one of these devices (ideally this is done through a UI control) and then use **RemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span> 

<span data-ttu-id="46125-131">重要な注意点として、リモート起動でターゲットにできるのはリモート デバイス_または_そのデバイス上の特定のリモート アプリケーションであり、前者の場合、指定された URI を、ホスト デバイスがその URI スキーム用の既定のアプリで起動します。</span><span class="sxs-lookup"><span data-stu-id="46125-131">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span> 

<span data-ttu-id="46125-132">前のセクションで説明したように、検出はまずデバイス レベルで行われます (**RemoteSystem** はデバイスを表します) が、**RemoteSystem** インスタンスの `getApplications` メソッドを呼び出して **RemoteSystemApp** オブジェクトの配列を取得することができます。これらのオブジェクトが表すのは、(前述の準備手順で独自のアプリを登録したのと同様に) Connected Devices Platform を使用するように登録されている、リモート デバイス上のアプリです。</span><span class="sxs-lookup"><span data-stu-id="46125-132">As the previous section demonstrated, discovery happens at the device level first (a **RemoteSystem** represents a device), but you can call the `getApplications` method on a **RemoteSystem** instance to get an array of **RemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="46125-133">**RemoteSystem** と **RemoteSystemApp** のどちらを使用しても、URI を起動するために必要な **RemoteSystemConnectionRequest** を作成できます。</span><span class="sxs-lookup"><span data-stu-id="46125-133">Both **RemoteSystem** and **RemoteSystemApp** can be used to construct a **RemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

```java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the launch operation
// is called.
private RemoteSystem target; 

// ...

/**
* Responsible for calling into the Rome API to launch the given URI and provides
* the logic to handle the RemoteLaunchUriStatus response.
* @param uri URI to launch
* @param target The target for the launch URI request
*/
private void launchUri(final String uri, final RemoteSystem target, final long messageId)
{
    RemoteLauncher remoteLauncher = new RemoteLauncher();

    AsyncOperation<RemoteLaunchUriStatus> resultOperation = remoteLauncher.launchUriAsync(new RemoteSystemConnectionRequest(target), uri);
    // ...
```
<span data-ttu-id="46125-134">起動試行の結果を処理するには、返された **AsyncOperation** を使用します。</span><span class="sxs-lookup"><span data-stu-id="46125-134">Use the returned **AsyncOperation** to handle the result of the launch attempt.</span></span>

```Java
    // ...
    resultOperation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<RemoteLaunchUriStatus, Throwable>() {
        @Override
        public void accept(RemoteLaunchUriStatus status, Throwable throwable) throws Throwable {
            if (throwable != null) {
                // handle the exception, referencing "throwable"
            } else {
                if (status == RemoteLaunchUriStatus.SUCCESS) {
                    // report the success case
                } else {
                    // report the non-success case, referencing "status"
                }
            }
        }
    });
}
```
<span data-ttu-id="46125-135">送信する URI に応じて、特定の状態または構成でリモート デバイス上でアプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="46125-135">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="46125-136">これにより、映画を観るなどのユーザー タスクを、中断することなく別のデバイス上で継続することができます。</span><span class="sxs-lookup"><span data-stu-id="46125-136">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span> 

<span data-ttu-id="46125-137">ユース ケースによっては、ターゲット システム上のどのアプリも URI を処理できない、または複数のアプリがそれを処理できる状況への対応が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="46125-137">Depending on your use case, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="46125-138">**[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** クラスと **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** クラスは、これを行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="46125-138">The **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** class and **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="46125-139">B) リモート アプリ サービス</span><span class="sxs-lookup"><span data-stu-id="46125-139">B) Remote app services</span></span>

<span data-ttu-id="46125-140">Android アプリは Connected Devices ポータルを使用して、他のデバイス上のアプリ サービスと対話できます。</span><span class="sxs-lookup"><span data-stu-id="46125-140">Your Android app can use the Connected Devices Portal interact with app services on other devices.</span></span> <span data-ttu-id="46125-141">これにより、他のデバイスと通信するための多くの方法が提供されます&mdash;アプリをホスト デバイスの前面に出す必要はまったくありません。</span><span class="sxs-lookup"><span data-stu-id="46125-141">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span> 

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="46125-142">ターゲット デバイスでアプリ サービスを設定する</span><span class="sxs-lookup"><span data-stu-id="46125-142">Set up the app service on the target device</span></span>
<span data-ttu-id="46125-143">このガイドでは、[Windows 用の Roman テスト アプリ](https://aka.ms/romeapp)をターゲット アプリ サービスとして使用します。</span><span class="sxs-lookup"><span data-stu-id="46125-143">This guide will use the [Roman Test App for Windows](https://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="46125-144">したがって、次のコードにより、Android アプリは特定のリモート システム上でその特定のアプリ サービスを探します。</span><span class="sxs-lookup"><span data-stu-id="46125-144">Therefore, the code below will cause an Android app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="46125-145">このシナリオをテストする場合は、Windows デバイス上で Roman テスト アプリをダウンロードし、先の準備手順で使用したのと同じ MSA でサインインしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="46125-145">If you wish to test this scenario,download the Roman Test App on a Windows device and make sure you are signed in with the same MSA that you used in the preliminary steps above.</span></span> 

<span data-ttu-id="46125-146">独自の UWP アプリ サービスを記述する方法については、[アプリ サービスの作成と利用 (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="46125-146">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="46125-147">サービスに Connected Devices との互換性を持たせるために、いくつかの変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="46125-147">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="46125-148">これを行う方法については、[リモート アプリ サービスに関する UWP ガイド](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46125-148">See the [UWP guide for remote app services](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="46125-149">クライアント デバイス上でアプリ サービス接続を開く</span><span class="sxs-lookup"><span data-stu-id="46125-149">Open an app service connection on the client device</span></span>
<span data-ttu-id="46125-150">Android アプリは、リモートのデバイスまたはアプリケーションへの参照を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46125-150">Your Android app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="46125-151">起動のセクションと同様、このシナリオでは **RemoteSystemConnectionRequest** を使用する必要があります。これは **RemoteSystem** から、またはシステム上の利用可能なアプリを表す **RemoteSystemApp** から作成できます。</span><span class="sxs-lookup"><span data-stu-id="46125-151">Like the launch section, this scenario requires the use of a **RemoteSystemConnectionRequest**, which can be constructed from either a **RemoteSystem** or a **RemoteSystemApp** representing an available app on the system.</span></span>


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
<span data-ttu-id="46125-152">さらにアプリは、*アプリ サービス名*と*パッケージ識別子*の 2 つの文字列を使用して、そのターゲットであるアプリ サービスを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46125-152">Additionally, your app will need to identify its targeted app service using two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="46125-153">これらはアプリ サービス プロバイダーのソース コードに含まれています。この文字列を Windows アプリ サービス用に取得する方法については、[アプリ サービスの作成と利用 (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="46125-153">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details on how to get this strings for Windows app services).</span></span> <span data-ttu-id="46125-154">これらの文字列が合わさって **AppServiceDescription** になり、これが **AppServiceConnection** インスタンスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="46125-154">Together these strings construct the **AppServiceDescription**, which is fed into an **AppServiceConnection** instance.</span></span>

```Java
// this is defined below
private AppServiceConnection connection = null; 


/**
* Creates an AppService connection with the current identifier and service name and opens the
* app service connection.
*/
private void onNewConnectionButtonClicked()
{
    connection = new AppServiceConnection();

    // these hard-coded strings must be defined elsewhere in the app
    connection.setAppServiceDescription(new AppServiceDescription(mAppServiceName, mPackageIdentifier));

    // this method is defined below
    openAppServiceConnection();
}
```
```Java
/**
* Establish an app service connection.
* Opens the given AppService connection using the connection request. Once the connection is
* opened, it adds the listeners for request-received and close. Catches all exceptions
* to show behavior of API surface exceptions.
*/
private void openAppServiceConnection()
{
    // optionally report outbound request
    // ...

    RemoteSystemConnectionRequest connectionRequest = new RemoteSystemConnectionRequest(target));

    /* Will asynchronously open the app service connection using the given connection request
    * When this is done, we log the traffic in the UI for visibility to the user (for sample purposes)
    * We can check the status of the connection to determine whether or not it was successful, and show 
    * some UI if it wasn't (in this case it is part of the list item).
    */
    connection.openRemoteAsync(connectionRequest)
        .thenAcceptAsync(new AsyncOperation.ResultConsumer<AppServiceConnectionStatus>() {
            @Override
            public void accept(AppServiceConnectionStatus appServiceConnectionStatus) throws Throwable {
                // optionally report inbound response
                // ...

                if (appServiceConnectionStatus != AppServiceConnectionStatus.SUCCESS) {
                    // report the error, referencing "appServiceConnectionStatus"
                    return;
                }
            }
        })
        .exceptionally(new AsyncOperation.ResultFunction<Throwable, Void>() {
            @Override
            public Void apply(Throwable throwable) throws Throwable {
                // report the exception
                return null;
            }
        });
}
```

#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="46125-155">アプリ サービスに送信するメッセージの作成</span><span class="sxs-lookup"><span data-stu-id="46125-155">Create a message to send to the app service</span></span>

<span data-ttu-id="46125-156">送信するメッセージを格納する変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="46125-156">Declare a variable to store the message to send.</span></span> <span data-ttu-id="46125-157">Android では、リモート アプリ サービスに送信するメッセージは **Map** 型になります。</span><span class="sxs-lookup"><span data-stu-id="46125-157">On Android, the messages that you send to remote app services will be of the **Map** type.</span></span>

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> <span data-ttu-id="46125-158">アプリが他のプラットフォーム上のアプリ サービスと通信するとき、Connected Devices Platform はこの **Map** を受信側プラットフォームでそれに対応するコンストラクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="46125-158">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **Map** into the matching construct on the receiving platform.</span></span> <span data-ttu-id="46125-159">たとえば、このアプリから Windows アプリ サービスに送信される **[Map](https://developer.android.com/reference/java/util/Map)** は、アプリ サービスが解釈できる (.NET Framework の) [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) オブジェクトに変換されます。</span><span class="sxs-lookup"><span data-stu-id="46125-159">For example, a **[Map](https://developer.android.com/reference/java/util/Map)** sent from this app to a Windows app service gets translated into a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="46125-160">反対方向に渡される情報には、逆の変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="46125-160">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="46125-161">次のメソッドは、Windows 用の Roman テスト アプリのアプリ サービスによって解釈できるメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="46125-161">The following method composes a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

```Java
/**
* Send the current message payload through all selected AppService connections on a non-UI
* thread as to not block user interaction, a result of the delay between API calls.
*/
private void onMessageButtonClicked()
{
    mMessagePayload = new HashMap<>();
    // Add the required fields of RomanApp on Windows
    DateFormat df = new SimpleDateFormat(DATE_FORMAT);
    mMessagePayload.put("Type", "ping");
    mMessagePayload.put("CreationDate", df.format(new Date()));
    mMessagePayload.put("TargetId", "check if this field needs to be included");

    // this method is defined below.
    sendMessage(connection, mMessagePayload);
}
```

> [!IMPORTANT]
> <span data-ttu-id="46125-162">リモート アプリ サービスのシナリオでアプリとサービスの間で受け渡しされる **Map** は、次の形式に従う必要があります。キーは文字列である必要があり、次の値を入れることができます: 文字列、ボックス数値型 (整数または浮動小数点数)、ボックス ブール値、android.graphics.Point、android.graphics.Rect、java.util.Date、java.util.UUID、上記いずれかの型と同種の配列、またはこの仕様を満たすその他の **Map** オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="46125-162">The **Map**s that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be Strings, and the values may be: Strings, boxed numeric types (integers or floating points), boxed booleans, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, homogeneous arrays of any of these types, or other **Map** objects that meet this specification.</span></span>

#### <a name="send-message-to-the-app-service"></a><span data-ttu-id="46125-163">アプリ サービスにメッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="46125-163">Send message to the app service</span></span>

<span data-ttu-id="46125-164">アプリ サービス接続が確立されてメッセージが作成されたら、それをアプリ サービスに送信するのは簡単であり、そのアプリ サービス接続インスタンスとメッセージへの参照があるアプリ内のどこからでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="46125-164">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the app service connection instance and the message.</span></span>


```java

// When assigning message IDs, use an incremental counter
private AtomicInteger mMessageIdAppServices = new AtomicInteger(0);

// ...

/**
* Send a message using the app service connection
* Send the given Map object through the given AppServiceConnection. Uses an internal messageId
* for logging purposes.
* @param connection AppServiceConnection to send the Map payload
* @param message Payload to be translated to a ValueSet
*/
private void sendMessage(final AppServiceConnection connection, Map<String, Object> message)
{
    final long messageId = mMessageIdAppServices.incrementAndGet();

    connection.sendMessageAsync(message)
        .thenAcceptAsync(new AsyncOperation.ResultConsumer<AppServiceResponse>() {
            @Override
            public void accept(AppServiceResponse appServiceResponse) throws Throwable {
                // optionally report an inbound response

                // this method is defined below
                handleAppServiceResponse(appServiceResponse, messageId);
            }
        })
        .exceptionally(new AsyncOperation.ResultFunction<Throwable, Void>() {
            @Override
            public Void apply(Throwable throwable) throws Throwable {
                // report the exception, referencing "throwable"

                return null;
            }
        });

    // optionally log the outbound message request here, referencing 
    // connection.getAppServiceDescription().getName() as the recipient.
}
```

<span data-ttu-id="46125-165">アプリ サービスの応答は、次のメソッドによって受信および解釈されます。</span><span class="sxs-lookup"><span data-stu-id="46125-165">The app service's response will be received and interpreted by the following method.</span></span>

```Java
private void handleAppServiceResponse(AppServiceResponse appServiceResponse, long messageId)
{
    AppServiceResponseStatus status = appServiceResponse.getStatus();
    if (status == AppServiceResponseStatus.SUCCESS)
    {
        // the message was delivered successfully; interpret the response.
        Map<String, Object> response;
        response = appServiceResponse.getMessage();

        // in the Roman App case, the response contains the date it was created.
        String dateStr = (String)response.get("CreationDate");
        DateFormat df = new SimpleDateFormat(DATE_FORMAT, Locale.getDefault());

        // in this very simple use case, we compare the dates to get the total
        // transit time of the message response.
        try {
            Date startDate = df.parse(dateStr);
            Date nowDate = new Date();
            long diff = nowDate.getTime() - startDate.getTime();
            // do something with "diff"
        } catch (ParseException e) { e.printStackTrace(); }
    }
}
```
<span data-ttu-id="46125-166">Roman アプリの場合、応答にはそれが作成された日付が含まれているため、この非常に単純なユース ケースでは、日付を比較してメッセージ応答の合計転送時間を取得できます。</span><span class="sxs-lookup"><span data-stu-id="46125-166">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="46125-167">これで、リモート アプリ サービスとの 1 回のメッセージ交換が終了します。</span><span class="sxs-lookup"><span data-stu-id="46125-167">This concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="46125-168">アプリ サービス通信の終了</span><span class="sxs-lookup"><span data-stu-id="46125-168">Finish app service communication</span></span>

<span data-ttu-id="46125-169">アプリがターゲット デバイスのアプリ サービスとの対話を終了したら、2 つのデバイス間の接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="46125-169">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a><span data-ttu-id="46125-170">関連トピック</span><span class="sxs-lookup"><span data-stu-id="46125-170">Related topics</span></span>
* [<span data-ttu-id="46125-171">API リファレンス ページ</span><span class="sxs-lookup"><span data-stu-id="46125-171">API reference page</span></span>](api-reference-for-android.md) 
* [<span data-ttu-id="46125-172">Android サンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="46125-172">Android sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [<span data-ttu-id="46125-173">リモート アプリ サービスとの通信 (UWP)</span><span class="sxs-lookup"><span data-stu-id="46125-173">Communicate with a remote app service (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="46125-174">[アプリ サービスの作成と利用 (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)</span><span class="sxs-lookup"><span data-stu-id="46125-174">[Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>
