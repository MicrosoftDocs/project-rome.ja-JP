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
## <a name="preliminary-setup-for-push-notifications"></a>プッシュ通知の準備段階のセットアップ

### <a name="register-your-app-for-push-notifications"></a>プッシュ通知のためにアプリを登録する

通知のサポートのためにアプリケーションを Google に登録します。 受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a>Connected Devices Platform へのクロスデバイス アクセスのためにアプリを登録する

次に、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録します。 これは、先の準備手順で説明した Windows デベロッパー センターへの登録とは異なる手続きです。 これは、Connected Devices Platform がネイティブのプッシュ通知サービスを使用して通知を送信することを承認します。 デベロッパーセンターのオンボーディング プロセスに必要なものは次のとおりです。
* アプリのクライアント ID。
* Google Cloud Messaging キー。 これは、プッシュ通知の形式でデータやコマンドを (ロックまたはスリープ状態になる可能性があるデバイス上の) アプリに配信するために必要です。 

### <a name="configure-your-app-to-be-notification-compatible"></a>通知互換性のためにアプリを構成する

デベロッパー ダッシュボードでワークフローを完了したら、アプリの実際のコードを変更して、アプリでプッシュ通知を受信可能にする必要があります。 この方法がわからない場合は、[Android での Firebase Cloud Messaging クライアント アプリの設定](https://firebase.google.com/docs/cloud-messaging/android/client)に関するページを参照してください。

### <a name="associate-the-notification-service-with-the-local-platform"></a>通知サービスをローカルのプラットフォームに関連付ける

最後に、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。 上記の手順では、`null` *notificationProvider* パラメーターを使用してプラットフォームを初期化しました。 ここでは、 **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** を実装するオブジェクトを作成して渡す必要があります。 主な注意点は、`getNotificationRegistrationAsync` メソッドが **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** インスタンスを返す必要があることです。 **NotificationRegistration** の役割は、通知サービス用のアクセス トークン (および関連情報) を Connected Devices Platform に提供することです。


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

**NotificationProvider** の実装でこの登録を配信します。 その後は、**Platform** の初期化呼び出しによって、プッシュ通知サービスへのアクセスがローカルの **Platform** に提供され、アプリがサーバー側の Connected Devices Platform からデータを受信できるようになります。このプラットフォームは、他のデバイスからの起動要求およびアプリ サービス メッセージを中継します。 

ここで行う必要があるのは、`onMessageReceived` メソッド (通知処理メソッド) の特殊なオーバーロードによって、ネイティブ リスナー サービス クラス (この場合は [FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService)。このガイドでは Firebase Cloud Messaging を使用するため) を拡張することだけです。

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

アプリで Connected Devices Platform からの通知を処理できるようになりました。
