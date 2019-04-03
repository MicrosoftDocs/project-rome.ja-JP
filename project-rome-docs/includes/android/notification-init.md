---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909454"
---
## <a name="preliminary-setup-for-push-notifications"></a>プッシュ通知の暫定的なセットアップ

### <a name="register-your-app-for-push-notifications"></a>プッシュ通知をアプリを登録します。

通知のサポートを Google にアプリケーションを登録します。 送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a>デバイス間の接続されているデバイス プラットフォーム アクセス用アプリを登録します。

次に、アプリを登録、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。 これは、上記の準備手順で説明した、Windows デベロッパー センターの登録から別のプロシージャです。 これには、ネイティブのプッシュ通知サービスを使用して通知を送信する接続されているデバイス プラットフォームが認証されます。 デベロッパー センターで、オンボード プロセスが必要です。
* アプリのクライアント id。
* Google Cloud Messaging のキー。 これは必要です (デバイスがロックされているかスリープ状態にあります) 上のアプリにデータとコマンドを配信するにはプッシュ通知の形式でします。 

### <a name="configure-your-app-to-be-notification-compatible"></a>アプリ通知互換性を構成します

開発者向けダッシュ ボードのワークフローが完了した後には、プッシュ通知を受信できるように、アプリの実際のコードを変更する必要があります。 参照してください[設定を Firebase Cloud Messaging クライアント Android でのアプリ](https://firebase.google.com/docs/cloud-messaging/android/client)これを行う方法がない場合。

### <a name="associate-the-notification-service-with-the-local-platform"></a>ローカルのプラットフォーム通知サービスを関連付ける

最後に、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。 上記の手順で、初期化、プラットフォームを`null` *notificationProvider*パラメーター。 ここでは、作成して実装するオブジェクトで渡す必要があります **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** します。 重要なことに注意するは、`getNotificationRegistrationAsync`メソッドを返す必要があります、 **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** インスタンス。 **NotificationRegistration**通知サービスのアクセス トークン (および関連する情報) に接続されているデバイス プラットフォームを提供する責任を負います。


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

実装でこの登録を配信**NotificationProvider**します。 次に、**プラットフォーム**初期化呼び出しがローカルに提供する必要があります**プラットフォーム**プッシュ通知サービスにアクセスできる、サーバー側の接続されたデバイスからデータを受信するアプリを許可します。プラットフォームの起動要求とその他のデバイスからアプリ サービスのメッセージを中継します。 

すべて行う必要があるようになりましたが、ネイティブのリスナーを拡張サービス クラス ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService)ここでは、このガイドで使用されるため、Firebase Cloud Messaging) の特殊なオーバー ロードで、 `onMessageReceived` (メソッド通知の処理方法の場合)。

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

アプリは、接続されているデバイス プラットフォームから通知を処理することがようになりました。
