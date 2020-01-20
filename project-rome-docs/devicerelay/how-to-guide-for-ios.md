---
title: iOS のデバイス リレー機能の実装
description: このガイドでは、リモートのデバイスやアプリを検出してから、アプリを起動したり、アプリ サービスと対話したりする方法について説明します。
ms.topic: article
keywords: microsoft, windows, project rome, コマンド実行, ios
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: 09479f0caa232215dfce51628432529d0e322536
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115556"
---
# <a name="implementing-device-relay-for-ios"></a><span data-ttu-id="1424c-104">iOS のデバイス リレーの実装</span><span class="sxs-lookup"><span data-stu-id="1424c-104">Implementing device relay for iOS</span></span>

<span data-ttu-id="1424c-105">Project Rome のデバイス リレー機能は、2 つの主な機能であるリモート起動 (コマンド実行とも呼びます) とアプリ サービスをサポートする一連の API で構成されています。</span><span class="sxs-lookup"><span data-stu-id="1424c-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="1424c-106">リモート起動 API は、リモート デバイス上のプロセスがローカル デバイスから開始されるシナリオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1424c-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="1424c-107">たとえば、ユーザーが車に乗りながら電話でラジオを聴きますが、帰宅したらホーム ステレオに接続した Xbox に電話を使用して再生を転送することがあります。</span><span class="sxs-lookup"><span data-stu-id="1424c-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="1424c-108">アプリケーションは App Services API を使用して 2 つのデバイス間に永続的なパイプラインを確立し、任意の内容を含むメッセージをこのパイプライン経由で送信することができます。</span><span class="sxs-lookup"><span data-stu-id="1424c-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="1424c-109">たとえば、モバイル デバイス上で実行されている写真共有アプリが、写真を取得するためにユーザーの PC との接続を確立することができます。</span><span class="sxs-lookup"><span data-stu-id="1424c-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="1424c-110">Project Rome の機能は、Connected Devices Platform と呼ばれる基盤プラットフォームによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1424c-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="1424c-111">このガイドでは、Connected Devices Platform を初めて使用するために必要な手順と、このプラットフォームを使用してデバイス リレー関連機能を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1424c-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement device relay related features.</span></span>

<span data-ttu-id="1424c-112">この手順では、GitHub から入手できる [Project Rome iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)のコードを参照します。</span><span class="sxs-lookup"><span data-stu-id="1424c-112">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="1424c-113">Connected Devices Platform と通知の設定</span><span class="sxs-lookup"><span data-stu-id="1424c-113">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="1424c-114">プラットフォームの使用</span><span class="sxs-lookup"><span data-stu-id="1424c-114">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="1424c-115">リモートのデバイスとアプリの検出</span><span class="sxs-lookup"><span data-stu-id="1424c-115">Discover remote devices and apps</span></span>

<span data-ttu-id="1424c-116">**MCDRemoteSystemWatcher** インスタンスは、このセクションのコア機能を処理します。</span><span class="sxs-lookup"><span data-stu-id="1424c-116">An **MCDRemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="1424c-117">これは、リモート システムを検出するクラスの中で宣言します。</span><span class="sxs-lookup"><span data-stu-id="1424c-117">Declare it in the class which is to discover remote systems.</span></span>

`MCDRemoteSystemWatcher* _watcher;`

<span data-ttu-id="1424c-118">ウォッチャーを作成してデバイスの検出を開始する前に、検出フィルターを追加して、どのような種類のデバイスをアプリでターゲットにするかを決定することができます。</span><span class="sxs-lookup"><span data-stu-id="1424c-118">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="1424c-119">ユース ケースに応じて、これらはユーザーの入力によって決定、またはアプリにハードコードすることができます。</span><span class="sxs-lookup"><span data-stu-id="1424c-119">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

<span data-ttu-id="1424c-120">サンプル アプリの次のコードは、検出されたデバイスをアプリで解析し、それらと対話するためのウォッチャー インスタンスを作成して起動する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1424c-120">The following code from the sample app demonstrates how to create and start a watcher instance allowing your app to parse and interact with the devices that are discovered.</span></span>

```ObjectiveC
// Start watcher with filter for transport types, form factors
- (void)startWatcherWithFilter:(NSMutableArray<NSObject<MCDRemoteSystemFilter>*>*)remoteSystemFilter
{
    _discoveredSystems = [[NSMutableArray alloc] init];
    _devicesAdded = 0;
    _devicesUpdated = 0;
    _devicesRemoved = 0;

    // add filters (not defined here)
    _watcher = (remoteSystemFilter.count > 0) ? [[MCDRemoteSystemWatcher alloc] initWithFilters:remoteSystemFilter] :
        [[MCDRemoteSystemWatcher alloc] init];

    // add event handlers
    RemoteSystemViewController* __weak weakSelf = self;
    [_watcher addRemoteSystemAddedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemAdded:system]; }];

    [_watcher addRemoteSystemUpdatedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemUpdated:system]; }];

    [_watcher addRemoteSystemRemovedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemRemoved:system]; }];

    // start watcher
    [_watcher start];
}
```

<span data-ttu-id="1424c-121">ここでは、イベント ハンドラー メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="1424c-121">The event handler methods are defined here.</span></span>

```ObjectiveC
// Handle when RemoteSystems are added
- (void)_onRemoteSystemAdded:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesAdded++;
        [_discoveredSystems addObject:system];
        [_delegate remoteSystemsDidUpdate];
    }
}

// Handle when RemoteSystems are updated
- (void)_onRemoteSystemUpdated:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesUpdated++;

        for (unsigned i = 0; i < _discoveredSystems.count; i++)
        {
            MCDRemoteSystem* cachedSystem = [_discoveredSystems objectAtIndex:i];
            if ([cachedSystem.displayName isEqualToString:system.displayName])
            {
                [_discoveredSystems replaceObjectAtIndex:i withObject:system];
                break;
            }
        }
    }
}

// Handle when RemoteSystems are removed
- (void)_onRemoteSystemRemoved:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesRemoved++;

        for (unsigned i = 0; i < _discoveredSystems.count; i++)
        {
            MCDRemoteSystem* cachedSystem = [_discoveredSystems objectAtIndex:i];
            if ([cachedSystem.displayName isEqualToString:system.displayName])
            {
                [_discoveredSystems removeObjectAtIndex:i];
                break;
            }
        }
    }
}
```

<span data-ttu-id="1424c-122">(**MCDRemoteSystem** インスタンスで表される) 検出されたデバイスのセットをアプリで管理し、利用可能なデバイスとそのアプリについての情報 (表示名やデバイスの種類など) を UI に表示することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1424c-122">We recommend that your app maintain a set of discovered devices (represented by **MCDRemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="1424c-123">`[_watcher start]` が呼び出されると、リモート システムのアクティビティの監視が始まります。接続デバイスが検出、更新、または検出済みデバイスのセットから削除されると、イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="1424c-123">Once `[_watcher start]` is called, it will begin watching for remote system activity and will raise events when connected devices are discovered, updated, or removed from the set of detected devices.</span></span> <span data-ttu-id="1424c-124">バックグラウンドで継続的にスキャンされるため、不必要なネットワーク通信やバッテリの消耗を避けるために、不要になったら (`[_watcher stop]` を使用して) ウォッチャーを停止することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1424c-124">It will scan continuously in the background, so it is recommended that you stop the watcher (with `[_watcher stop]`) when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="1424c-125">ユース ケースの例: リモート起動とリモート アプリ サービスの実装</span><span class="sxs-lookup"><span data-stu-id="1424c-125">Example use case: implementing remote launching and remote app services</span></span>
<span data-ttu-id="1424c-126">コードのこの時点で、利用可能なデバイスを参照する **MCDRemoteSystem** オブジェクトの有効な一覧があるはずです。</span><span class="sxs-lookup"><span data-stu-id="1424c-126">At this point in your code, you should have a working list of **MCDRemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="1424c-127">これらのデバイスに対して何をするかは、アプリの機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="1424c-127">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="1424c-128">主な種類の対話は、リモート起動とリモート アプリ サービスです。</span><span class="sxs-lookup"><span data-stu-id="1424c-128">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="1424c-129">これらについては、以降のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="1424c-129">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="1424c-130">A) リモート起動</span><span class="sxs-lookup"><span data-stu-id="1424c-130">A) Remote launching</span></span>

<span data-ttu-id="1424c-131">次のコードは、**MCDRemoteSystem** オブジェクトのいずれかを選択し (UI コントロールを使って行われるのが理想的です)、**MCDRemoteLauncher** を使用して、アプリと互換性のある URI を渡してそのデバイス上でアプリを起動する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1424c-131">The following code shows how to select one of the **MCDRemoteSystem** objects (ideally this is done through a UI control) and then use **MCDRemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span>

<span data-ttu-id="1424c-132">重要な注意点として、リモート起動でターゲットにできるのはリモート デバイス_または_そのデバイス上の特定のリモート アプリケーションであり、前者の場合、指定された URI を、ホスト デバイスがその URI スキーム用の既定のアプリで起動します。</span><span class="sxs-lookup"><span data-stu-id="1424c-132">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span>

<span data-ttu-id="1424c-133">前のセクションで説明したように、検出はまずデバイス レベルで行われます (**MCDRemoteSystem** はデバイスを表します) が、**MCDRemoteSystem** インスタンスの `getApplications` メソッドを呼び出して **MCDRemoteSystemApp** オブジェクトの配列を取得することができます。これらのオブジェクトが表すのは、(前述の準備手順で独自のアプリを登録したのと同様に) Connected Devices Platform を使用するように登録されている、リモート デバイス上のアプリです。</span><span class="sxs-lookup"><span data-stu-id="1424c-133">As the previous section demonstrated, discovery happens at the device level first (an **MCDRemoteSystem** represents a device), but you can call the `getApplications` method on an **MCDRemoteSystem** instance to get an array of **MCDRemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="1424c-134">**MCDRemoteSystem** と **MCDRemoteSystemApp** のどちらを使用しても、URI を起動するために必要な **MCDRemoteSystemConnectionRequest** を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1424c-134">Both **MCDRemoteSystem** and **MCDRemoteSystemApp** can be used to construct a **MCDRemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

<span data-ttu-id="1424c-135">サンプルの次のコードは、接続要求を経由した URI のリモート起動を示しています。</span><span class="sxs-lookup"><span data-stu-id="1424c-135">The following code from the sample shows the remote launching of a URI over a connection request.</span></span>

```ObjectiveC
// Send a remote launch of a uri to RemoteSystemApplication
- (IBAction)launchUriButton:(id)sender
{
    NSString* uri = self.uriField.text;
    MCDRemoteLauncher* remoteLauncher = [[MCDRemoteLauncher alloc] init];
    MCDRemoteSystemConnectionRequest* connectionRequest =
        [MCDRemoteSystemConnectionRequest requestWithRemoteSystemApplication:self.selectedApplication];
    [remoteLauncher launchUriAsync:uri
        withConnectionRequest:connectionRequest
            completion:^(MCDRemoteLaunchUriStatus result, NSError* _Nullable error) {
                if (error)
                {
                    NSLog(@"LaunchURI [%@]: ERROR: %@", uri, error);
                    return;
                }

                if (result == MCDRemoteLaunchUriStatusSuccess)
                {
                    NSLog(@"LaunchURI [%@]: Success!", uri);
                }
                else
                {
                    NSLog(@"LaunchURI [%@]: Failed with code %d", uri, (int)result);
                }
            }];
}
```

<span data-ttu-id="1424c-136">送信する URI に応じて、特定の状態または構成でリモート デバイス上でアプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="1424c-136">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="1424c-137">これにより、映画を観るなどのユーザー タスクを、中断することなく別のデバイス上で継続することができます。</span><span class="sxs-lookup"><span data-stu-id="1424c-137">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span>

<span data-ttu-id="1424c-138">用途によっては、ターゲット システム上のどのアプリも URI を処理できない、または複数のアプリがそれを処理できる状況への対応が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="1424c-138">Depending on your use, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="1424c-139">**[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** クラスと **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** クラスは、これを行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1424c-139">The **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** class and **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="1424c-140">B) リモート アプリ サービス</span><span class="sxs-lookup"><span data-stu-id="1424c-140">B) Remote app services</span></span>

<span data-ttu-id="1424c-141">iOS アプリは Connected Devices ポータルを使用して、他のデバイス上のアプリ サービスと対話できます。</span><span class="sxs-lookup"><span data-stu-id="1424c-141">Your iOS app can use the Connected Devices Portal to interact with app services on other devices.</span></span> <span data-ttu-id="1424c-142">これにより、他のデバイスと通信するための多くの方法が提供されます&mdash;アプリをホスト デバイスの前面に出す必要はまったくありません。</span><span class="sxs-lookup"><span data-stu-id="1424c-142">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span>

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="1424c-143">ターゲット デバイスでアプリ サービスを設定する</span><span class="sxs-lookup"><span data-stu-id="1424c-143">Set up the app service on the target device</span></span>
<span data-ttu-id="1424c-144">このガイドでは、[Windows 用の Roman テスト アプリ](https://aka.ms/romeapp)をターゲット アプリ サービスとして使用します。</span><span class="sxs-lookup"><span data-stu-id="1424c-144">This guide will use the [Roman Test App for Windows](https://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="1424c-145">したがって、次のコードにより、iOS アプリは特定のリモート システム上でその特定のアプリ サービスを探します。</span><span class="sxs-lookup"><span data-stu-id="1424c-145">Therefore, the code below will cause an iOS app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="1424c-146">このシナリオをテストする場合は、Windows デバイス上で Roman テスト アプリをダウンロードし、先の準備手順で使用したのと同じ MSA でサインインしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1424c-146">If you wish to test this scenario, download the Roman Test App on a Windows device and make sure you are signed in with the same MSA that you used in the preliminary steps above.</span></span>

<span data-ttu-id="1424c-147">独自の UWP アプリ サービスを記述する方法については、[アプリ サービスの作成と利用 (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1424c-147">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="1424c-148">サービスに Connected Devices との互換性を持たせるために、いくつかの変更を加える必要があります。</span><span class="sxs-lookup"><span data-stu-id="1424c-148">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="1424c-149">これを行う方法については、[リモート アプリ サービスに関する UWP ガイド](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1424c-149">See the [UWP guide for remote app services](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="1424c-150">クライアント デバイス上でアプリ サービス接続を開く</span><span class="sxs-lookup"><span data-stu-id="1424c-150">Open an app service connection on the client device</span></span>
<span data-ttu-id="1424c-151">iOS アプリは、リモートのデバイスまたはアプリケーションへの参照を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1424c-151">Your iOS app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="1424c-152">起動のセクションと同様、このシナリオでは **MCDRemoteSystemConnectionRequest** を使用する必要があります。これは **MCDRemoteSystem** から、またはシステム上の利用可能なアプリを表す **MCDRemoteSystemApp** から作成できます。</span><span class="sxs-lookup"><span data-stu-id="1424c-152">Like the launch section, this scenario requires the use of a **MCDRemoteSystemConnectionRequest**, which can be constructed from either a **MCDRemoteSystem** or a **MCDRemoteSystemApp** representing an available app on the system.</span></span>

<span data-ttu-id="1424c-153">さらにアプリは、*アプリ サービス名*と*パッケージ識別子*の 2 つの文字列によって、そのターゲットであるアプリ サービスを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1424c-153">Additionally, your app will need to identify its targeted app service by two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="1424c-154">これらはアプリ サービス プロバイダーのソース コードに含まれています。詳細については、[アプリ サービスの作成と利用 (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1424c-154">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details).</span></span> <span data-ttu-id="1424c-155">これらの文字列が合わさって **MCDAppServiceDescription** になり、これが **MCDAppServiceConnection** インスタンスに渡されます。</span><span class="sxs-lookup"><span data-stu-id="1424c-155">Together these strings construct the **MCDAppServiceDescription**, which is fed into an **MCDAppServiceConnection** instance.</span></span>

```ObjectiveC
// Step #1:  Establish an app service connection
- (IBAction)connectAppServiceButton:(id)sender
{
    MCDAppServiceConnection* connection = nil;
    @synchronized(self)
    {
        connection = _appServiceConnection;
        if (!connection)
        {
            connection = _appServiceConnection = [MCDAppServiceConnection new];
            connection.appServiceDescription =
                [MCDAppServiceDescription descriptionWithName:g_appServiceName packageId:g_packageIdentifier];
            _serviceClosedRegistration = [connection addServiceClosedListener:^(__unused MCDAppServiceConnection* connection,
                MCDAppServiceClosedStatus status) { [self appServiceConnection:connection closedWithStatus:status]; }];
        }
    }

    @try
    {
        MCDRemoteSystemConnectionRequest* connectionRequest =
            [MCDRemoteSystemConnectionRequest requestWithRemoteSystemApplication:self.selectedApplication];
        [connection openRemoteAsync:connectionRequest
            completion:^(MCDAppServiceConnectionStatus status, NSError* error) {
                if (error)
                {
                    NSLog(@"ConnectAppService: ERROR: %@", error);
                    return;
                }
                if (status != MCDAppServiceConnectionStatusSuccess)
                {
                    NSLog(@"ConnectAppService: Failed with code %d", (int)status);
                    return;
                }
                NSLog(@"Successfully connected!");
                dispatch_async(
                    dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = @"App service connected! no ping sent"; });
            }];
    }
    @catch (NSException* ex)
    {
        NSLog(@"ConnectAppService: EXCEPTION! %@", ex);
    }
}
```


#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="1424c-156">アプリ サービスに送信するメッセージの作成</span><span class="sxs-lookup"><span data-stu-id="1424c-156">Create a message to send to the app service</span></span>

<span data-ttu-id="1424c-157">送信するメッセージを格納する変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="1424c-157">Declare a variable to store the message to send.</span></span> <span data-ttu-id="1424c-158">iOS では、リモート アプリ サービスに送信するメッセージは **NSDictionary** 型になります。</span><span class="sxs-lookup"><span data-stu-id="1424c-158">On iOS, the messages that you send to remote app services will be of the **NSDictionary** type.</span></span>

> [!NOTE]
> <span data-ttu-id="1424c-159">アプリが他のプラットフォーム上のアプリ サービスと通信するとき、Connected Devices Platform はこの **NSDictionary** を、受信側プラットフォームでの同等のコンストラクトに変換します。</span><span class="sxs-lookup"><span data-stu-id="1424c-159">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **NSDictionary** into the equivalent construct on the receiving platform.</span></span> <span data-ttu-id="1424c-160">たとえば、このアプリから Windows アプリ サービスに送信される **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** は、アプリ サービスが解釈できる (.NET Framework の) [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) オブジェクトに変換されます。</span><span class="sxs-lookup"><span data-stu-id="1424c-160">For example, a **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** sent from this app to a Windows app service gets translated into a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="1424c-161">反対方向に渡される情報には、逆の変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="1424c-161">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="1424c-162">次のメソッドは、Windows 用の Roman テスト アプリのアプリ サービスによって解釈できるメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="1424c-162">The following method crafts a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

```ObjectiveC
// Create a message to send
- (NSDictionary*)_createPingMessage
{
    return @{
        @"Type" : @"ping",
        @"CreationDate" : [_dateFormatter stringFromDate:[NSDate date]],
        @"TargetId" : _selectedApplication.applicationId
    };
}
```

> [!IMPORTANT]
> <span data-ttu-id="1424c-163">リモート アプリ サービスのシナリオでアプリとサービスの間で受け渡しされる **NSDictionary** オブジェクトは、次の形式に従う必要があります。キーは **NSString** である必要があり、次の値を入れることができます: **NSString**、ボックス数値型 (整数または浮動小数点数)、ボックス ブール値、**NSDate**、**NSUUID**、上記いずれかの型と同種の配列、またはこの仕様を満たすその他の **NSDictionary** オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1424c-163">The **NSDictionary** objects that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be **NSString**s, and the values may be: **NSString**, boxed numeric types (integers or floating points), boxed booleans, **NSDate**, **NSUUID**, homogeneous arrays of any of these types, or other **NSDictionary** objects that meet this specification.</span></span> 

#### <a name="send-messages-to-the-app-service"></a><span data-ttu-id="1424c-164">アプリ サービスにメッセージを送信する</span><span class="sxs-lookup"><span data-stu-id="1424c-164">Send messages to the app service</span></span>

<span data-ttu-id="1424c-165">アプリ サービス接続が確立されてメッセージが作成されたら、それをアプリ サービスに送信するのは簡単であり、接続インスタンスとメッセージへの参照があるアプリ内のどこからでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="1424c-165">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the connection instance and the message.</span></span>

<span data-ttu-id="1424c-166">サンプルの次のコードは、アプリ サービスへのメッセージ送信と応答の処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="1424c-166">The following code from the sample shows the sending of a message to an app service and the handling of the response.</span></span>

```ObjectiveC
//  Send a message using the app service connection
- (IBAction)sendAppServiceButton:(id)sender
{
    if (!_appServiceConnection)
    {
        return;
    }

    // Send the message and get a response
    @try
    {
        [_appServiceConnection sendMessageAsync:[self _createPingMessage]
            completion:^(MCDAppServiceResponse* response, NSError* error) {
                if (error)
                {
                    NSLog(@"SendPing: ERROR: %@", error);
                    return;
                }

                if (response.status != MCDAppServiceResponseStatusSuccess)
                {
                    NSLog(@"SendPing: Response received with bad status code %d", (int)response.status);
                    return;
                }

                NSString* creationDateString = response.message[@"CreationDate"];
                if (creationDateString)
                {
                    NSDate* date = [_dateFormatter dateFromString:creationDateString];
                    if (date)
                    {
                        NSTimeInterval diff = [[NSDate date] timeIntervalSinceDate:date];
                        dispatch_async(dispatch_get_main_queue(),
                            ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"%g", diff]; });
                    }
                }
            }];
    }
    @catch (NSException* ex)
    {
        NSLog(@"SendPing: EXCEPTION! %@", ex);
    }
}
```

<span data-ttu-id="1424c-167">Roman アプリの場合、応答にはそれが作成された日付が含まれているため、この非常に単純なユース ケースでは、日付を比較してメッセージ応答の合計転送時間を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1424c-167">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="1424c-168">以上で、リモート アプリ サービスとの 1 回のメッセージ交換が終了します。</span><span class="sxs-lookup"><span data-stu-id="1424c-168">That concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="1424c-169">アプリ サービス通信の終了</span><span class="sxs-lookup"><span data-stu-id="1424c-169">Finish app service communication</span></span>

<span data-ttu-id="1424c-170">アプリがターゲット デバイスのアプリ サービスとの対話を終了したら、2 つのデバイス間の接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="1424c-170">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a><span data-ttu-id="1424c-171">関連トピック</span><span class="sxs-lookup"><span data-stu-id="1424c-171">Related topics</span></span>
* [<span data-ttu-id="1424c-172">API リファレンス ページ</span><span class="sxs-lookup"><span data-stu-id="1424c-172">API reference page</span></span>](api-reference-for-ios.md) 
* [<span data-ttu-id="1424c-173">iOS サンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="1424c-173">iOS sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [<span data-ttu-id="1424c-174">リモート アプリ サービスとの通信 (UWP)</span><span class="sxs-lookup"><span data-stu-id="1424c-174">Communicate with a remote app service (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="1424c-175">[アプリ サービスの作成と利用 (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)</span><span class="sxs-lookup"><span data-stu-id="1424c-175">[Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>
