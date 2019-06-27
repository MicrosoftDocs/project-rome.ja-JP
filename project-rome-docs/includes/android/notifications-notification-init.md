---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 27ff12ef8b0773f1bd0e1960c285012f7e62fdc9
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801798"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a>Connected Devices Platform を各モバイル プラットフォームのネイティブのプッシュ通知に関連付けます。 

既に触れたように、アプリ クライアントは、登録プロセスの間、各モバイル プラットフォームで使用されているネイティブのプッシュ通知パイプラインに関する情報を、クライアント側 SDK と Connected Devices Platform に提供する必要があります。これは、ユーザーをターゲットにした通知をアプリ サーバーが Microsoft Graph API を使って発行したときに、Graph の通知サービスが個々のアプリ クライアント エンドポイントに通知を拡散できるようにするためです。

上記の手順では、`null` *notificationProvider* パラメーターを使用してプラットフォームを初期化しました。 ここでは、 **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** を実装するオブジェクトを作成して渡す必要があります。 主な注意点は、`getNotificationRegistrationAsync` メソッドが **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** インスタンスを返す必要があることです。 **NotificationRegistration** の役割は、通知サービス用のアクセス トークン (および関連情報) を Connected Devices Platform に提供することです。

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

**NotificationProvider** の実装でこの登録を配信します。 次に、**Platform** の初期化呼び出しで、プッシュ通知サービスへのアクセスをローカルの **Platform** に提供して、サーバー側の Microsoft Graph 通知からアプリがデータを受信できるようにする必要があります。 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>着信プッシュ通知をクライアント SDK に渡す
ここで、`onMessageReceived` メソッド (通知処理メソッド) の特殊なオーバーロードによって、ネイティブ リスナー サービス クラス (この場合は [FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService)。このチュートリアルでは Firebase Cloud Messaging を使用するため) を拡張することだけです。

コンプライアンス、セキュリティ、潜在的な最適化のため、サーバー側の Graph 通知から受信する Google Cloud Messaging 通知は、アプリ サーバーによって最初に公開される一切のデータを含まないショルダー タップである可能性があります。 アプリ サーバーによって発行された実際の通知内容の取得は、クライアント側の SDK API の背後に隠されています。 このため SDK は、アプリ クライアントが常に、受信した Google Cloud Messaging ペイロードを SDK に渡すという一貫したプログラミング パターンを提供できます。 これによって SDK は、(Android のネイティブ Google Cloud Messaging チャネルが他の目的のためにアプリ クライアントによって使用されている場合に) これが Connected Device Platform のシナリオ向けの通知であるかどうか、また、この受信した通知はどのシナリオや機能 (Graph 通知、ユーザー アクティビティ、その他) に対応しているのかを判断できます。 その後、さまざまな種類のシナリオの処理に関する特定のロジックをアプリ クライアントによって実行できます。 

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

アプリで Connected Devices Platform からの通知を処理できるようになりました。

