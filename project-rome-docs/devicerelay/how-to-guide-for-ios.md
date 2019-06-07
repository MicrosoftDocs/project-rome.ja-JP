---
title: Ios デバイスのリレー機能を実装します。
description: このガイドでは、リモート デバイスとアプリを検出してアプリを起動し、またはアプリ サービスと対話する方法を説明します。
ms.topic: article
keywords: microsoft、windows、プロジェクト、ローマ、コマンド実行の ios
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: c9c3e8bf580884c6f0c3b6ccdf177f163f05c03a
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755810"
---
# <a name="implementing-device-relay-for-ios"></a><span data-ttu-id="8d6bd-104">Ios デバイスのリレーを実装します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-104">Implementing device relay for iOS</span></span>

<span data-ttu-id="8d6bd-105">プロジェクト ローマのデバイスのリレー機能は、2 つの主な機能をサポートする Api のセットで構成されています。 リモートの起動 (コマンドの実行とも呼ばれます) と app services。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="8d6bd-106">リモート起動の Api は、ローカル デバイスからリモート デバイス上のプロセスが開始されるシナリオをサポートします。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="8d6bd-107">たとえば、ユーザーは、携帯電話、車のラジオをリッスンする可能性がありますが自宅のステレオにフックされているが、Xbox に再生を転送する電話を使用するホーム取得すると。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="8d6bd-108">App Services Api により、任意のコンテンツを含むメッセージを送信できる 2 つのデバイス間で永続的なパイプラインを確立するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="8d6bd-109">などの写真をモバイル デバイスで実行されているアプリを共有では、写真を取得するために、ユーザーの PC に接続を確立する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="8d6bd-110">プロジェクトのローマの機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="8d6bd-111">このガイドは、接続されているデバイス プラットフォームの使用を開始するために必要な手順について説明し、プラットフォームを使用して実装する方法を説明しますデバイス リレー機能に関連します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement device relay related features.</span></span>

<span data-ttu-id="8d6bd-112">この手順はからコードを参照、[プロジェクト ローマ iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)GitHub に用意されています。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-112">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="8d6bd-113">接続されているデバイス プラットフォームと通知を設定します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-113">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="8d6bd-114">プラットフォームを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-114">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="8d6bd-115">リモート デバイスとアプリを検出します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-115">Discover remote devices and apps</span></span>

<span data-ttu-id="8d6bd-116">**MCDRemoteSystemWatcher**インスタンスは、このセクションのコア機能を処理します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-116">An **MCDRemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="8d6bd-117">リモート システムを検出するには、クラスで宣言します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-117">Declare it in the class which is to discover remote systems.</span></span>

`MCDRemoteSystemWatcher* _watcher;`

<span data-ttu-id="8d6bd-118">ウォッチャーを作成して、デバイスの検出を開始する前にどのような種類のデバイスのアプリの対象を決定する検索フィルターを追加したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-118">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="8d6bd-119">これらは、ユーザーの入力またはユース ケースに応じて、アプリにハードコーディングで決定できます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-119">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

<span data-ttu-id="8d6bd-120">サンプル アプリから次のコードでは、作成して、アプリを解析し、検出されたデバイスとの対話を許可する watcher のインスタンスを開始する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-120">The following code from the sample app demonstrates how to create and start a watcher instance allowing your app to parse and interact with the devices that are discovered.</span></span>

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

<span data-ttu-id="8d6bd-121">ここで、イベント ハンドラー メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-121">The event handler methods are defined here.</span></span>

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

<span data-ttu-id="8d6bd-122">アプリが検出されたデバイスのセットを維持することをお勧めします。 (によって表される**MCDRemoteSystem**インスタンス) と、UI で使用可能なデバイスと (表示名とデバイスの種類) などのアプリに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-122">We recommend that your app maintain a set of discovered devices (represented by **MCDRemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="8d6bd-123">1 回`[_watcher start]`が呼び出されると、リモート システムの使用状況の監視を開始して接続されているデバイスが検出された、更新、または検出されたデバイスのセットから削除されるときにイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-123">Once `[_watcher start]` is called, it will begin watching for remote system activity and will raise events when connected devices are discovered, updated, or removed from the set of detected devices.</span></span> <span data-ttu-id="8d6bd-124">はスキャン継続的に、バック グラウンドでため、監視を停止することをお勧め (で`[_watcher stop]`) とが不要になったため、不要なネットワーク通信とバッテリの消耗します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-124">It will scan continuously in the background, so it is recommended that you stop the watcher (with `[_watcher stop]`) when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="8d6bd-125">ユース ケースの例: リモート起動して、リモート アプリ サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-125">Example use case: implementing remote launching and remote app services</span></span>
<span data-ttu-id="8d6bd-126">この時点で、コードにしておくの作業一覧**MCDRemoteSystem**使用可能なデバイスを参照するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-126">At this point in your code, you should have a working list of **MCDRemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="8d6bd-127">これらのデバイスで何は、アプリの機能によって異なります。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-127">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="8d6bd-128">相互作用の主な型では、リモート起動してリモート アプリのサービスが。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-128">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="8d6bd-129">これらは、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-129">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="8d6bd-130">A) リモート起動</span><span class="sxs-lookup"><span data-stu-id="8d6bd-130">A) Remote launching</span></span>

<span data-ttu-id="8d6bd-131">次のコードのいずれかを選択する方法を示しています、 **MCDRemoteSystem**オブジェクト (理想的にはこれは、UI コントロールを介して) し、使用して**MCDRemoteLauncher**アプリと互換性のあるを渡すことで、上のアプリを起動するにはURI。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-131">The following code shows how to select one of the **MCDRemoteSystem** objects (ideally this is done through a UI control) and then use **MCDRemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span>

<span data-ttu-id="8d6bd-132">リモートからの起動 (である場合、ホスト デバイスが起動する URI スキーム用の既定のアプリで指定された URI) リモート デバイスを対象にできることを確認することが重要_または_にそのデバイスにリモート アプリケーションを特定します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-132">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span>

<span data-ttu-id="8d6bd-133">検出をデバイス レベルで最初に実行前のセクションで示したように、(、 **MCDRemoteSystem**デバイスを表します) を呼び出すことができますが、`getApplications`メソッドを**MCDRemoteSystem**インスタンスの配列を取得する**MCDRemoteSystemApp** (準備手順で、独自のアプリを登録したのと同様に、接続されているデバイス プラットフォームを使用する登録されているリモート デバイスでアプリを表すオブジェクト上記の場合)。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-133">As the previous section demonstrated, discovery happens at the device level first (an **MCDRemoteSystem** represents a device), but you can call the `getApplications` method on an **MCDRemoteSystem** instance to get an array of **MCDRemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="8d6bd-134">両方**MCDRemoteSystem**と**MCDRemoteSystemApp**作成に使用できます、 **MCDRemoteSystemConnectionRequest**URI の起動に必要なものであります。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-134">Both **MCDRemoteSystem** and **MCDRemoteSystemApp** can be used to construct a **MCDRemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

<span data-ttu-id="8d6bd-135">サンプルを次のコードでは、接続要求経由で URI のリモートの起動を示します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-135">The following code from the sample shows the remote launching of a URI over a connection request.</span></span>

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

<span data-ttu-id="8d6bd-136">によって送信される URI は、特定の状態またはリモート デバイス上の構成でのアプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-136">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="8d6bd-137">これにより、中断することがなく別のデバイスで映画を見てなど、ユーザーのタスクを継続する能力。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-137">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span>

<span data-ttu-id="8d6bd-138">によって、使用を対象となるシステム上のアプリを取り扱うことが、URI の場合を対象にする必要があります。 または複数のアプリで処理できます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-138">Depending on your use, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="8d6bd-139">**[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** クラスと **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** クラスは、これを行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-139">The **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** class and **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="8d6bd-140">B) リモート アプリ サービス</span><span class="sxs-lookup"><span data-stu-id="8d6bd-140">B) Remote app services</span></span>

<span data-ttu-id="8d6bd-141">IOS アプリでは、その他のデバイス上の app services と対話するデバイスの接続ポータルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-141">Your iOS app can use the Connected Devices Portal to interact with app services on other devices.</span></span> <span data-ttu-id="8d6bd-142">これにより、他のデバイスと通信する方法は多数&mdash;ホスト デバイスの前面にアプリを表示する必要はありませんすべて。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-142">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span>

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="8d6bd-143">ターゲット デバイスでアプリ サービスをセットアップする</span><span class="sxs-lookup"><span data-stu-id="8d6bd-143">Set up the app service on the target device</span></span>
<span data-ttu-id="8d6bd-144">このガイドを使用して、 [Roman テスト アプリの Windows](http://aka.ms/romeapp)そのターゲット アプリケーションのサービスとして。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-144">This guide will use the [Roman Test App for Windows](http://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="8d6bd-145">そのため、次のコードは、特定のリモート システムでは、その特定のアプリ サービスを検索する iOS アプリになります。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-145">Therefore, the code below will cause an iOS app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="8d6bd-146">このシナリオをテストする場合は、Windows デバイスで Roman テスト アプリをダウンロードし、サインインしている同じ MSA 前の準備手順で使用したかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-146">If you wish to test this scenario, download the Roman Test App on a Windows device and make sure you are signed in with the same MSA that you used in the preliminary steps above.</span></span>

<span data-ttu-id="8d6bd-147">UWP アプリ サービスを作成する方法に関する手順については、次を参照してください。[を作成する (UWP) アプリ サービスの使用と](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-147">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="8d6bd-148">接続されたデバイスと互換性のあるサービスを作成するには、いくつか変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-148">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="8d6bd-149">参照してください、[リモート アプリ サービスの UWP ガイド](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)これを行う方法の詳細について。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-149">See the [UWP guide for remote app services](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="8d6bd-150">クライアント デバイスにアプリ サービスの接続を開く</span><span class="sxs-lookup"><span data-stu-id="8d6bd-150">Open an app service connection on the client device</span></span>
<span data-ttu-id="8d6bd-151">IOS アプリには、リモート デバイスまたはアプリケーションへの参照を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-151">Your iOS app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="8d6bd-152">このシナリオの起動セクションなどを使用する必要を**MCDRemoteSystemConnectionRequest**、いずれかから構築できますが、 **MCDRemoteSystem**または**MCDRemoteSystemApp**システムで利用可能なアプリを表します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-152">Like the launch section, this scenario requires the use of a **MCDRemoteSystemConnectionRequest**, which can be constructed from either a **MCDRemoteSystem** or a **MCDRemoteSystemApp** representing an available app on the system.</span></span>

<span data-ttu-id="8d6bd-153">アプリは 2 つの文字列でその対象となるアプリ サービスを識別する必要がありますさらに、: *app service の名前*と*パッケージ識別子*します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-153">Additionally, your app will need to identify its targeted app service by two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="8d6bd-154">アプリのサービス プロバイダーのソース コードにあるこれらは (を参照してください[を作成する (UWP) アプリ サービスの使用と](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)詳細については)。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-154">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details).</span></span> <span data-ttu-id="8d6bd-155">これらの文字列を構築して、 **MCDAppServiceDescription**にフィードするが、 **MCDAppServiceConnection**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-155">Together these strings construct the **MCDAppServiceDescription**, which is fed into an **MCDAppServiceConnection** instance.</span></span>

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


#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="8d6bd-156">App service に送信するメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-156">Create a message to send to the app service</span></span>

<span data-ttu-id="8d6bd-157">送信するメッセージを格納する変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-157">Declare a variable to store the message to send.</span></span> <span data-ttu-id="8d6bd-158">Ios では、リモート アプリ サービスに送信するメッセージはで、 **NSDictionary**型。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-158">On iOS, the messages that you send to remote app services will be of the **NSDictionary** type.</span></span>

> [!NOTE]
> <span data-ttu-id="8d6bd-159">接続されているデバイス プラットフォームを変換、アプリが他のプラットフォーム上の app services を通信する場合、 **NSDictionary**受信側のプラットフォームで同等のコンストラクトにします。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-159">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **NSDictionary** into the equivalent construct on the receiving platform.</span></span> <span data-ttu-id="8d6bd-160">たとえば、 **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** アプリ サービスに変換します Windows にこのアプリから送信される、 [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) (.NET のオブジェクト。Framework)、app service によって、解釈できます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-160">For example, a **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** sent from this app to a Windows app service gets translated into a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="8d6bd-161">その他の方向に渡された情報には、逆の変換が行われます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-161">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="8d6bd-162">次のメソッドは、Windows 用の欧文テスト アプリの app service で解釈できるメッセージを提案します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-162">The following method crafts a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

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
> <span data-ttu-id="8d6bd-163">**NSDictionary**アプリとアプリのリモート サービスのシナリオでのサービス間で渡されるオブジェクトは、次の形式に従う必要があります。キーである必要があります**NSString**秒、および値可能性があります。**NSString**、数値型 (整数または浮動小数点) をボックス化、ブール値、ボックス化**NSDate**、 **NSUUID**、これらの型、またはその他のいずれかの同種のアレイ**NSDictionary**この仕様に一致するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-163">The **NSDictionary** objects that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be **NSString**s, and the values may be: **NSString**, boxed numeric types (integers or floating points), boxed booleans, **NSDate**, **NSUUID**, homogeneous arrays of any of these types, or other **NSDictionary** objects that meet this specification.</span></span> 

#### <a name="send-messages-to-the-app-service"></a><span data-ttu-id="8d6bd-164">App service へのメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-164">Send messages to the app service</span></span>

<span data-ttu-id="8d6bd-165">アプリ サービスの接続が確立され、メッセージが作成された、app service に送信は単純なとを接続インスタンスおよびメッセージへの参照を持つアプリで任意の場所から実行できます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-165">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the connection instance and the message.</span></span>

<span data-ttu-id="8d6bd-166">このサンプルを次のコードでは、app service と応答の処理へのメッセージの送信を示します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-166">The following code from the sample shows the sending of a message to an app service and the handling of the response.</span></span>

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

<span data-ttu-id="8d6bd-167">ローマ アプリの場合、応答には、この非常に単純なユース ケースでは、メッセージの応答の転送中の合計時間を取得する日付を比較できるように、作成された日付が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-167">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="8d6bd-168">リモート アプリ サービスで、1 つのメッセージ交換を終了します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-168">That concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="8d6bd-169">アプリ サービスの通信を完了します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-169">Finish app service communication</span></span>

<span data-ttu-id="8d6bd-170">アプリが終了すると、ターゲット デバイスのアプリのサービスと対話する 2 つのデバイス間の接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-170">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a><span data-ttu-id="8d6bd-171">関連トピック</span><span class="sxs-lookup"><span data-stu-id="8d6bd-171">Related topics</span></span>
* [<span data-ttu-id="8d6bd-172">API リファレンスのページ</span><span class="sxs-lookup"><span data-stu-id="8d6bd-172">API reference page</span></span>](api-reference-for-ios.md) 
* [<span data-ttu-id="8d6bd-173">iOS アプリをサンプルします。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-173">iOS sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [<span data-ttu-id="8d6bd-174">(UWP) アプリのリモート サービスと通信します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-174">Communicate with a remote app service (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="8d6bd-175">[作成し、app service (UWP) を使用する](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)します。</span><span class="sxs-lookup"><span data-stu-id="8d6bd-175">[Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>
