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
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="ea609-103">プッシュ通知の準備段階のセットアップ</span><span class="sxs-lookup"><span data-stu-id="ea609-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="ea609-104">プッシュ通知のためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="ea609-104">Register your app for push notifications</span></span>

<span data-ttu-id="ea609-105">[Apple Push Notification](https://developer.apple.com/notifications/) のサポートのためにアプリケーションを登録します。</span><span class="sxs-lookup"><span data-stu-id="ea609-105">Register your application for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="ea609-106">受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。</span><span class="sxs-lookup"><span data-stu-id="ea609-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a><span data-ttu-id="ea609-107">Connected Devices Platform へのクロスデバイス アクセスのためにアプリフォームを登録する</span><span class="sxs-lookup"><span data-stu-id="ea609-107">Register your app form cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="ea609-108">次に、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="ea609-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="ea609-109">これは、先の準備手順で説明した Windows デベロッパー センターへの登録とは異なる手続きです。</span><span class="sxs-lookup"><span data-stu-id="ea609-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="ea609-110">これは、Connected Devices Platform がネイティブのプッシュ通知サービスを使用して通知を送信することを承認します。</span><span class="sxs-lookup"><span data-stu-id="ea609-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="ea609-111">デベロッパーセンターのオンボーディング プロセスに必要なものは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ea609-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="ea609-112">アプリのクライアント ID。</span><span class="sxs-lookup"><span data-stu-id="ea609-112">Your app's client ID.</span></span>
* <span data-ttu-id="ea609-113">Apple Push Notification サービス キー。</span><span class="sxs-lookup"><span data-stu-id="ea609-113">The Apple Push Notification Service key.</span></span> <span data-ttu-id="ea609-114">これは、通知の形式でデータやコマンドを (ロックまたはスリープ状態になる可能性があるデバイス上の) アプリに配信するために必要です。</span><span class="sxs-lookup"><span data-stu-id="ea609-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="ea609-115">通知互換性のためにアプリを構成する</span><span class="sxs-lookup"><span data-stu-id="ea609-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="ea609-116">デベロッパー ダッシュボードでワークフローを完了したら、アプリの実際のコードを変更してプッシュ通知を受信可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea609-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="ea609-117">まず、バックグラウンドでの実行中にアプリが通知を受信できるように、"remote-notifications" **UIBackgroundMode** をアプリの _Info.plist_ に追加します。</span><span class="sxs-lookup"><span data-stu-id="ea609-117">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="ea609-118">TBD</span><span class="sxs-lookup"><span data-stu-id="ea609-118">TBD</span></span>

<span data-ttu-id="ea609-119">次に、アプリが起動したら、アラート通知を表示するために認可を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea609-119">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="ea609-120">これは、iOS のどのバージョンをターゲットにしているかに応じて、`-[UIApplication registerUsernotificationSettings:categories:]` または `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]` のどちらかを呼び出すことによって行われます。</span><span class="sxs-lookup"><span data-stu-id="ea609-120">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="ea609-121">アプリが認可を取得したら、`-[UIApplication registerForRemoteNotifications]` を呼び出してリモート通知の受信登録ができます。</span><span class="sxs-lookup"><span data-stu-id="ea609-121">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

<span data-ttu-id="ea609-122">Connected Devices Platform からの一部の通知はアラートを表示し、これらのアラートのテキストはローカライズ可能であり、アプリケーションの文字列リソースに挿入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea609-122">Some notifications from the Connected Devices Platform will present alerts, and the text of these alerts is localizable and must be inserted into your application's string resources.</span></span> <span data-ttu-id="ea609-123">アプリの _en.lproj\Localizable.strings_ ファイルで次のリソース タグを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea609-123">You must define the following resource tags in your app's _en.lproj\Localizable.strings_ file.</span></span> <span data-ttu-id="ea609-124">このファイルの作成が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ea609-124">You may need to create this file.</span></span> <span data-ttu-id="ea609-125">Xcode で **[New] (新規)** を選択し、ファイルの種類 "Strings" を検索し、_Localizable.strings_ という名前のファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="ea609-125">In Xcode, select **New**, search for the file type "Strings", and create a file called _Localizable.strings_.</span></span>

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="ea609-126">通知サービスをローカルのプラットフォームに関連付ける</span><span class="sxs-lookup"><span data-stu-id="ea609-126">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="ea609-127">最後に、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea609-127">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="ea609-128">上記の手順では、*notificationProvider* パラメーターを定義せずにプラットフォームを初期化しました。</span><span class="sxs-lookup"><span data-stu-id="ea609-128">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="ea609-129">ここでは、 **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** を実装するオブジェクトを作成して渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea609-129">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="ea609-130">主な注意点は、`getNotificationRegistrationAsync:` メソッドが **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** インスタンスを返す必要があることです。</span><span class="sxs-lookup"><span data-stu-id="ea609-130">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="ea609-131">**MCDNotificationRegistration** の役割は、通知サービス用のアクセス トークン (および関連情報) を Connected Devices Platform に提供することです。</span><span class="sxs-lookup"><span data-stu-id="ea609-131">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="ea609-132">**MCDNotificationProvider** の実装でこの登録を配信します。</span><span class="sxs-lookup"><span data-stu-id="ea609-132">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="ea609-133">その後は、プラットフォーム初期化呼び出しによって、プッシュ通知サービスへのアクセスがローカル プラットフォームに提供され、アプリがサーバー側の Connected Devices Platform からデータを受信できるようになります。このプラットフォームは、他のデバイスからの起動要求およびアプリ サービス メッセージを中継します。</span><span class="sxs-lookup"><span data-stu-id="ea609-133">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="ea609-134">次に示すのは、サンプル アプリの **MCDNotificationProvider** の実装です。</span><span class="sxs-lookup"><span data-stu-id="ea609-134">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="ea609-135">次のサンプル コードは、渡された **MCDNotificationRegistration** でこの **MCDNotificationProvider** を更新します。</span><span class="sxs-lookup"><span data-stu-id="ea609-135">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
