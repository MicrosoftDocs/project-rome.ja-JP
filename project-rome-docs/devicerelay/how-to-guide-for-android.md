---
title: コマンドのリモート デバイスとアプリ (Android)
description: このガイドでは、リモート デバイスとアプリを検出してアプリを起動し、またはアプリ サービスと対話する方法を説明します。
ms.topic: article
keywords: microsoft、windows、プロジェクト、ローマをコマンド、android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: 78cb712d3b1cbbd3d613a45cd42af491eaa33afc
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907764"
---
# <a name="implementing-device-relay-for-android"></a><span data-ttu-id="6caa1-104">Android 用のデバイスのリレーの実装</span><span class="sxs-lookup"><span data-stu-id="6caa1-104">Implementing device relay for Android</span></span>

<span data-ttu-id="6caa1-105">プロジェクト ローマのデバイスのリレー機能は、2 つの主な機能をサポートする Api のセットで構成されています。 リモートの起動 (コマンドの実行とも呼ばれます) と app services。</span><span class="sxs-lookup"><span data-stu-id="6caa1-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="6caa1-106">リモート起動の Api は、ローカル デバイスからリモート デバイス上のプロセスが開始されるシナリオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="6caa1-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="6caa1-107">たとえば、ユーザーは、携帯電話、車のラジオをリッスンする可能性がありますが自宅のステレオにフックされているが、Xbox に再生を転送する電話を使用するホーム取得すると。</span><span class="sxs-lookup"><span data-stu-id="6caa1-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="6caa1-108">App Services Api により、任意のコンテンツを含むメッセージを送信できる 2 つのデバイス間で永続的なパイプラインを確立するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="6caa1-109">などの写真をモバイル デバイスで実行されているアプリを共有では、写真を取得するために、ユーザーの PC に接続を確立する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6caa1-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="6caa1-110">プロジェクトのローマの機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="6caa1-111">このガイドは、接続されているデバイス プラットフォームの使用を開始するために必要な手順について説明し、プラットフォームを使用して、デバイスのリレーを実装する方法を説明します機能に関連します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement Device Relay related features.</span></span>

<span data-ttu-id="6caa1-112">この手順はからコードを参照、[プロジェクト ローマ Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-112">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="6caa1-113">プラットフォームを使用します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-113">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="6caa1-114">リモート デバイスとアプリを検出します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-114">Discover remote devices and apps</span></span>

<span data-ttu-id="6caa1-115">A **RemoteSystemWatcher**インスタンスは、このセクションのコア機能を処理します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-115">A **RemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="6caa1-116">リモート システムを検出するには、クラスで宣言します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-116">Declare it in the class which is to discover remote systems.</span></span>

```Java
private RemoteSystemWatcher mWatcher = null;
```

<span data-ttu-id="6caa1-117">ウォッチャーを作成して、デバイスの検出を開始する前にどのような種類のデバイスのアプリの対象を決定する検索フィルターを追加したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="6caa1-117">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="6caa1-118">これらは、ユーザーの入力またはユース ケースに応じて、アプリにハードコーディングで決定できます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-118">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

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

<span data-ttu-id="6caa1-119">この時点では、アプリは、アプリが解析し、検出されたデバイスと対話する方法を決定する監視オブジェクトを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-119">At this point, the app can initialize the watcher object which determine how your app will parse and interact with devices that are discovered.</span></span>

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

<span data-ttu-id="6caa1-120">アプリが検出されたデバイスのセットを保持することをお勧め (によって表される**RemoteSystem**インスタンス) と、UI で使用可能なデバイスと (表示名とデバイスの種類) などのアプリに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-120">It is recommended that your app maintain a set of discovered devices (represented by **RemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="6caa1-121">次のクラスのスタブは、watcher のインスタンスのイベント リスナーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-121">The following class stubs can be used as event listeners for the watcher instance.</span></span>

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

<span data-ttu-id="6caa1-122">1 回`mWatcher.start`が呼び出されると、リモート システムの使用状況の監視を開始してデバイスの検出、更新、または検出されたデバイスのセットから削除されるときにイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-122">Once `mWatcher.start` is called, it will begin watching for remote system activity and will raise events when devices are discovered, updated, or removed from the set of discovered devices.</span></span> <span data-ttu-id="6caa1-123">これはスキャン継続的に、バック グラウンドでため不要なネットワーク通信とバッテリの消耗を回避するためにこれが不要になったときに、監視を停止することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6caa1-123">It will scan continuously in the background, so it is recommended that you stop the watcher when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

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
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="6caa1-124">ユース ケースの例: リモート起動して、リモート アプリ サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-124">Example use case: implementing remote launching and remote app services</span></span>

<span data-ttu-id="6caa1-125">この時点で、コードにしておくの作業一覧**RemoteSystem**使用可能なデバイスを参照するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6caa1-125">At this point in your code, you should have a working list of **RemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="6caa1-126">これらのデバイスで何は、アプリの機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="6caa1-126">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="6caa1-127">相互作用の主な型では、リモート起動してリモート アプリのサービスが。</span><span class="sxs-lookup"><span data-stu-id="6caa1-127">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="6caa1-128">これらは、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-128">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="6caa1-129">A) リモート起動</span><span class="sxs-lookup"><span data-stu-id="6caa1-129">A) Remote launching</span></span>

<span data-ttu-id="6caa1-130">次のコードは、これらのデバイス (理想的にはこれは、UI コントロールを介して) のいずれかを選択し、使用する方法を示しています。 **RemoteLauncher**を、アプリと互換性のある URI を渡すことによって、上のアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-130">The following code shows how to select one of these devices (ideally this is done through a UI control) and then use **RemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span> 

<span data-ttu-id="6caa1-131">リモートからの起動 (である場合、ホスト デバイスが起動する URI スキーム用の既定のアプリで指定された URI) リモート デバイスを対象にできることを確認することが重要_または_にそのデバイスにリモート アプリケーションを特定します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-131">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span> 

<span data-ttu-id="6caa1-132">検出をデバイス レベルで最初に実行前のセクションで示したように、(、 **RemoteSystem**デバイスを表します)、呼び出すことができますが、`getApplications`メソッドを**RemoteSystem**インスタンスを取得する、配列**RemoteSystemApp** (上記の準備手順では、独自のアプリを登録) と同様に、接続されているデバイス プラットフォームを使用する登録されているリモート デバイスでアプリを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6caa1-132">As the previous section demonstrated, discovery happens at the device level first (a **RemoteSystem** represents a device), but you can call the `getApplications` method on a **RemoteSystem** instance to get an array of **RemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="6caa1-133">両方**RemoteSystem**と**RemoteSystemApp**作成に使用できます、 **RemoteSystemConnectionRequest**URI の起動に必要なものであります。</span><span class="sxs-lookup"><span data-stu-id="6caa1-133">Both **RemoteSystem** and **RemoteSystemApp** can be used to construct a **RemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

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
<span data-ttu-id="6caa1-134">使用して、返された**AsyncOperation**起動試行の結果を処理します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-134">Use the returned **AsyncOperation** to handle the result of the launch attempt.</span></span>

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
<span data-ttu-id="6caa1-135">によって送信される URI は、特定の状態またはリモート デバイス上の構成でのアプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-135">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="6caa1-136">これにより、中断することがなく別のデバイスで映画を見てなど、ユーザーのタスクを継続する能力。</span><span class="sxs-lookup"><span data-stu-id="6caa1-136">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span> 

<span data-ttu-id="6caa1-137">ユース ケースに応じてを対象となるシステム上のアプリを取り扱うことが、URI の場合を対象にする必要があります。 または複数のアプリで処理できます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-137">Depending on your use case, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="6caa1-138">**[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** クラスと **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** クラスは、これを行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-138">The **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** class and **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="6caa1-139">B) リモート アプリ サービス</span><span class="sxs-lookup"><span data-stu-id="6caa1-139">B) Remote app services</span></span>

<span data-ttu-id="6caa1-140">Android アプリで接続されているデバイス ポータルを使用できるその他のデバイス上の app services と対話します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-140">Your Android app can use the Connected Devices Portal interact with app services on other devices.</span></span> <span data-ttu-id="6caa1-141">これにより、他のデバイスと通信する方法は多数&mdash;ホスト デバイスの前面にアプリを表示する必要はありませんすべて。</span><span class="sxs-lookup"><span data-stu-id="6caa1-141">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span> 

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="6caa1-142">ターゲット デバイスでアプリ サービスをセットアップする</span><span class="sxs-lookup"><span data-stu-id="6caa1-142">Set up the app service on the target device</span></span>
<span data-ttu-id="6caa1-143">このガイドを使用して、 [Roman テスト アプリの Windows](http://aka.ms/romeapp)そのターゲット アプリケーションのサービスとして。</span><span class="sxs-lookup"><span data-stu-id="6caa1-143">This guide will use the [Roman Test App for Windows](http://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="6caa1-144">そのため、次のコードは、特定のリモート システムでは、その特定のアプリ サービスを検索する Android アプリになります。</span><span class="sxs-lookup"><span data-stu-id="6caa1-144">Therefore, the code below will cause an Android app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="6caa1-145">このシナリオをテストする場合は、Windows デバイスで Roman テスト アプリをダウンロードし、同じ MSA または前の準備手順で使用する AAD でサインインしているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-145">If you wish to test this scenario, download the Roman Test App on a Windows device and make sure you are signed in with the same MSA or AAD that you used in the preliminary steps above.</span></span> 

<span data-ttu-id="6caa1-146">UWP アプリ サービスを作成する方法に関する手順については、次を参照してください。[を作成する (UWP) アプリ サービスの使用と](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-146">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="6caa1-147">接続されたデバイスと互換性のあるサービスを作成するには、いくつか変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6caa1-147">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="6caa1-148">参照してください、[リモート アプリ サービスの UWP ガイド](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)これを行う方法の詳細について。</span><span class="sxs-lookup"><span data-stu-id="6caa1-148">See the [UWP guide for remote app services](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="6caa1-149">クライアント デバイスにアプリ サービスの接続を開く</span><span class="sxs-lookup"><span data-stu-id="6caa1-149">Open an app service connection on the client device</span></span>
<span data-ttu-id="6caa1-150">Android アプリでは、リモート デバイスまたはアプリケーションへの参照を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6caa1-150">Your Android app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="6caa1-151">このシナリオの起動セクションなどを使用する必要を**RemoteSystemConnectionRequest**、いずれかから構築できますが、 **RemoteSystem**または**RemoteSystemApp**システムで利用可能なアプリを表します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-151">Like the launch section, this scenario requires the use of a **RemoteSystemConnectionRequest**, which can be constructed from either a **RemoteSystem** or a **RemoteSystemApp** representing an available app on the system.</span></span>


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
<span data-ttu-id="6caa1-152">アプリは 2 つの文字列を使用して、対象となるアプリ サービスを特定する必要がありますさらに、: *app service の名前*と*パッケージ識別子*します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-152">Additionally, your app will need to identify its targeted app service using two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="6caa1-153">アプリのサービス プロバイダーのソース コードにあるこれらは (を参照してください[を作成する (UWP) アプリ サービスの使用と](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)Windows app services についてこの文字列を取得する方法の詳細について)。</span><span class="sxs-lookup"><span data-stu-id="6caa1-153">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details on how to get this strings for Windows app services).</span></span> <span data-ttu-id="6caa1-154">これらの文字列を構築して、 **AppServiceDescription**にフィードするが、 **AppServiceConnection**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="6caa1-154">Together these strings construct the **AppServiceDescription**, which is fed into an **AppServiceConnection** instance.</span></span>

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

#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="6caa1-155">App service に送信するメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-155">Create a message to send to the app service</span></span>

<span data-ttu-id="6caa1-156">送信するメッセージを格納する変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-156">Declare a variable to store the message to send.</span></span> <span data-ttu-id="6caa1-157">Android では、リモート アプリ サービスに送信するメッセージはで、**マップ**型。</span><span class="sxs-lookup"><span data-stu-id="6caa1-157">On Android, the messages that you send to remote app services will be of the **Map** type.</span></span>

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> <span data-ttu-id="6caa1-158">接続されているデバイス プラットフォームを変換、アプリが他のプラットフォーム上の app services を通信する場合、**マップ**受信側のプラットフォームに一致するコンス トラクターにします。</span><span class="sxs-lookup"><span data-stu-id="6caa1-158">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **Map** into the matching construct on the receiving platform.</span></span> <span data-ttu-id="6caa1-159">たとえば、 **[マップ](https://developer.android.com/reference/java/util/Map)** アプリ サービスに変換します Windows にこのアプリから送信される、 [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) (.NET Framework にある) のオブジェクト。これは、app service でし解釈できます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-159">For example, a **[Map](https://developer.android.com/reference/java/util/Map)** sent from this app to a Windows app service gets translated into a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="6caa1-160">その他の方向に渡された情報には、逆の変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-160">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="6caa1-161">次のメソッドは、Windows 用の欧文テスト アプリの app service で解釈できるメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-161">The following method composes a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

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
> <span data-ttu-id="6caa1-162">**マップ**アプリとアプリのリモート サービスのシナリオでのサービス間で渡されることは、次の形式に従う必要があります。キーは、文字列である必要があり、値があります。文字列、ブール値、android.graphics.Point、android.graphics.Rect、java.util.Date、java.util.UUID、これらの型、またはその他のいずれかの同種の配列 (整数または浮動小数点)、ボックス化された数値の型がボックス化**マップ**オブジェクトこの仕様を満たしています。</span><span class="sxs-lookup"><span data-stu-id="6caa1-162">The **Map**s that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be Strings, and the values may be: Strings, boxed numeric types (integers or floating points), boxed booleans, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, homogeneous arrays of any of these types, or other **Map** objects that meet this specification.</span></span>

#### <a name="send-message-to-the-app-service"></a><span data-ttu-id="6caa1-163">App service へのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-163">Send message to the app service</span></span>

<span data-ttu-id="6caa1-164">アプリ サービスの接続が確立され、メッセージが作成された、app service に送信は単純なとでアプリを app service の接続インスタンスおよびメッセージへの参照を持つ任意の場所から実行できます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-164">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the app service connection instance and the message.</span></span>


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

<span data-ttu-id="6caa1-165">アプリ サービスの応答を受信して、次の方法で解釈されます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-165">The app service's response will be received and interpreted by the following method.</span></span>

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
<span data-ttu-id="6caa1-166">ローマ アプリの場合、応答には、この非常に単純なユース ケースでは、メッセージの応答の転送中の合計時間を取得する日付を比較できるように、作成された日付が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-166">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="6caa1-167">これは、リモート アプリ サービスで、1 つのメッセージ交換を終了します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-167">This concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="6caa1-168">アプリ サービスの通信を完了します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-168">Finish app service communication</span></span>

<span data-ttu-id="6caa1-169">アプリが終了すると、ターゲット デバイスのアプリのサービスと対話する 2 つのデバイス間の接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="6caa1-169">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a><span data-ttu-id="6caa1-170">関連トピック</span><span class="sxs-lookup"><span data-stu-id="6caa1-170">Related topics</span></span>
* [<span data-ttu-id="6caa1-171">API リファレンスのページ</span><span class="sxs-lookup"><span data-stu-id="6caa1-171">API reference page</span></span>](api-reference-for-android.md) 
* [<span data-ttu-id="6caa1-172">Android のサンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="6caa1-172">Android sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [<span data-ttu-id="6caa1-173">(UWP) アプリのリモート サービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-173">Communicate with a remote app service (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="6caa1-174">[作成し、app service (UWP) を使用する](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)します。</span><span class="sxs-lookup"><span data-stu-id="6caa1-174">[Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>
