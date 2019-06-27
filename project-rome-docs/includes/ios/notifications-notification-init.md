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
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a><span data-ttu-id="5dc7b-103">TODO: APNs 通知互換性のためにアプリを構成する</span><span class="sxs-lookup"><span data-stu-id="5dc7b-103">TODO Configure your app to be APNs notification-compatible</span></span>

<span data-ttu-id="5dc7b-104">デベロッパー ダッシュボードでワークフローを完了したら、アプリの実際のコードを変更してプッシュ通知を受信可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-104">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="5dc7b-105">まず、バックグラウンドでの実行中にアプリが通知を受信できるように、"remote-notifications" **UIBackgroundMode** をアプリの _Info.plist_ に追加します。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-105">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="5dc7b-106">次に、アプリが起動したら、アラート通知を表示するために認可を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-106">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="5dc7b-107">これは、iOS のどのバージョンをターゲットにしているかに応じて、`-[UIApplication registerUsernotificationSettings:categories:]` または `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]` のどちらかを呼び出すことによって行われます。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-107">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="5dc7b-108">アプリが認可を取得したら、`-[UIApplication registerForRemoteNotifications]` を呼び出してリモート通知の受信登録ができます。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-108">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a><span data-ttu-id="5dc7b-109">Connected Devices Platform を、iOS の APNs ネイティブ プッシュ通知に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-109">Associate the Connected Devices Platform with APNs native push notification for iOS.</span></span> 
<span data-ttu-id="5dc7b-110">既に触れたように、アプリ クライアントは、登録プロセスの間、各モバイル プラットフォームで使用されているネイティブのプッシュ通知パイプラインに関する情報を、クライアント側 SDK と Connected Devices Platform に提供する必要があります。これは、ユーザーをターゲットにした通知をアプリ サーバーが MS Graph API を使って発行したときに、Graph の通知サービスが個々のアプリ クライアント エンドポイントに通知を拡散できるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-110">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via MS Graph APIs.</span></span>

<span data-ttu-id="5dc7b-111">上記の手順では、*notificationProvider* パラメーターを定義せずにプラットフォームを初期化しました。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-111">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="5dc7b-112">ここでは、 **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** を実装するオブジェクトを作成して渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-112">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="5dc7b-113">主な注意点は、`getNotificationRegistrationAsync:` メソッドが **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** インスタンスを返す必要があることです。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-113">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="5dc7b-114">**MCDNotificationRegistration** の役割は、通知サービス用のアクセス トークン (および関連情報) を Connected Devices Platform に提供することです。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-114">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="5dc7b-115">**MCDNotificationProvider** の実装でこの登録を配信します。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-115">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="5dc7b-116">その後は、プラットフォーム初期化呼び出しによって、プッシュ通知サービスへのアクセスがローカル プラットフォームに提供され、アプリがサーバー側の Connected Devices Platform からデータを受信できるようになります。このプラットフォームは、他のデバイスからの起動要求およびアプリ サービス メッセージを中継します。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-116">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="5dc7b-117">次に示すのは、サンプル アプリの **MCDNotificationProvider** の実装です。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-117">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="5dc7b-118">次のサンプル コードは、渡された **MCDNotificationRegistration** でこの **MCDNotificationProvider** を更新します。</span><span class="sxs-lookup"><span data-stu-id="5dc7b-118">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
