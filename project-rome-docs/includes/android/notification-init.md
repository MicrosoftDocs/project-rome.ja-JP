---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801574"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="6fd78-103">プッシュ通知の暫定的なセットアップ</span><span class="sxs-lookup"><span data-stu-id="6fd78-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="6fd78-104">プッシュ通知をアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="6fd78-104">Register your app for push notifications</span></span>

<span data-ttu-id="6fd78-105">通知のサポートを Google にアプリケーションを登録します。</span><span class="sxs-lookup"><span data-stu-id="6fd78-105">Register your application with Google for notification support.</span></span> <span data-ttu-id="6fd78-106">送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fd78-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a><span data-ttu-id="6fd78-107">デバイス間の接続されているデバイス プラットフォーム アクセス用アプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="6fd78-107">Register your app for cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="6fd78-108">次に、アプリを登録、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。</span><span class="sxs-lookup"><span data-stu-id="6fd78-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="6fd78-109">これは、上記の準備手順で説明した、Windows デベロッパー センターの登録から別のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="6fd78-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="6fd78-110">これには、ネイティブのプッシュ通知サービスを使用して通知を送信する接続されているデバイス プラットフォームが認証されます。</span><span class="sxs-lookup"><span data-stu-id="6fd78-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="6fd78-111">デベロッパー センターで、オンボード プロセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="6fd78-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="6fd78-112">アプリのクライアント id。</span><span class="sxs-lookup"><span data-stu-id="6fd78-112">Your app's client ID.</span></span>
* <span data-ttu-id="6fd78-113">Google Cloud Messaging のキー。</span><span class="sxs-lookup"><span data-stu-id="6fd78-113">The Google Cloud Messaging key.</span></span> <span data-ttu-id="6fd78-114">これは必要です (デバイスがロックされているかスリープ状態にあります) 上のアプリにデータとコマンドを配信するにはプッシュ通知の形式でします。</span><span class="sxs-lookup"><span data-stu-id="6fd78-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of push notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="6fd78-115">アプリ通知互換性を構成します</span><span class="sxs-lookup"><span data-stu-id="6fd78-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="6fd78-116">開発者向けダッシュ ボードのワークフローが完了した後には、プッシュ通知を受信できるように、アプリの実際のコードを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fd78-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make it capable of receiving push notifications.</span></span> <span data-ttu-id="6fd78-117">参照してください[設定を Firebase Cloud Messaging クライアント Android でのアプリ](https://firebase.google.com/docs/cloud-messaging/android/client)これを行う方法がない場合。</span><span class="sxs-lookup"><span data-stu-id="6fd78-117">See [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client) if you are unsure how to do this.</span></span>

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="6fd78-118">ローカルのプラットフォーム通知サービスを関連付ける</span><span class="sxs-lookup"><span data-stu-id="6fd78-118">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="6fd78-119">最後に、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="6fd78-119">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="6fd78-120">上記の手順で、初期化、プラットフォームを`null` *notificationProvider*パラメーター。</span><span class="sxs-lookup"><span data-stu-id="6fd78-120">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="6fd78-121">ここでは、作成して実装するオブジェクトで渡す必要があります **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** します。</span><span class="sxs-lookup"><span data-stu-id="6fd78-121">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="6fd78-122">重要なことに注意するは、`getNotificationRegistrationAsync`メソッドを返す必要があります、 **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** インスタンス。</span><span class="sxs-lookup"><span data-stu-id="6fd78-122">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="6fd78-123">**NotificationRegistration**通知サービスのアクセス トークン (および関連する情報) に接続されているデバイス プラットフォームを提供する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="6fd78-123">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>


```Java
private NotificationRegistration mNotificationRegistration;

// ...

/**
* NotificationRegistration is constructed with four parameters:
* Type: This is the notification platform type.
* Token: This is the string that GCM or FCM sends to your registration intent service.
* SenderId: This is the numeric Sender ID that you received when you registered your app for push notifications.
* DisplayName: This should be the name of the app that you used when you registered it on the Microsoft dev portal. 
*/
mNotificationRegistration = new NotificationRegistration(NotificationType.FCM, token, FCM_SENDER_ID, "MyAppName");
```

<span data-ttu-id="6fd78-124">実装でこの登録を配信**NotificationProvider**します。</span><span class="sxs-lookup"><span data-stu-id="6fd78-124">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="6fd78-125">次に、**プラットフォーム**初期化呼び出しがローカルに提供する必要があります**プラットフォーム**プッシュ通知サービスにアクセスできる、サーバー側の接続されたデバイスからデータを受信するアプリを許可します。プラットフォームの起動要求とその他のデバイスからアプリ サービスのメッセージを中継します。</span><span class="sxs-lookup"><span data-stu-id="6fd78-125">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="6fd78-126">すべて行う必要があるようになりましたが、ネイティブのリスナーを拡張サービス クラス ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService)ここでは、このガイドで使用されるため、Firebase Cloud Messaging) の特殊なオーバー ロードで、 `onMessageReceived` (メソッド通知の処理方法の場合)。</span><span class="sxs-lookup"><span data-stu-id="6fd78-126">All you need to do now is extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this guide used Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

```Java
/**
* Check whether it's a rome notification or not.
* If it is a rome notification, it will notify the apps with the information in the notification.
* @param from describes message sender.
* @param data message data as String key/value pairs.
*/
@Override
public void onMessageReceived(String from, Bundle data) {
    Log.d(TAG, "From: " + from);

    // Ensure that the Platform is initialized here before going on
    // ...

    // This method passes the data to the Connected Devices Platform if is compatible.
    if (!NotificationReceiver.Receive(data)) {
        // a value of false indicates a non-Rome notification
        Log.d(TAG, "GCM client received a message that was not a Rome notification");
    }
}
```

<span data-ttu-id="6fd78-127">アプリは、接続されているデバイス プラットフォームから通知を処理することがようになりました。</span><span class="sxs-lookup"><span data-stu-id="6fd78-127">Your app is now able to handle notifications from the Connected Devices Platform.</span></span>
