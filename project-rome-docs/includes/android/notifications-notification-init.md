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
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a>各モバイル プラットフォームのネイティブ プッシュ通知には、接続されているデバイス プラットフォームを関連付けます。 

ようにアプリのクライアントは既に触れましたが、グラフを許可するクライアント側の SDK を各モバイル プラットフォームとデバイスの接続されているプラットフォームの登録プロセス中に使用されているネイティブのプッシュ通知のパイプラインに関する知識を提供する必要がありますアプリケーション サーバーは、Microsoft Graph Api を使用してユーザーを対象とした通知を発行するときのアプリのクライアント エンドポイントは各にファンアウト通知を通知サービス。

上記の手順で、初期化、プラットフォームを`null` *notificationProvider*パラメーター。 ここでは、作成して実装するオブジェクトで渡す必要があります **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** します。 重要なことに注意するは、`getNotificationRegistrationAsync`メソッドを返す必要があります、 **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** インスタンス。 **NotificationRegistration**通知サービスのアクセス トークン (および関連する情報) に接続されているデバイス プラットフォームを提供する責任を負います。

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

実装でこの登録を配信**NotificationProvider**します。 次に、**プラットフォーム**初期化呼び出しがローカルに提供する必要があります**プラットフォーム**プッシュ通知サービスにアクセスできる、アプリを Microsoft Graph の通知からのデータの受信を許可します。サーバー側。 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>クライアント SDK にプッシュ通知の受信を渡す
ネイティブのリスナーを拡張するようになりましたが、サービス クラス ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService)ここでは、このチュートリアルを使用するため Firebase Cloud Messaging) の特殊なオーバー ロードで、`onMessageReceived`メソッド (通知の処理メソッドの場合)。

により、コンプライアンス、セキュリティ、および潜在的な最適化では、グラフの通知サーバー側から受信した、Google Cloud Messaging の通知には最初に、アプリケーション サーバーによって発行されたすべてのデータが含まれていない、肩のタップ可能性があります。 アプリ サーバーによって発行された実際の通知コンテンツの取得は、クライアント側 SDK の Api の背後に表示されません。 このため、SDK は、一貫したプログラミング パターンをアプリのクライアントを常に受信の Google Cloud Messaging のペイロードに渡します SDK を提供できます。 これにより、これは接続されているデバイス プラットフォームのシナリオまたはない (大文字と小文字の Android のネイティブ Google Cloud Messaging チャネルは、アプリのクライアントによって他の目的で使用)、通知であるかどうかを決定する SDK と、この受信シナリオ/機能通知は (グラフの通知、ユーザーの利用状況など) に対応します。 別の種類のシナリオの処理に関する特定のロジックは、その後、アプリのクライアントで実行できます。 

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

アプリでは、接続されているデバイス プラットフォームから通知を処理できるようになりました。

