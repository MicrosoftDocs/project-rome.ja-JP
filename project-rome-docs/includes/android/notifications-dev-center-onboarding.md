---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: f085486eece082366dddc00d86f0c4959d09a5cf
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907304"
---
### <a name="register-your-app-for-push-notifications"></a>プッシュ通知のためにアプリを登録する

[Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) のサポートのために、アプリケーションを Google に登録します。 受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。

登録したら、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。

```Java
mNotificationRegistration = new ConnectedDevicesNotificationRegistration();
mNotificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
mNotificationRegistration.setToken(token);
mNotificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
mNotificationRegistration.setAppDisplayName("SampleApp");
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Microsoft Windows デベロッパー センターでクロスデバイス エクスペリエンスのためにアプリを登録する

> [!IMPORTANT]
> この手順は、Project Rome の機能を使用して非 Windows デバイスからデータにアクセスする、またはそのデバイスの要求を実行する場合にのみ必要です。 Windows デバイスのみをターゲットにする場合、この手順を完了する必要はありません。

次に示すように、デベロッパー センターのダッシュボードに移動し、左側のナビゲーション ウィンドウから [Cross-Device Experiences] (クロスデバイス エクスペリエンス) に移動して、[configuring a new cross-device app] (新しいクロスデバイス アプリの構成) を選択します。
![デベロッパー センター ダッシュボード – クロスデバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターのオンボーディング プロセスでは、次の手順が必要です。
* サポートされているプラットフォームの選択 – アプリがプレゼンスを持ち、クロスデバイス エクスペリエンスが有効化されるプラットフォームを選択します。 Graph 通知との統合の場合、Windows、Android、iOS から選択できます。
![クロスデバイス エクスペリエンス – サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ ID の指定 – アプリがプレゼンスを持っているプラットフォームごとにアプリ ID を指定します。 Android アプリの場合、これはプロジェクト作成時にアプリに割り当てたパッケージ名です。 パッケージ名は、Firebase コンソールで [Project Overview] (プロジェクトの概要) -> [General] (全般) から確認できます。 プラットフォームごとに (最大 10 個の) 異なる ID を追加できます。これは、同じアプリの複数のバージョン、または複数の異なるアプリがあり、同じユーザーをターゲットにしてアプリ サーバーから送信された同じ通知をこれらのアプリで受信できるようにしたい場合です。 
![クロスデバイス エクスペリエンス – アプリ ID](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* MSA/AAD アプリ登録のアプリ ID を指定または選択します。 MSA または AAD アプリ登録に対応するこれらのクライアント ID は、前述した以前の MSA/AAD アプリ登録手順で取得しました。 
![クロスデバイス エクスペリエンス – MSA および AAD アプリ登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Graph 通知やその他の Connected Devices Platform の機能は、主要プラットフォームの各ネイティブ通知プラットフォーム、具体的には WNS (Windows UWP)、FCM (Android)、および APNS (iOS) を利用してアプリ クライアント エンドポイントに通知を送信します。 ユーザーをターゲットにした通知を発行したときに Graph 通知がアプリ サーバーの通知を配信できるよう、これらの通知プラットフォームの資格情報を指定します。 Android の場合、[Cloud Messaging サービスの有効化](https://firebase.google.com/docs/cloud-messaging/android/client)が、Microsoft Graph 通知を使用するための前提条件です。 また、必要な送信者 ID は Firebase Cloud Messaging の Sender ID に対応し、API キーは Legacy Server Key (従来のサーバー キー) に対応することに注意してください。 スクリーンショットに示すように、どちらも Firebase コンソールの [Project] (プロジェクト) -> [Settings] (設定) の [Cloud Messaging] タブにあります。
![クロスデバイス エクスペリエンス – プッシュ資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* 最後の手順では、クロスデバイス アプリ ドメインを検証します。これには、登録したアプリのクロスデバイス アプリ ID のように機能するこのドメインの所有権をアプリが持っていることを証明する検証プロセスとしての役割があります。
![クロスデバイス エクスペリエンス – ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
