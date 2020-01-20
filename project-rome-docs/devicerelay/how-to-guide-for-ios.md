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
# <a name="implementing-device-relay-for-ios"></a>iOS のデバイス リレーの実装

Project Rome のデバイス リレー機能は、2 つの主な機能であるリモート起動 (コマンド実行とも呼びます) とアプリ サービスをサポートする一連の API で構成されています。

リモート起動 API は、リモート デバイス上のプロセスがローカル デバイスから開始されるシナリオをサポートします。 たとえば、ユーザーが車に乗りながら電話でラジオを聴きますが、帰宅したらホーム ステレオに接続した Xbox に電話を使用して再生を転送することがあります。

アプリケーションは App Services API を使用して 2 つのデバイス間に永続的なパイプラインを確立し、任意の内容を含むメッセージをこのパイプライン経由で送信することができます。 たとえば、モバイル デバイス上で実行されている写真共有アプリが、写真を取得するためにユーザーの PC との接続を確立することができます。

Project Rome の機能は、Connected Devices Platform と呼ばれる基盤プラットフォームによってサポートされます。 このガイドでは、Connected Devices Platform を初めて使用するために必要な手順と、このプラットフォームを使用してデバイス リレー関連機能を実装する方法について説明します。

この手順では、GitHub から入手できる [Project Rome iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)のコードを参照します。  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Connected Devices Platform と通知の設定

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームの使用

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>リモートのデバイスとアプリの検出

**MCDRemoteSystemWatcher** インスタンスは、このセクションのコア機能を処理します。 これは、リモート システムを検出するクラスの中で宣言します。

`MCDRemoteSystemWatcher* _watcher;`

ウォッチャーを作成してデバイスの検出を開始する前に、検出フィルターを追加して、どのような種類のデバイスをアプリでターゲットにするかを決定することができます。 ユース ケースに応じて、これらはユーザーの入力によって決定、またはアプリにハードコードすることができます。

サンプル アプリの次のコードは、検出されたデバイスをアプリで解析し、それらと対話するためのウォッチャー インスタンスを作成して起動する方法を示しています。

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

ここでは、イベント ハンドラー メソッドを定義します。

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

(**MCDRemoteSystem** インスタンスで表される) 検出されたデバイスのセットをアプリで管理し、利用可能なデバイスとそのアプリについての情報 (表示名やデバイスの種類など) を UI に表示することをお勧めします。 

`[_watcher start]` が呼び出されると、リモート システムのアクティビティの監視が始まります。接続デバイスが検出、更新、または検出済みデバイスのセットから削除されると、イベントが発生します。 バックグラウンドで継続的にスキャンされるため、不必要なネットワーク通信やバッテリの消耗を避けるために、不要になったら (`[_watcher stop]` を使用して) ウォッチャーを停止することをお勧めします。

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>ユース ケースの例: リモート起動とリモート アプリ サービスの実装
コードのこの時点で、利用可能なデバイスを参照する **MCDRemoteSystem** オブジェクトの有効な一覧があるはずです。 これらのデバイスに対して何をするかは、アプリの機能によって異なります。 主な種類の対話は、リモート起動とリモート アプリ サービスです。 これらについては、以降のセクションで説明します。

### <a name="a-remote-launching"></a>A) リモート起動

次のコードは、**MCDRemoteSystem** オブジェクトのいずれかを選択し (UI コントロールを使って行われるのが理想的です)、**MCDRemoteLauncher** を使用して、アプリと互換性のある URI を渡してそのデバイス上でアプリを起動する方法を示しています。

重要な注意点として、リモート起動でターゲットにできるのはリモート デバイス_または_そのデバイス上の特定のリモート アプリケーションであり、前者の場合、指定された URI を、ホスト デバイスがその URI スキーム用の既定のアプリで起動します。

前のセクションで説明したように、検出はまずデバイス レベルで行われます (**MCDRemoteSystem** はデバイスを表します) が、**MCDRemoteSystem** インスタンスの `getApplications` メソッドを呼び出して **MCDRemoteSystemApp** オブジェクトの配列を取得することができます。これらのオブジェクトが表すのは、(前述の準備手順で独自のアプリを登録したのと同様に) Connected Devices Platform を使用するように登録されている、リモート デバイス上のアプリです。 **MCDRemoteSystem** と **MCDRemoteSystemApp** のどちらを使用しても、URI を起動するために必要な **MCDRemoteSystemConnectionRequest** を作成できます。

サンプルの次のコードは、接続要求を経由した URI のリモート起動を示しています。

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

送信する URI に応じて、特定の状態または構成でリモート デバイス上でアプリを起動できます。 これにより、映画を観るなどのユーザー タスクを、中断することなく別のデバイス上で継続することができます。

用途によっては、ターゲット システム上のどのアプリも URI を処理できない、または複数のアプリがそれを処理できる状況への対応が必要な場合があります。 **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** クラスと **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** クラスは、これを行う方法を説明します。

### <a name="b-remote-app-services"></a>B) リモート アプリ サービス

iOS アプリは Connected Devices ポータルを使用して、他のデバイス上のアプリ サービスと対話できます。 これにより、他のデバイスと通信するための多くの方法が提供されます&mdash;アプリをホスト デバイスの前面に出す必要はまったくありません。

#### <a name="set-up-the-app-service-on-the-target-device"></a>ターゲット デバイスでアプリ サービスを設定する
このガイドでは、[Windows 用の Roman テスト アプリ](https://aka.ms/romeapp)をターゲット アプリ サービスとして使用します。 したがって、次のコードにより、iOS アプリは特定のリモート システム上でその特定のアプリ サービスを探します。 このシナリオをテストする場合は、Windows デバイス上で Roman テスト アプリをダウンロードし、先の準備手順で使用したのと同じ MSA でサインインしていることを確認してください。

独自の UWP アプリ サービスを記述する方法については、[アプリ サービスの作成と利用 (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) に関するページを参照してください。 サービスに Connected Devices との互換性を持たせるために、いくつかの変更を加える必要があります。 これを行う方法については、[リモート アプリ サービスに関する UWP ガイド](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)を参照してください。 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>クライアント デバイス上でアプリ サービス接続を開く
iOS アプリは、リモートのデバイスまたはアプリケーションへの参照を取得する必要があります。 起動のセクションと同様、このシナリオでは **MCDRemoteSystemConnectionRequest** を使用する必要があります。これは **MCDRemoteSystem** から、またはシステム上の利用可能なアプリを表す **MCDRemoteSystemApp** から作成できます。

さらにアプリは、*アプリ サービス名*と*パッケージ識別子*の 2 つの文字列によって、そのターゲットであるアプリ サービスを識別する必要があります。 これらはアプリ サービス プロバイダーのソース コードに含まれています。詳細については、[アプリ サービスの作成と利用 (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) に関するページを参照してください。 これらの文字列が合わさって **MCDAppServiceDescription** になり、これが **MCDAppServiceConnection** インスタンスに渡されます。

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


#### <a name="create-a-message-to-send-to-the-app-service"></a>アプリ サービスに送信するメッセージの作成

送信するメッセージを格納する変数を宣言します。 iOS では、リモート アプリ サービスに送信するメッセージは **NSDictionary** 型になります。

> [!NOTE]
> アプリが他のプラットフォーム上のアプリ サービスと通信するとき、Connected Devices Platform はこの **NSDictionary** を、受信側プラットフォームでの同等のコンストラクトに変換します。 たとえば、このアプリから Windows アプリ サービスに送信される **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** は、アプリ サービスが解釈できる (.NET Framework の) [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) オブジェクトに変換されます。 反対方向に渡される情報には、逆の変換が行われます。

次のメソッドは、Windows 用の Roman テスト アプリのアプリ サービスによって解釈できるメッセージを作成します。

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
> リモート アプリ サービスのシナリオでアプリとサービスの間で受け渡しされる **NSDictionary** オブジェクトは、次の形式に従う必要があります。キーは **NSString** である必要があり、次の値を入れることができます: **NSString**、ボックス数値型 (整数または浮動小数点数)、ボックス ブール値、**NSDate**、**NSUUID**、上記いずれかの型と同種の配列、またはこの仕様を満たすその他の **NSDictionary** オブジェクト。 

#### <a name="send-messages-to-the-app-service"></a>アプリ サービスにメッセージを送信する

アプリ サービス接続が確立されてメッセージが作成されたら、それをアプリ サービスに送信するのは簡単であり、接続インスタンスとメッセージへの参照があるアプリ内のどこからでも実行できます。

サンプルの次のコードは、アプリ サービスへのメッセージ送信と応答の処理を示しています。

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

Roman アプリの場合、応答にはそれが作成された日付が含まれているため、この非常に単純なユース ケースでは、日付を比較してメッセージ応答の合計転送時間を取得できます。

以上で、リモート アプリ サービスとの 1 回のメッセージ交換が終了します。

#### <a name="finish-app-service-communication"></a>アプリ サービス通信の終了

アプリがターゲット デバイスのアプリ サービスとの対話を終了したら、2 つのデバイス間の接続を閉じます。

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a>関連トピック
* [API リファレンス ページ](api-reference-for-ios.md) 
* [iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [リモート アプリ サービスとの通信 (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [アプリ サービスの作成と利用 (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)
