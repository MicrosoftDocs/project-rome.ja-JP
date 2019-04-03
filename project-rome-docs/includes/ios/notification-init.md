---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 195e419e-ac8d-4e96-8faa-c3659570fa27
ms.localizationpriority: medium
ms.openlocfilehash: 1780fa768475015946b5e33add55ac0f9f247f86
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909664"
---
## <a name="preliminary-setup-for-push-notifications"></a>プッシュ通知の暫定的なセットアップ

### <a name="register-your-app-for-push-notifications"></a>プッシュ通知をアプリを登録します。

アプリケーションを登録する[Apple Push Notification](https://developer.apple.com/notifications/)をサポートします。 送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a>フォーム クロス デバイスのデバイス プラットフォームの接続アクセスをアプリケーションの登録します。

次に、アプリを登録、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。 これは、上記の準備手順で説明した、Windows デベロッパー センターの登録から別のプロシージャです。 これには、ネイティブのプッシュ通知サービスを使用して通知を送信する接続されているデバイス プラットフォームが認証されます。 デベロッパー センターで、オンボード プロセスが必要です。
* アプリのクライアント id。
* Apple Push Notification Service のキー。 これは必要です (デバイスがロックされているかスリープ状態にあります) 上のアプリにデータとコマンドを配信するには通知の形式にします。 

### <a name="configure-your-app-to-be-notification-compatible"></a>アプリ通知互換性を構成します

開発者向けダッシュ ボードのワークフローを完了すると、プッシュ通知を受信できるアプリの実際のコードを変更する必要があります。 まず、「リモート通知」を追加することを確認してください**UIBackgroundMode**アプリの_Info.plist_アプリがバック グラウンドで実行中に通知を受信できるようにします。 

TBD

第 2 に、アプリの開始時に、アラート通知を表示するための承認を要求する必要があります。 これは、いずれかを呼び出すことで`-[UIApplication registerUsernotificationSettings:categories:]`または`-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`、対象としている iOS のバージョンによって異なります。 呼び出すことによってリモート通知を受信登録できますし、アプリが取得されると、承認、`-[UIApplication registerForRemoteNotifications]`します。 

接続されているデバイス プラットフォームから一部の通知、アラートが表示され、これらのアラートのテキストがローカライズ可能なは、アプリケーションの文字列リソースに挿入する必要があります。 アプリの次のリソース タグを定義する必要があります_en.lproj\Localizable.strings_ファイル。 このファイルを作成する必要があります。 Xcode で、次のように選択します。**新規**ファイルの種類"文字列"を検索し、という名前のファイルを作成、 _Localizable.strings_します。

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a>ローカルのプラットフォーム通知サービスを関連付ける

最後に、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。 定義することがなく、プラットフォームの初期化前の手順で、 *notificationProvider*パラメーター。 ここでは、作成して実装するオブジェクトで渡す必要があります **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** します。 重要なことに注意するは、`getNotificationRegistrationAsync:`メソッドを返す必要があります、 **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** インスタンス。 **MCDNotificationRegistration**通知サービスのアクセス トークン (および関連する情報) に接続されているデバイス プラットフォームを提供する責任を負います。

実装でこの登録を配信**MCDNotificationProvider**します。 プラットフォームの初期化呼び出しが起動要求とからアプリ サービスのメッセージをリレーするアプリをサーバー側接続されているデバイス プラットフォームからのデータの受信を許可する、プッシュ通知サービスにアクセスできるローカルのプラットフォームを提供し、その他のデバイス。 

実装を次に**MCDNotificationProvider**サンプル アプリから。

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

この更新プログラムの次のサンプル コード**MCDNotificationProvider**を入力で**MCDNotificationRegistration**します。

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
