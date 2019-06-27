---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801574"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="4fb64-103">プッシュ通知の準備段階のセットアップ</span><span class="sxs-lookup"><span data-stu-id="4fb64-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="4fb64-104">プッシュ通知のためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="4fb64-104">Register your app for push notifications</span></span>

<span data-ttu-id="4fb64-105">通知のサポートのためにアプリケーションを Google に登録します。</span><span class="sxs-lookup"><span data-stu-id="4fb64-105">Register your application with Google for notification support.</span></span> <span data-ttu-id="4fb64-106">受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。</span><span class="sxs-lookup"><span data-stu-id="4fb64-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a><span data-ttu-id="4fb64-107">Connected Devices Platform へのクロスデバイス アクセスのためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="4fb64-107">Register your app for cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="4fb64-108">次に、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="4fb64-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="4fb64-109">これは、先の準備手順で説明した Windows デベロッパー センターへの登録とは異なる手続きです。</span><span class="sxs-lookup"><span data-stu-id="4fb64-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="4fb64-110">これは、Connected Devices Platform がネイティブのプッシュ通知サービスを使用して通知を送信することを承認します。</span><span class="sxs-lookup"><span data-stu-id="4fb64-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="4fb64-111">デベロッパーセンターのオンボーディング プロセスに必要なものは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4fb64-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="4fb64-112">アプリのクライアント ID。</span><span class="sxs-lookup"><span data-stu-id="4fb64-112">Your app's client ID.</span></span>
* <span data-ttu-id="4fb64-113">Google Cloud Messaging キー。</span><span class="sxs-lookup"><span data-stu-id="4fb64-113">The Google Cloud Messaging key.</span></span> <span data-ttu-id="4fb64-114">これは、プッシュ通知の形式でデータやコマンドを (ロックまたはスリープ状態になる可能性があるデバイス上の) アプリに配信するために必要です。</span><span class="sxs-lookup"><span data-stu-id="4fb64-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of push notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="4fb64-115">通知互換性のためにアプリを構成する</span><span class="sxs-lookup"><span data-stu-id="4fb64-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="4fb64-116">デベロッパー ダッシュボードでワークフローを完了したら、アプリの実際のコードを変更して、アプリでプッシュ通知を受信可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fb64-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make it capable of receiving push notifications.</span></span> <span data-ttu-id="4fb64-117">この方法がわからない場合は、[Android での Firebase Cloud Messaging クライアント アプリの設定](https://firebase.google.com/docs/cloud-messaging/android/client)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fb64-117">See [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client) if you are unsure how to do this.</span></span>

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="4fb64-118">通知サービスをローカルのプラットフォームに関連付ける</span><span class="sxs-lookup"><span data-stu-id="4fb64-118">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="4fb64-119">最後に、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fb64-119">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="4fb64-120">上記の手順では、`null` *notificationProvider* パラメーターを使用してプラットフォームを初期化しました。</span><span class="sxs-lookup"><span data-stu-id="4fb64-120">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="4fb64-121">ここでは、 **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** を実装するオブジェクトを作成して渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fb64-121">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="4fb64-122">主な注意点は、`getNotificationRegistrationAsync` メソッドが **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** インスタンスを返す必要があることです。</span><span class="sxs-lookup"><span data-stu-id="4fb64-122">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="4fb64-123">**NotificationRegistration** の役割は、通知サービス用のアクセス トークン (および関連情報) を Connected Devices Platform に提供することです。</span><span class="sxs-lookup"><span data-stu-id="4fb64-123">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>


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

<span data-ttu-id="4fb64-124">**NotificationProvider** の実装でこの登録を配信します。</span><span class="sxs-lookup"><span data-stu-id="4fb64-124">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="4fb64-125">その後は、**Platform** の初期化呼び出しによって、プッシュ通知サービスへのアクセスがローカルの **Platform** に提供され、アプリがサーバー側の Connected Devices Platform からデータを受信できるようになります。このプラットフォームは、他のデバイスからの起動要求およびアプリ サービス メッセージを中継します。</span><span class="sxs-lookup"><span data-stu-id="4fb64-125">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="4fb64-126">ここで行う必要があるのは、`onMessageReceived` メソッド (通知処理メソッド) の特殊なオーバーロードによって、ネイティブ リスナー サービス クラス (この場合は [FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService)。このガイドでは Firebase Cloud Messaging を使用するため) を拡張することだけです。</span><span class="sxs-lookup"><span data-stu-id="4fb64-126">All you need to do now is extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this guide used Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

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

<span data-ttu-id="4fb64-127">アプリで Connected Devices Platform からの通知を処理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4fb64-127">Your app is now able to handle notifications from the Connected Devices Platform.</span></span>
