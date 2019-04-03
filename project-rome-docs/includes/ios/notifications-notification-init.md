---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 30df8538-1c1f-498f-af25-0be0aed687c8
ms.localizationpriority: medium
ms.openlocfilehash: 95b6dd68706a1582a91718a48ba7961cd8d07ddf
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907434"
---
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a><span data-ttu-id="b43fd-103">APNs 通知と互換性のあるアプリの TODO 構成</span><span class="sxs-lookup"><span data-stu-id="b43fd-103">TODO Configure your app to be APNs notification-compatible</span></span>

<span data-ttu-id="b43fd-104">開発者向けダッシュ ボードのワークフローを完了すると、プッシュ通知を受信できるアプリの実際のコードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b43fd-104">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="b43fd-105">まず、「リモート通知」を追加することを確認してください**UIBackgroundMode**アプリの_Info.plist_アプリがバック グラウンドで実行中に通知を受信できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b43fd-105">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="b43fd-106">第 2 に、アプリの開始時に、アラート通知を表示するための承認を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b43fd-106">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="b43fd-107">これは、いずれかを呼び出すことで`-[UIApplication registerUsernotificationSettings:categories:]`または`-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`、対象としている iOS のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b43fd-107">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="b43fd-108">呼び出すことによってリモート通知を受信登録できますし、アプリが取得されると、承認、`-[UIApplication registerForRemoteNotifications]`します。</span><span class="sxs-lookup"><span data-stu-id="b43fd-108">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a><span data-ttu-id="b43fd-109">IOS の APNs ネイティブ プッシュ通知には、接続されているデバイス プラットフォームを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="b43fd-109">Associate the Connected Devices Platform with APNs native push notification for iOS.</span></span> 
<span data-ttu-id="b43fd-110">ようにアプリのクライアントは既に触れましたが、グラフを許可するクライアント側の SDK を各モバイル プラットフォームとデバイスの接続されているプラットフォームの登録プロセス中に使用されているネイティブのプッシュ通知のパイプラインに関する知識を提供する必要がありますアプリケーション サーバーは、MS Graph Api を使用してユーザーを対象とした通知を発行するときのアプリのクライアント エンドポイントは各にファンアウト通知を通知サービス。</span><span class="sxs-lookup"><span data-stu-id="b43fd-110">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via MS Graph APIs.</span></span>

<span data-ttu-id="b43fd-111">定義することがなく、プラットフォームの初期化前の手順で、 *notificationProvider*パラメーター。</span><span class="sxs-lookup"><span data-stu-id="b43fd-111">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="b43fd-112">ここでは、作成して実装するオブジェクトで渡す必要があります **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** します。</span><span class="sxs-lookup"><span data-stu-id="b43fd-112">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="b43fd-113">重要なことに注意するは、`getNotificationRegistrationAsync:`メソッドを返す必要があります、 **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** インスタンス。</span><span class="sxs-lookup"><span data-stu-id="b43fd-113">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="b43fd-114">**MCDNotificationRegistration**通知サービスのアクセス トークン (および関連する情報) に接続されているデバイス プラットフォームを提供する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="b43fd-114">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="b43fd-115">実装でこの登録を配信**MCDNotificationProvider**します。</span><span class="sxs-lookup"><span data-stu-id="b43fd-115">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="b43fd-116">プラットフォームの初期化呼び出しが起動要求とからアプリ サービスのメッセージをリレーするアプリをサーバー側接続されているデバイス プラットフォームからのデータの受信を許可する、プッシュ通知サービスにアクセスできるローカルのプラットフォームを提供し、その他のデバイス。</span><span class="sxs-lookup"><span data-stu-id="b43fd-116">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="b43fd-117">実装を次に**MCDNotificationProvider**サンプル アプリから。</span><span class="sxs-lookup"><span data-stu-id="b43fd-117">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="b43fd-118">この更新プログラムの次のサンプル コード**MCDNotificationProvider**を入力で**MCDNotificationRegistration**します。</span><span class="sxs-lookup"><span data-stu-id="b43fd-118">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
