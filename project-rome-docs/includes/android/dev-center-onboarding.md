---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: d8e94884c742015b08d87e83a9384cbb577695c4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907924"
---
## <a name="preliminary-setup-for-push-notifications"></a>プッシュ通知の暫定的なセットアップ

### <a name="register-your-app-for-push-notifications"></a>プッシュ通知をアプリを登録します。

Google にアプリケーションを登録[Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client)をサポートします。 送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。 

登録されると、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。

```Java
notificationRegistration = new ConnectedDevicesNotificationRegistration();
notificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
notificationRegistration.setToken(token);
notificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
notificationRegistration.setAppDisplayName("SampleApp");

mConnectedDevicesPlatform.getNotificationRegistrationManager().registerForAccountAsync(mConnectedDevicesAccount).whenComplete(() -> {
  // Now that notifications are registered, this account can receive replies to commands and incoming commands.
});
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスのアプリを登録します。
Android デバイスへの通信を必要とする場合のアプリを登録する必要があります、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。 これは、上記 MSA と AAD のアプリ登録から別のプロシージャです。  このプロセスの主な目的は、接続されているデバイス プラットフォームによって認識され、同時に、ネイティブのプッシュ通知を使用して通知を送信するプラットフォームを承認するクロス プラットフォーム アプリの id によるプラットフォームの特定のアプリ id にマップするには各モバイル プラットフォームに対応するサービス。 この場合、その、Firebase Cloud Messaging を使用して iOS アプリのエンドポイントへの通信を有効にできます。

Dev Center のダッシュ ボードに移動して、左側にあるナビゲーション ウィンドウで、クロス デバイス エクスペリエンスに移動して次のように示すように、新しいクロス デバイス アプリの構成を選択します。
![デベロッパー センター ダッシュ ボード-クロス デバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターで、オンボード プロセスには、次の手順が必要です。
* サポートされているプラットフォームを選択します: アプリが存在する必要があり、クロス デバイス エクスペリエンスを有効にするプラットフォームを選択します。 Windows、Android、および iOS から選択できます。
![クロス デバイス エクスペリエンス: サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ Id を提供: 各アプリが、プレゼンスがプラットフォームにアプリ Id を提供します。 
![クロス デバイス エクスペリエンス: アプリ Id](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> プラットフォームごと (最大 10 個) の異なる Id を追加することがあります-これは、同じアプリ、または異なる場合でも、同じユーザーを対象としたアプリケーション サーバーによって送信された同じ通知を受信できるようにアプリの複数のバージョンがある場合、します。 
> [!TIP] 
> Android アプリは、これは、プロジェクトを作成したときに、アプリに割り当てたパッケージ名です。 プロジェクトの概要の下、Firebase コンソールで、パッケージ名が見つかりません] [全般]-> [です。
![Firebase コンソール – プロジェクトの概要](../../notifications/media/dev_center_portal/firebase_overview.png)

* 指定するか、MSA または AAD アプリの登録からアプリ Id を選択します。 MSA または AAD アプリの登録に対応するこれらのクライアント Id は、上記の前の MSA/AAD アプリ登録の手順で取得されました。 
![クロス デバイス エクスペリエンス: MSA と AAD アプリの登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* デバイス プラットフォームの機能を活用してそれぞれのエンドポイント、つまり、アプリのクライアントに通知を送信する WNS (Windows UWP) 用、GCM (Android) 用、および APNS (iOS) 用の主要なプラットフォームでネイティブ通知プラットフォームを接続します。 ユーザーを対象とした通知を発行するときに、アプリ サーバーの通知を配信するプラットフォームを有効にするには、これらの通知プラットフォーム用の資格情報を提供します。
![クロス デバイス エクスペリエンス: プッシュの資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Android では、Android のデバイスと通信する前提条件は、クラウド メッセージング サービスを有効にします。 参照してください[設定を Firebase Cloud Messaging クライアント Android でのアプリ](https://firebase.google.com/docs/cloud-messaging/android/client)の詳細。 オンボードを完了すると接続されているデバイス プラットフォームに Windows デベロッパー センターを使用してプッシュの資格情報を提供できます。 
> [!TIP] 
> Firebase クラウド メッセージング Sender ID に対応する必須の送信者 ID と API キーがレガシ サーバー キーに対応します。 Firebase コンソールで見つかります両方プロジェクト->-> 設定 の Cloud Messaging タブで、スクリーン ショットに示すようにします。
![Firebase コンソール – Android のプッシュの資格情報](../../notifications/media/dev_center_portal/firebase_push_creds.png)

* 最後の手順では、アプリではこのドメインの所有権に登録されているアプリのクロス デバイス アプリ id のように機能することを証明する検証プロセスとして機能するクロス デバイス アプリ ドメインを確認します。
![クロス デバイス エクスペリエンス: ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>アプリで受信した通知を処理します。

Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスが検証されるでやり取りされるようにアプリが通知を処理できますを確認します。 

```Java
    ensurePlatformInitialized().thenAccept((ConnectedDevicesPlatform platform) -> {
            ConnectedDevicesProcessNotificationOperation operation = platform.processNotification(data);
        });
```
