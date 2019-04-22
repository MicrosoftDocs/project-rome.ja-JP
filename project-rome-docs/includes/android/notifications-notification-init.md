---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 27ff12ef8b0773f1bd0e1960c285012f7e62fdc9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801798"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a><span data-ttu-id="a4b49-103">各モバイル プラットフォームのネイティブ プッシュ通知には、接続されているデバイス プラットフォームを関連付けます。</span><span class="sxs-lookup"><span data-stu-id="a4b49-103">Associate the Connected Devices Platform with the native push notification for each mobile platform.</span></span> 

<span data-ttu-id="a4b49-104">ようにアプリのクライアントは既に触れましたが、グラフを許可するクライアント側の SDK を各モバイル プラットフォームとデバイスの接続されているプラットフォームの登録プロセス中に使用されているネイティブのプッシュ通知のパイプラインに関する知識を提供する必要がありますアプリケーション サーバーは、Microsoft Graph Api を使用してユーザーを対象とした通知を発行するときのアプリのクライアント エンドポイントは各にファンアウト通知を通知サービス。</span><span class="sxs-lookup"><span data-stu-id="a4b49-104">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via Microsoft Graph APIs.</span></span>

<span data-ttu-id="a4b49-105">上記の手順で、初期化、プラットフォームを`null` *notificationProvider*パラメーター。</span><span class="sxs-lookup"><span data-stu-id="a4b49-105">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="a4b49-106">ここでは、作成して実装するオブジェクトで渡す必要があります **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** します。</span><span class="sxs-lookup"><span data-stu-id="a4b49-106">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="a4b49-107">重要なことに注意するは、`getNotificationRegistrationAsync`メソッドを返す必要があります、 **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** インスタンス。</span><span class="sxs-lookup"><span data-stu-id="a4b49-107">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="a4b49-108">**NotificationRegistration**通知サービスのアクセス トークン (および関連する情報) に接続されているデバイス プラットフォームを提供する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="a4b49-108">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

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

<span data-ttu-id="a4b49-109">実装でこの登録を配信**NotificationProvider**します。</span><span class="sxs-lookup"><span data-stu-id="a4b49-109">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="a4b49-110">次に、**プラットフォーム**初期化呼び出しがローカルに提供する必要があります**プラットフォーム**プッシュ通知サービスにアクセスできる、アプリを Microsoft Graph の通知からのデータの受信を許可します。サーバー側。</span><span class="sxs-lookup"><span data-stu-id="a4b49-110">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the Microsoft Graph Notifications server-side.</span></span> 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a><span data-ttu-id="a4b49-111">クライアント SDK にプッシュ通知の受信を渡す</span><span class="sxs-lookup"><span data-stu-id="a4b49-111">Pass incoming push notifications to the client SDK</span></span>
<span data-ttu-id="a4b49-112">ネイティブのリスナーを拡張するようになりましたが、サービス クラス ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService)ここでは、このチュートリアルを使用するため Firebase Cloud Messaging) の特殊なオーバー ロードで、`onMessageReceived`メソッド (通知の処理メソッドの場合)。</span><span class="sxs-lookup"><span data-stu-id="a4b49-112">Now, extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this tutorial uses Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

<span data-ttu-id="a4b49-113">により、コンプライアンス、セキュリティ、および潜在的な最適化では、グラフの通知サーバー側から受信した、Google Cloud Messaging の通知には最初に、アプリケーション サーバーによって発行されたすべてのデータが含まれていない、肩のタップ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4b49-113">Due to compliance, security, and potential optimizations, the incoming Google Cloud Messaging notification coming from Graph Notifications server-side could be a shoulder tap, which doesn’t contain any data that is initially published by the app server.</span></span> <span data-ttu-id="a4b49-114">アプリ サーバーによって発行された実際の通知コンテンツの取得は、クライアント側 SDK の Api の背後に表示されません。</span><span class="sxs-lookup"><span data-stu-id="a4b49-114">The retrieval of the actual notification content published by the app server is hidden behind client-side SDK APIs.</span></span> <span data-ttu-id="a4b49-115">このため、SDK は、一貫したプログラミング パターンをアプリのクライアントを常に受信の Google Cloud Messaging のペイロードに渡します SDK を提供できます。</span><span class="sxs-lookup"><span data-stu-id="a4b49-115">Because of this, the SDK can provide a consistent programming pattern in which the app client always passes the incoming Google Cloud Messaging payload to the SDK.</span></span> <span data-ttu-id="a4b49-116">これにより、これは接続されているデバイス プラットフォームのシナリオまたはない (大文字と小文字の Android のネイティブ Google Cloud Messaging チャネルは、アプリのクライアントによって他の目的で使用)、通知であるかどうかを決定する SDK と、この受信シナリオ/機能通知は (グラフの通知、ユーザーの利用状況など) に対応します。</span><span class="sxs-lookup"><span data-stu-id="a4b49-116">This allows the SDK to determine whether this is a notification for Connected Device Platform scenarios or not (in case Android’s native Google Cloud Messaging channel is used by the app client for other purposes), and which scenario/capability this incoming notification is corresponding to (Graph Notifications, User Activity, etc.).</span></span> <span data-ttu-id="a4b49-117">別の種類のシナリオの処理に関する特定のロジックは、その後、アプリのクライアントで実行できます。</span><span class="sxs-lookup"><span data-stu-id="a4b49-117">Specific logics on handling different type of scenarios can then be executed by the app client after that.</span></span> 

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

<span data-ttu-id="a4b49-118">アプリでは、接続されているデバイス プラットフォームから通知を処理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a4b49-118">Your app can now handle notifications from the Connected Devices Platform.</span></span>

