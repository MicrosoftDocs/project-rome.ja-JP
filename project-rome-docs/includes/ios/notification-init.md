---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 195e419e-ac8d-4e96-8faa-c3659570fa27
ms.localizationpriority: medium
ms.openlocfilehash: 1780fa768475015946b5e33add55ac0f9f247f86
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801154"
---
## <a name="preliminary-setup-for-push-notifications"></a>プッシュ通知の準備段階のセットアップ

### <a name="register-your-app-for-push-notifications"></a>プッシュ通知のためにアプリを登録する

[Apple Push Notification](https://developer.apple.com/notifications/) のサポートのためにアプリケーションを登録します。 受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a>Connected Devices Platform へのクロスデバイス アクセスのためにアプリフォームを登録する

次に、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録します。 これは、先の準備手順で説明した Windows デベロッパー センターへの登録とは異なる手続きです。 これは、Connected Devices Platform がネイティブのプッシュ通知サービスを使用して通知を送信することを承認します。 デベロッパーセンターのオンボーディング プロセスに必要なものは次のとおりです。
* アプリのクライアント ID。
* Apple Push Notification サービス キー。 これは、通知の形式でデータやコマンドを (ロックまたはスリープ状態になる可能性があるデバイス上の) アプリに配信するために必要です。 

### <a name="configure-your-app-to-be-notification-compatible"></a>通知互換性のためにアプリを構成する

デベロッパー ダッシュボードでワークフローを完了したら、アプリの実際のコードを変更してプッシュ通知を受信可能にする必要があります。 まず、バックグラウンドでの実行中にアプリが通知を受信できるように、"remote-notifications" **UIBackgroundMode** をアプリの _Info.plist_ に追加します。 

TBD

次に、アプリが起動したら、アラート通知を表示するために認可を要求する必要があります。 これは、iOS のどのバージョンをターゲットにしているかに応じて、`-[UIApplication registerUsernotificationSettings:categories:]` または `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]` のどちらかを呼び出すことによって行われます。 アプリが認可を取得したら、`-[UIApplication registerForRemoteNotifications]` を呼び出してリモート通知の受信登録ができます。 

Connected Devices Platform からの一部の通知はアラートを表示し、これらのアラートのテキストはローカライズ可能であり、アプリケーションの文字列リソースに挿入する必要があります。 アプリの _en.lproj\Localizable.strings_ ファイルで次のリソース タグを定義する必要があります。 このファイルの作成が必要になる場合があります。 Xcode で **[New] (新規)** を選択し、ファイルの種類 "Strings" を検索し、_Localizable.strings_ という名前のファイルを作成します。

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a>通知サービスをローカルのプラットフォームに関連付ける

最後に、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。 上記の手順では、*notificationProvider* パラメーターを定義せずにプラットフォームを初期化しました。 ここでは、 **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** を実装するオブジェクトを作成して渡す必要があります。 主な注意点は、`getNotificationRegistrationAsync:` メソッドが **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** インスタンスを返す必要があることです。 **MCDNotificationRegistration** の役割は、通知サービス用のアクセス トークン (および関連情報) を Connected Devices Platform に提供することです。

**MCDNotificationProvider** の実装でこの登録を配信します。 その後は、プラットフォーム初期化呼び出しによって、プッシュ通知サービスへのアクセスがローカル プラットフォームに提供され、アプリがサーバー側の Connected Devices Platform からデータを受信できるようになります。このプラットフォームは、他のデバイスからの起動要求およびアプリ サービス メッセージを中継します。 

次に示すのは、サンプル アプリの **MCDNotificationProvider** の実装です。

```ObjectiveC
@implementation NotificationProvider
{
    MCDRegistrationUpdatedEvent* _registrationUpdated;
    MCDNotificationRegistration* _notificationRegistration;
}

+ (instancetype)sharedInstance
{
    static NotificationProvider* sharedInstance = nil;

    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{ sharedInstance = [[NotificationProvider alloc] init]; });

    return sharedInstance;
}

+ (void)updateNotificationRegistration:(MCDNotificationRegistration*)notificationRegistration
{
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0),
        ^{ [[NotificationProvider sharedInstance] _updateNotificationRegistration:notificationRegistration]; });
}

// MCDNotificationProvider
@synthesize registrationUpdated = _registrationUpdated;

- (void)getNotificationRegistrationAsync:(nonnull void (^)(MCDNotificationRegistration* _Nullable, NSError* _Nullable))completionBlock
{
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{ completionBlock(_notificationRegistration, nil); });
}

- (instancetype)init
{
    if (self = [super init])
    {
        _registrationUpdated = [MCDRegistrationUpdatedEvent new];
    }

    return self;
}

- (void)_updateNotificationRegistration:(MCDNotificationRegistration*)notificationRegistration
{
    _notificationRegistration = notificationRegistration;

    [_registrationUpdated raiseWithNotificationRegistration:notificationRegistration];
}
@end
```

次のサンプル コードは、渡された **MCDNotificationRegistration** でこの **MCDNotificationProvider** を更新します。

```ObjectiveC
/*
* NotificationRegistration is constructed with four parameters:
* Type: This is GCM or FCM or APN (the notification platform type).
* Token: This is the NSData that APNs sends to your app delegate's didRegisterForRemoteNotificationsWithDeviceToken: method. You must convert the NSData into a string by hex-encoding it.
* SenderId: This is your app’s bundle identifier. 
* DisplayName: This should be the name of the app that you used when you registered it on the Microsoft dev portal. 
*/
[NotificationProvider
    updateNotificationRegistration:[[MCDNotificationRegistration alloc]
        initWithNotificationType:MCDNotificationTypeAPN
        token:deviceTokenStr
        appId:[[NSBundle mainBundle] bundleIdentifier]
        appDisplayName:(NSString*)[[NSBundle mainBundle]
            objectForInfoDictionaryKey:@"CFBundleDisplayName"]]];
```
