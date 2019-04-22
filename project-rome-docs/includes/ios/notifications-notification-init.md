---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 30df8538-1c1f-498f-af25-0be0aed687c8
ms.localizationpriority: medium
ms.openlocfilehash: 95b6dd68706a1582a91718a48ba7961cd8d07ddf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801504"
---
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a>APNs 通知と互換性のあるアプリの TODO 構成

開発者向けダッシュ ボードのワークフローを完了すると、プッシュ通知を受信できるアプリの実際のコードを変更する必要があります。 まず、「リモート通知」を追加することを確認してください**UIBackgroundMode**アプリの_Info.plist_アプリがバック グラウンドで実行中に通知を受信できるようにします。 

第 2 に、アプリの開始時に、アラート通知を表示するための承認を要求する必要があります。 これは、いずれかを呼び出すことで`-[UIApplication registerUsernotificationSettings:categories:]`または`-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`、対象としている iOS のバージョンによって異なります。 呼び出すことによってリモート通知を受信登録できますし、アプリが取得されると、承認、`-[UIApplication registerForRemoteNotifications]`します。 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a>IOS の APNs ネイティブ プッシュ通知には、接続されているデバイス プラットフォームを関連付けます。 
ようにアプリのクライアントは既に触れましたが、グラフを許可するクライアント側の SDK を各モバイル プラットフォームとデバイスの接続されているプラットフォームの登録プロセス中に使用されているネイティブのプッシュ通知のパイプラインに関する知識を提供する必要がありますアプリケーション サーバーは、MS Graph Api を使用してユーザーを対象とした通知を発行するときのアプリのクライアント エンドポイントは各にファンアウト通知を通知サービス。

定義することがなく、プラットフォームの初期化前の手順で、 *notificationProvider*パラメーター。 ここでは、作成して実装するオブジェクトで渡す必要があります **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** します。 重要なことに注意するは、`getNotificationRegistrationAsync:`メソッドを返す必要があります、 **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** インスタンス。 **MCDNotificationRegistration**通知サービスのアクセス トークン (および関連する情報) に接続されているデバイス プラットフォームを提供する責任を負います。

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
