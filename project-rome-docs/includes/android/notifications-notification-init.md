---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 5b565b3eeaffb350f9296e38bf8bf9d46a58a64d
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98948530"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a><span data-ttu-id="313a4-103">Connected Devices Platform を各モバイル プラットフォームのネイティブのプッシュ通知に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="313a4-103">Associate the Connected Devices Platform with the native push notification for each mobile platform.</span></span> 

<span data-ttu-id="313a4-104">既に触れたように、アプリ クライアントは、登録プロセスの間、各モバイル プラットフォームで使用されているネイティブのプッシュ通知パイプラインに関する情報を、クライアント側 SDK と Connected Devices Platform に提供する必要があります。これは、ユーザーをターゲットにした通知をアプリ サーバーが Microsoft Graph API を使って発行したときに、Graph の通知サービスが個々のアプリ クライアント エンドポイントに通知を拡散できるようにするためです。</span><span class="sxs-lookup"><span data-stu-id="313a4-104">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via Microsoft Graph APIs.</span></span>

<span data-ttu-id="313a4-105">上記の手順では、`null` *notificationProvider* パラメーターを使用してプラットフォームを初期化しました。</span><span class="sxs-lookup"><span data-stu-id="313a4-105">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="313a4-106">ここでは、 **[NotificationProvider](/java/api/com.microsoft.connecteddevices.core._notification_provider)** を実装するオブジェクトを作成して渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="313a4-106">Here, you need to construct and pass in an object that implements **[NotificationProvider](/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="313a4-107">主な注意点は、`getNotificationRegistrationAsync` メソッドが **[NotificationRegistration](/java/api/com.microsoft.connecteddevices.core._notification_registration)** インスタンスを返す必要があることです。</span><span class="sxs-lookup"><span data-stu-id="313a4-107">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="313a4-108">**NotificationRegistration** の役割は、通知サービス用のアクセス トークン (および関連情報) を Connected Devices Platform に提供することです。</span><span class="sxs-lookup"><span data-stu-id="313a4-108">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

```java
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

<span data-ttu-id="313a4-109">**NotificationProvider** の実装でこの登録を配信します。</span><span class="sxs-lookup"><span data-stu-id="313a4-109">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="313a4-110">次に、**Platform** の初期化呼び出しで、プッシュ通知サービスへのアクセスをローカルの **Platform** に提供して、サーバー側の Microsoft Graph 通知からアプリがデータを受信できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="313a4-110">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the Microsoft Graph Notifications server-side.</span></span> 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a><span data-ttu-id="313a4-111">着信プッシュ通知をクライアント SDK に渡す</span><span class="sxs-lookup"><span data-stu-id="313a4-111">Pass incoming push notifications to the client SDK</span></span>
<span data-ttu-id="313a4-112">ここで、`onMessageReceived` メソッド (通知処理メソッド) の特殊なオーバーロードによって、ネイティブ リスナー サービス クラス (この場合は [FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService)。このチュートリアルでは Firebase Cloud Messaging を使用するため) を拡張することだけです。</span><span class="sxs-lookup"><span data-stu-id="313a4-112">Now, extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this tutorial uses Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

<span data-ttu-id="313a4-113">コンプライアンス、セキュリティ、潜在的な最適化のため、サーバー側の Graph 通知から受信する Google Cloud Messaging 通知は、アプリ サーバーによって最初に公開される一切のデータを含まないショルダー タップである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="313a4-113">Due to compliance, security, and potential optimizations, the incoming Google Cloud Messaging notification coming from Graph Notifications server-side could be a shoulder tap, which doesn’t contain any data that is initially published by the app server.</span></span> <span data-ttu-id="313a4-114">アプリ サーバーによって発行された実際の通知内容の取得は、クライアント側の SDK API の背後に隠されています。</span><span class="sxs-lookup"><span data-stu-id="313a4-114">The retrieval of the actual notification content published by the app server is hidden behind client-side SDK APIs.</span></span> <span data-ttu-id="313a4-115">このため SDK は、アプリ クライアントが常に、受信した Google Cloud Messaging ペイロードを SDK に渡すという一貫したプログラミング パターンを提供できます。</span><span class="sxs-lookup"><span data-stu-id="313a4-115">Because of this, the SDK can provide a consistent programming pattern in which the app client always passes the incoming Google Cloud Messaging payload to the SDK.</span></span> <span data-ttu-id="313a4-116">これによって SDK は、(Android のネイティブ Google Cloud Messaging チャネルが他の目的のためにアプリ クライアントによって使用されている場合に) これが Connected Device Platform のシナリオ向けの通知であるかどうか、また、この受信した通知はどのシナリオや機能 (Graph 通知、ユーザー アクティビティ、その他) に対応しているのかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="313a4-116">This allows the SDK to determine whether this is a notification for Connected Device Platform scenarios or not (in case Android’s native Google Cloud Messaging channel is used by the app client for other purposes), and which scenario/capability this incoming notification is corresponding to (Graph Notifications, User Activity, etc.).</span></span> <span data-ttu-id="313a4-117">その後、さまざまな種類のシナリオの処理に関する特定のロジックをアプリ クライアントによって実行できます。</span><span class="sxs-lookup"><span data-stu-id="313a4-117">Specific logics on handling different type of scenarios can then be executed by the app client after that.</span></span> 

```java
/**
* Check whether it's a Connected Devices Platform notification or not.
* If it is a Connected Devices Platform notification, it will notify the apps with the information in the notification.
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

<span data-ttu-id="313a4-118">アプリで Connected Devices Platform からの通知を処理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="313a4-118">Your app can now handle notifications from the Connected Devices Platform.</span></span>