---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "58909294"
---
### <a name="register-your-app-for-push-notifications"></a>プッシュ通知のためにアプリを登録する

[Apple Push Notification](https://developer.apple.com/notifications/) のサポートのためにアプリケーションを Apple に登録します。 受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。

登録したら、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。

```ObjectiveC
self.notificationRegistration = [[MCDConnectedDevicesNotificationRegistration alloc] init];
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        self.notificationRegistration.type = MCDNotificationTypeAPN;
    }
    else
    {
        self.notificationRegistration.type = MCDNotificationTypePolling;
    }
    self.notificationRegistration.appId = [[NSBundle mainBundle] bundleIdentifier];
    self.notificationRegistration.appDisplayName = (NSString*)[[NSBundle mainBundle] objectForInfoDictionaryKey:@"CFBundleDisplayName"];
    self.notificationRegistration.token = deviceToken;
    self.isRegisteredWithToken = YES;
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Microsoft Windows デベロッパー センターでクロスデバイス エクスペリエンスのためにアプリを登録する

> [!WARNING]
> この手順は、Project Rome の機能を使用して非 Windows デバイスからデータにアクセスする、またはそのデバイスの要求を実行する場合にのみ必要です。 Windows デバイスのみをターゲットにする場合、この手順を完了する必要はありません。

[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録します。 これは、上記の MSA および AAD アプリ登録とは異なる手順です。 このプロセスの主な目的は、プラットフォーム固有のアプリ ID を、Connected Devices Platform によって認識されるクロスプラットフォームのアプリ ID にマップすることです。 この手順により、アプリで利用するモバイル プラットフォームに対応するネイティブのプッシュ通知サービスを使用した通知の送信も有効化されます。 iOS の場合、それによって、APNS (Apple Push Notification Service) 経由で iOS アプリのエンドポイントに通知を送信できるようになります。

デベロッパー センターのダッシュボードに移動し、左側のナビゲーション ウィンドウから [Cross-Device Experiences] (クロスデバイス エクスペリエンス) に移動して、[configuring a new cross-device app] (新しいクロスデバイス アプリの構成) を選択します。
![デベロッパー センター ダッシュボード – クロスデバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターのオンボーディング プロセスでは、次の手順が必要です。

* サポートされているプラットフォームの選択 – アプリがプレゼンスを持ち、クロスデバイス エクスペリエンスが有効化されるプラットフォームを選択します。 Graph 通知との統合の場合、使用しているプラットフォームに応じて Windows、Android、iOS から選択できます。 ![クロスデバイス エクスペリエンス – サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ ID の指定 – 使用しているプラットフォームごとにアプリ ID を指定します。 iOS アプリの場合、これはプロジェクト作成時にアプリに割り当てたパッケージ名です。 プラットフォームごとに (最大 10 個の) 異なる ID を追加できることに注意してください。これは、同じアプリの複数のバージョン、または複数の異なるアプリがあり、同じユーザーをターゲットにしてアプリ サーバーから送信された同じ通知をこれらのアプリで受信できるようにしたい場合です。 ![クロスデバイス エクスペリエンス – アプリ ID](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* 前述した以前の MSA/AAD アプリ登録手順で取得した、MSA/AAD アプリ登録のアプリ ID を指定または選択します。 ![クロスデバイス エクスペリエンス – MSA および AAD アプリ登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* ユーザーをターゲットにした通知を発行したときにアプリ サーバーから通知が配信されるよう、アプリで使用するネイティブ通知プラットフォーム (Windows の WNS、Android の FCM、iOS の APNS) の資格情報を入力します。 ![クロスデバイス エクスペリエンス – プッシュ資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* 最後に、クロスデバイス アプリ ドメインを検証して、アプリがドメインの所有権を持っていること、また、それをアプリのクロスデバイス ID として使用できることを確認します。 ![クロスデバイス エクスペリエンス – ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
