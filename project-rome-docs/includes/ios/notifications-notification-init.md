---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 30df8538-1c1f-498f-af25-0be0aed687c8
ms.localizationpriority: medium
ms.openlocfilehash: 95b6dd68706a1582a91718a48ba7961cd8d07ddf
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801504"
---
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a>TODO: APNs 通知互換性のためにアプリを構成する

デベロッパー ダッシュボードでワークフローを完了したら、アプリの実際のコードを変更してプッシュ通知を受信可能にする必要があります。 まず、バックグラウンドでの実行中にアプリが通知を受信できるように、"remote-notifications" **UIBackgroundMode** をアプリの _Info.plist_ に追加します。 

次に、アプリが起動したら、アラート通知を表示するために認可を要求する必要があります。 これは、iOS のどのバージョンをターゲットにしているかに応じて、`-[UIApplication registerUsernotificationSettings:categories:]` または `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]` のどちらかを呼び出すことによって行われます。 アプリが認可を取得したら、`-[UIApplication registerForRemoteNotifications]` を呼び出してリモート通知の受信登録ができます。 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a>Connected Devices Platform を、iOS の APNs ネイティブ プッシュ通知に関連付けます。 
既に触れたように、アプリ クライアントは、登録プロセスの間、各モバイル プラットフォームで使用されているネイティブのプッシュ通知パイプラインに関する情報を、クライアント側 SDK と Connected Devices Platform に提供する必要があります。これは、ユーザーをターゲットにした通知をアプリ サーバーが MS Graph API を使って発行したときに、Graph の通知サービスが個々のアプリ クライアント エンドポイントに通知を拡散できるようにするためです。

上記の手順では、*notificationProvider* パラメーターを定義せずにプラットフォームを初期化しました。 ここでは、 **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** を実装するオブジェクトを作成して渡す必要があります。 主な注意点は、`getNotificationRegistrationAsync:` メソッドが **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** インスタンスを返す必要があることです。 **MCDNotificationRegistration** の役割は、通知サービス用のアクセス トークン (および関連情報) を Connected Devices Platform に提供することです。

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
