---
title: Ios デバイスのリレー機能を実装します。
description: このガイドでは、リモート デバイスとアプリを検出してアプリを起動し、またはアプリ サービスと対話する方法を説明します。
ms.topic: article
keywords: microsoft、windows、プロジェクト、ローマ、コマンド実行の ios
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: 11596720d9363f0ef29fd9c7bf0ccc5b4db62fae
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907734"
---
# <a name="implementing-device-relay-for-ios"></a>Ios デバイスのリレーを実装します。

プロジェクト ローマのデバイスのリレー機能は、2 つの主な機能をサポートする Api のセットで構成されています。 リモートの起動 (コマンドの実行とも呼ばれます) と app services。

リモート起動の Api は、ローカル デバイスからリモート デバイス上のプロセスが開始されるシナリオをサポートします。 たとえば、ユーザーは、携帯電話、車のラジオをリッスンする可能性がありますが自宅のステレオにフックされているが、Xbox に再生を転送する電話を使用するホーム取得すると。

App Services Api により、任意のコンテンツを含むメッセージを送信できる 2 つのデバイス間で永続的なパイプラインを確立するために使用できます。 などの写真をモバイル デバイスで実行されているアプリを共有では、写真を取得するために、ユーザーの PC に接続を確立する可能性があります。

プロジェクトのローマの機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームでサポートされます。 このガイドは、接続されているデバイス プラットフォームの使用を開始するために必要な手順について説明し、プラットフォームを使用して実装する方法を説明しますデバイス リレー機能に関連します。

この手順はからコードを参照、[プロジェクト ローマ iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)GitHub に用意されています。  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>接続されているデバイス プラットフォームと通知を設定します。

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームを使用します。

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>リモート デバイスとアプリを検出します。

**MCDRemoteSystemWatcher**インスタンスは、このセクションのコア機能を処理します。 リモート システムを検出するには、クラスで宣言します。

`MCDRemoteSystemWatcher* _watcher;`

ウォッチャーを作成して、デバイスの検出を開始する前にどのような種類のデバイスのアプリの対象を決定する検索フィルターを追加したい場合があります。 これらは、ユーザーの入力またはユース ケースに応じて、アプリにハードコーディングで決定できます。

サンプル アプリから次のコードでは、作成して、アプリを解析し、検出されたデバイスとの対話を許可する watcher のインスタンスを開始する方法を示します。

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

ここで、イベント ハンドラー メソッドを定義します。

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

アプリが検出されたデバイスのセットを維持することをお勧めします。 (によって表される**MCDRemoteSystem**インスタンス) と、UI で使用可能なデバイスと (表示名とデバイスの種類) などのアプリに関する情報を表示します。 

1 回`[_watcher start]`が呼び出されると、リモート システムの使用状況の監視を開始して接続されているデバイスが検出された、更新、または検出されたデバイスのセットから削除されるときにイベントが発生します。 はスキャン継続的に、バック グラウンドでため、監視を停止することをお勧め (で`[_watcher stop]`) とが不要になったため、不要なネットワーク通信とバッテリの消耗します。

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>ユース ケースの例: リモート起動して、リモート アプリ サービスを実装します。
この時点で、コードにしておくの作業一覧**MCDRemoteSystem**使用可能なデバイスを参照するオブジェクト。 これらのデバイスで何は、アプリの機能によって異なります。 相互作用の主な型では、リモート起動してリモート アプリのサービスが。 これらは、次のセクションで説明します。

### <a name="a-remote-launching"></a>A) リモート起動

次のコードのいずれかを選択する方法を示しています、 **MCDRemoteSystem**オブジェクト (理想的にはこれは、UI コントロールを介して) し、使用して**MCDRemoteLauncher**アプリと互換性のあるを渡すことで、上のアプリを起動するにはURI。

リモートからの起動 (である場合、ホスト デバイスが起動する URI スキーム用の既定のアプリで指定された URI) リモート デバイスを対象にできることを確認することが重要_または_にそのデバイスにリモート アプリケーションを特定します。

検出をデバイス レベルで最初に実行前のセクションで示したように、(、 **MCDRemoteSystem**デバイスを表します) を呼び出すことができますが、`getApplications`メソッドを**MCDRemoteSystem**インスタンスの配列を取得する**MCDRemoteSystemApp** (準備手順で、独自のアプリを登録したのと同様に、接続されているデバイス プラットフォームを使用する登録されているリモート デバイスでアプリを表すオブジェクト上記の場合)。 両方**MCDRemoteSystem**と**MCDRemoteSystemApp**作成に使用できます、 **MCDRemoteSystemConnectionRequest**URI の起動に必要なものであります。

サンプルを次のコードでは、接続要求経由で URI のリモートの起動を示します。

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

によって送信される URI は、特定の状態またはリモート デバイス上の構成でのアプリを起動できます。 これにより、中断することがなく別のデバイスで映画を見てなど、ユーザーのタスクを継続する能力。

によって、使用を対象となるシステム上のアプリを取り扱うことが、URI の場合を対象にする必要があります。 または複数のアプリで処理できます。 **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** クラスと **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** クラスは、これを行う方法を説明します。

### <a name="b-remote-app-services"></a>B) リモート アプリ サービス

IOS アプリでは、その他のデバイス上の app services と対話するデバイスの接続ポータルを使用できます。 これにより、他のデバイスと通信する方法は多数&mdash;ホスト デバイスの前面にアプリを表示する必要はありませんすべて。

#### <a name="set-up-the-app-service-on-the-target-device"></a>ターゲット デバイスでアプリ サービスをセットアップする
このガイドを使用して、 [Roman テスト アプリの Windows](http://aka.ms/romeapp)そのターゲット アプリケーションのサービスとして。 そのため、次のコードは、特定のリモート システムでは、その特定のアプリ サービスを検索する iOS アプリになります。 このシナリオをテストする場合は、Windows デバイスで Roman テスト アプリをダウンロードし、同じ MSA または前の準備手順で使用する AAD でサインインしているかどうかを確認します。

UWP アプリ サービスを作成する方法に関する手順については、次を参照してください。[を作成する (UWP) アプリ サービスの使用と](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)します。 接続されたデバイスと互換性のあるサービスを作成するには、いくつか変更する必要があります。 参照してください、[リモート アプリ サービスの UWP ガイド](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)これを行う方法の詳細について。 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>クライアント デバイスにアプリ サービスの接続を開く
IOS アプリには、リモート デバイスまたはアプリケーションへの参照を取得する必要があります。 このシナリオの起動セクションなどを使用する必要を**MCDRemoteSystemConnectionRequest**、いずれかから構築できますが、 **MCDRemoteSystem**または**MCDRemoteSystemApp**システムで利用可能なアプリを表します。

アプリは 2 つの文字列でその対象となるアプリ サービスを識別する必要がありますさらに、: *app service の名前*と*パッケージ識別子*します。 アプリのサービス プロバイダーのソース コードにあるこれらは (を参照してください[を作成する (UWP) アプリ サービスの使用と](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)詳細については)。 これらの文字列を構築して、 **MCDAppServiceDescription**にフィードするが、 **MCDAppServiceConnection**インスタンス。

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


#### <a name="create-a-message-to-send-to-the-app-service"></a>App service に送信するメッセージを作成します。

送信するメッセージを格納する変数を宣言します。 Ios では、リモート アプリ サービスに送信するメッセージはで、 **NSDictionary**型。

> [!NOTE]
> 接続されているデバイス プラットフォームを変換、アプリが他のプラットフォーム上の app services を通信する場合、 **NSDictionary**受信側のプラットフォームで同等のコンストラクトにします。 たとえば、 **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** アプリ サービスに変換します Windows にこのアプリから送信される、 [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) (.NET のオブジェクト。Framework)、app service によって、解釈できます。 その他の方向に渡された情報には、逆の変換が行われます。

次のメソッドは、Windows 用の欧文テスト アプリの app service で解釈できるメッセージを提案します。

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
> **NSDictionary**アプリとアプリのリモート サービスのシナリオでのサービス間で渡されるオブジェクトは、次の形式に従う必要があります。キーである必要があります**NSString**秒、および値可能性があります。**NSString**、数値型 (整数または浮動小数点) をボックス化、ブール値、ボックス化**NSDate**、 **NSUUID**、これらの型、またはその他のいずれかの同種のアレイ**NSDictionary**この仕様に一致するオブジェクト。 

#### <a name="send-messages-to-the-app-service"></a>App service へのメッセージを送信します。

アプリ サービスの接続が確立され、メッセージが作成された、app service に送信は単純なとを接続インスタンスおよびメッセージへの参照を持つアプリで任意の場所から実行できます。

このサンプルを次のコードでは、app service と応答の処理へのメッセージの送信を示します。

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

ローマ アプリの場合、応答には、この非常に単純なユース ケースでは、メッセージの応答の転送中の合計時間を取得する日付を比較できるように、作成された日付が含まれます。

リモート アプリ サービスで、1 つのメッセージ交換を終了します。

#### <a name="finish-app-service-communication"></a>アプリ サービスの通信を完了します。

アプリが終了すると、ターゲット デバイスのアプリのサービスと対話する 2 つのデバイス間の接続を閉じます。

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a>関連トピック
* [API リファレンスのページ](api-reference-for-ios.md) 
* [iOS アプリをサンプルします。](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [(UWP) アプリのリモート サービスと通信します。](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [作成し、app service (UWP) を使用する](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)します。
