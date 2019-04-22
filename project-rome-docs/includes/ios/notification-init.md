---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 195e419e-ac8d-4e96-8faa-c3659570fa27
ms.localizationpriority: medium
ms.openlocfilehash: 1780fa768475015946b5e33add55ac0f9f247f86
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801154"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="bdd05-103">プッシュ通知の暫定的なセットアップ</span><span class="sxs-lookup"><span data-stu-id="bdd05-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="bdd05-104">プッシュ通知をアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="bdd05-104">Register your app for push notifications</span></span>

<span data-ttu-id="bdd05-105">アプリケーションを登録する[Apple Push Notification](https://developer.apple.com/notifications/)をサポートします。</span><span class="sxs-lookup"><span data-stu-id="bdd05-105">Register your application for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="bdd05-106">送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd05-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a><span data-ttu-id="bdd05-107">フォーム クロス デバイスのデバイス プラットフォームの接続アクセスをアプリケーションの登録します。</span><span class="sxs-lookup"><span data-stu-id="bdd05-107">Register your app form cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="bdd05-108">次に、アプリを登録、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。</span><span class="sxs-lookup"><span data-stu-id="bdd05-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="bdd05-109">これは、上記の準備手順で説明した、Windows デベロッパー センターの登録から別のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="bdd05-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="bdd05-110">これには、ネイティブのプッシュ通知サービスを使用して通知を送信する接続されているデバイス プラットフォームが認証されます。</span><span class="sxs-lookup"><span data-stu-id="bdd05-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="bdd05-111">デベロッパー センターで、オンボード プロセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="bdd05-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="bdd05-112">アプリのクライアント id。</span><span class="sxs-lookup"><span data-stu-id="bdd05-112">Your app's client ID.</span></span>
* <span data-ttu-id="bdd05-113">Apple Push Notification Service のキー。</span><span class="sxs-lookup"><span data-stu-id="bdd05-113">The Apple Push Notification Service key.</span></span> <span data-ttu-id="bdd05-114">これは必要です (デバイスがロックされているかスリープ状態にあります) 上のアプリにデータとコマンドを配信するには通知の形式にします。</span><span class="sxs-lookup"><span data-stu-id="bdd05-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="bdd05-115">アプリ通知互換性を構成します</span><span class="sxs-lookup"><span data-stu-id="bdd05-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="bdd05-116">開発者向けダッシュ ボードのワークフローを完了すると、プッシュ通知を受信できるアプリの実際のコードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd05-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="bdd05-117">まず、「リモート通知」を追加することを確認してください**UIBackgroundMode**アプリの_Info.plist_アプリがバック グラウンドで実行中に通知を受信できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bdd05-117">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="bdd05-118">TBD</span><span class="sxs-lookup"><span data-stu-id="bdd05-118">TBD</span></span>

<span data-ttu-id="bdd05-119">第 2 に、アプリの開始時に、アラート通知を表示するための承認を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd05-119">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="bdd05-120">これは、いずれかを呼び出すことで`-[UIApplication registerUsernotificationSettings:categories:]`または`-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`、対象としている iOS のバージョンによって異なります。</span><span class="sxs-lookup"><span data-stu-id="bdd05-120">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="bdd05-121">呼び出すことによってリモート通知を受信登録できますし、アプリが取得されると、承認、`-[UIApplication registerForRemoteNotifications]`します。</span><span class="sxs-lookup"><span data-stu-id="bdd05-121">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

<span data-ttu-id="bdd05-122">接続されているデバイス プラットフォームから一部の通知、アラートが表示され、これらのアラートのテキストがローカライズ可能なは、アプリケーションの文字列リソースに挿入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd05-122">Some notifications from the Connected Devices Platform will present alerts, and the text of these alerts is localizable and must be inserted into your application's string resources.</span></span> <span data-ttu-id="bdd05-123">アプリの次のリソース タグを定義する必要があります_en.lproj\Localizable.strings_ファイル。</span><span class="sxs-lookup"><span data-stu-id="bdd05-123">You must define the following resource tags in your app's _en.lproj\Localizable.strings_ file.</span></span> <span data-ttu-id="bdd05-124">このファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd05-124">You may need to create this file.</span></span> <span data-ttu-id="bdd05-125">Xcode で、次のように選択します。**新規**ファイルの種類"文字列"を検索し、という名前のファイルを作成、 _Localizable.strings_します。</span><span class="sxs-lookup"><span data-stu-id="bdd05-125">In Xcode, select **New**, search for the file type "Strings", and create a file called _Localizable.strings_.</span></span>

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="bdd05-126">ローカルのプラットフォーム通知サービスを関連付ける</span><span class="sxs-lookup"><span data-stu-id="bdd05-126">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="bdd05-127">最後に、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="bdd05-127">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="bdd05-128">定義することがなく、プラットフォームの初期化前の手順で、 *notificationProvider*パラメーター。</span><span class="sxs-lookup"><span data-stu-id="bdd05-128">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="bdd05-129">ここでは、作成して実装するオブジェクトで渡す必要があります **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** します。</span><span class="sxs-lookup"><span data-stu-id="bdd05-129">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="bdd05-130">重要なことに注意するは、`getNotificationRegistrationAsync:`メソッドを返す必要があります、 **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** インスタンス。</span><span class="sxs-lookup"><span data-stu-id="bdd05-130">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="bdd05-131">**MCDNotificationRegistration**通知サービスのアクセス トークン (および関連する情報) に接続されているデバイス プラットフォームを提供する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="bdd05-131">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="bdd05-132">実装でこの登録を配信**MCDNotificationProvider**します。</span><span class="sxs-lookup"><span data-stu-id="bdd05-132">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="bdd05-133">プラットフォームの初期化呼び出しが起動要求とからアプリ サービスのメッセージをリレーするアプリをサーバー側接続されているデバイス プラットフォームからのデータの受信を許可する、プッシュ通知サービスにアクセスできるローカルのプラットフォームを提供し、その他のデバイス。</span><span class="sxs-lookup"><span data-stu-id="bdd05-133">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="bdd05-134">実装を次に**MCDNotificationProvider**サンプル アプリから。</span><span class="sxs-lookup"><span data-stu-id="bdd05-134">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="bdd05-135">この更新プログラムの次のサンプル コード**MCDNotificationProvider**を入力で**MCDNotificationRegistration**します。</span><span class="sxs-lookup"><span data-stu-id="bdd05-135">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
