---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: d8e94884c742015b08d87e83a9384cbb577695c4
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907924"
---
## <a name="preliminary-setup-for-push-notifications"></a>プッシュ通知の準備段階のセットアップ

### <a name="register-your-app-for-push-notifications"></a>プッシュ通知のためにアプリを登録する

[Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) のサポートのために、アプリケーションを Google に登録します。 受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。 

登録したら、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Microsoft Windows デベロッパー センターでクロスデバイス エクスペリエンスのためにアプリを登録する
Android デバイスとの通信が必要な場合、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録する必要があります。 これは、上記の MSA および AAD アプリ登録とは異なる手順です。  このプロセスの主な目的は、プラットフォーム固有のアプリ ID を、Connected Devices Platform によって認識されるクロスプラットフォームのアプリ ID にマップすること、またそれと同時に、プラットフォームにおいて、各モバイル プラットフォームに対応したネイティブのプッシュ通知サービスを使用して通知を送信するのを認可することです。 この場合、それによって、Firebase Cloud Messaging 経由で iOS アプリのエンドポイントと通信できるようになります。

次に示すように、デベロッパー センターのダッシュボードに移動し、左側のナビゲーション ウィンドウから [Cross-Device Experiences] (クロスデバイス エクスペリエンス) に移動して、[configuring a new cross-device app] (新しいクロスデバイス アプリの構成) を選択します。
![デベロッパー センター ダッシュボード – クロスデバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターのオンボーディング プロセスでは、次の手順が必要です。
* サポートされているプラットフォームの選択 – アプリがプレゼンスを持ち、クロスデバイス エクスペリエンスが有効化されるプラットフォームを選択します。 Windows、Android、iOS から選択できます。
![クロスデバイス エクスペリエンス – サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ ID の指定 – アプリがプレゼンスを持っているプラットフォームごとにアプリ ID を指定します。 
![クロスデバイス エクスペリエンス – アプリ ID](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> プラットフォームごとに (最大 10 個の) 異なる ID を追加できます。これは、同じアプリの複数のバージョン、または複数の異なるアプリがあり、同じユーザーをターゲットにしてアプリ サーバーから送信された同じ通知をこれらのアプリで受信できるようにしたい場合です。 
> [!TIP] 
> Android アプリの場合、これはプロジェクト作成時にアプリに割り当てたパッケージ名です。 パッケージ名は、Firebase コンソールで [Project Overview] (プロジェクトの概要) -> [General] (全般) から確認できます。
![Firebase コンソール – プロジェクトの概要](../../notifications/media/dev_center_portal/firebase_overview.png)

* MSA/AAD アプリ登録のアプリ ID を指定または選択します。 MSA または AAD アプリ登録に対応するこれらのクライアント ID は、前述した以前の MSA/AAD アプリ登録手順で取得しました。 
![クロスデバイス エクスペリエンス – MSA および AAD アプリ登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Connected Devices Platform の機能は、主要プラットフォームの各ネイティブ通知プラットフォーム、具体的には WNS (Windows UWP)、GCM (Android)、および APNS (iOS) を利用してアプリ クライアント エンドポイントに通知を送信します。 ユーザーをターゲットにした通知を発行したときにプラットフォームがアプリ サーバーの通知を配信できるよう、これらの通知プラットフォームの資格情報を指定します。
![クロスデバイス エクスペリエンス – プッシュ資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Android の場合、Cloud Messaging サービスの有効化は、Android デバイスと通信するための前提条件です。 詳細については、[Android での Firebase Cloud Messaging クライアント アプリの設定](https://firebase.google.com/docs/cloud-messaging/android/client)に関するページを参照してください。 オンボーディングが完了したら、Windows デベロッパー センターから Connected Device Platform にプッシュ資格情報を提供できるようになります。 
> [!TIP] 
> 必要な送信者 ID は Firebase Cloud Messaging の Sender ID に対応し、API キーは Legacy Server Key (従来のサーバー キー) に対応します。 スクリーンショットに示すように、どちらも Firebase コンソールの [Project] (プロジェクト) -> [Settings] (設定) の [Cloud Messaging] タブにあります。
![Firebase コンソール – Android プッシュ資格情報](../../notifications/media/dev_center_portal/firebase_push_creds.png)

* 最後の手順では、クロスデバイス アプリ ドメインを検証します。これには、登録したアプリのクロスデバイス アプリ ID のように機能するこのドメインの所有権をアプリが持っていることを証明する検証プロセスとしての役割があります。
![クロスデバイス エクスペリエンス – ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>アプリで受信した通知の処理

Microsoft Windows デベロッパー センター内でクロスデバイス エクスペリエンスが検証されたら、通知を受信したときにアプリがそれを処理できることを確認します。 

```Java
    ensurePlatformInitialized().thenAccept((ConnectedDevicesPlatform platform) -> {
            ConnectedDevicesProcessNotificationOperation operation = platform.processNotification(data);
        });
```
