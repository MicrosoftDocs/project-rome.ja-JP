---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: b03420e0229bed45fba5a079b955d62165a6b642
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907604"
---
## <a name="preliminary-setup-for-push-notifications"></a>プッシュ通知の準備段階のセットアップ

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
iOS デバイスとの通信が必要な場合、Microsoft Windows デベロッパー センターで登録する必要があります。  次に、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録する必要があります。 これは、上記の MSA および AAD アプリ登録とは異なる手順です。 このプロセスの主な目的は、プラットフォーム固有のアプリ ID を、Connected Devices Platform によって認識されるクロスプラットフォームのアプリ ID にマップすること、またそれと同時に、プラットフォームにおいて、各モバイル プラットフォームに対応したネイティブのプッシュ通知サービスを使用して通知を送信するのを認可することです。 この場合、それによって、APNs (Apple Push Notification Service) 経由で iOS アプリのエンドポイントと通信できるようになります。 デベロッパー センターのダッシュボードに移動し、左側のナビゲーション ウィンドウから [Cross-Device Experiences] (クロスデバイス エクスペリエンス) に移動して、[configuring a new cross-device app] (新しいクロスデバイス アプリの構成) を選択します。
![デベロッパー センター ダッシュボード – クロスデバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターのオンボーディング プロセスでは、次の手順が必要です。
* サポートされているプラットフォームの選択 – アプリがプレゼンスを持ち、クロスデバイス エクスペリエンスが有効化されるプラットフォームを選択します。 Windows、Android、iOS から選択できます。
![クロスデバイス エクスペリエンス – サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ ID の指定 – アプリがプレゼンスを持っているプラットフォームごとにアプリ ID を指定します。
![クロスデバイス エクスペリエンス – アプリ ID](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> プラットフォームごとに (最大 10 個の) 異なる ID を追加できます。これは、同じアプリの複数のバージョン、または複数の異なるアプリがあり、同じユーザーをターゲットにしてアプリ サーバーから送信された同じ通知をこれらのアプリで受信できるようにしたい場合です。 
> [!TIP] 
> iOS アプリの場合、これはプロジェクト作成時にアプリに割り当てたパッケージ名です。 

* MSA/AAD アプリ登録のアプリ ID を指定または選択します。 MSA または AAD アプリ登録に対応するこれらのクライアント ID は、前述した以前の MSA/AAD アプリ登録手順で取得しました。
![クロスデバイス エクスペリエンス – MSA および AAD アプリ登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)
* Connected Devices Platform の機能は、主要プラットフォームの各ネイティブ通知プラットフォーム、具体的には WNS (Windows UWP)、GCM (Android)、および APNs (iOS) を利用してアプリ クライアント エンドポイントに通知を送信します。 ユーザーをターゲットにした通知を発行したときにプラットフォームがアプリ サーバーの通知を配信できるよう、これらの通知プラットフォームの資格情報を指定します。 
![クロスデバイス エクスペリエンス – プッシュ資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> iOS の場合、APNs の有効化は iOS デバイスと通信するための前提条件です。 詳細については、[APNs の概要](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1)に関する記事を参照してください。 オンボーディングが完了したら、Windows デベロッパー センターから Connected Device Platform にプッシュ資格情報を提供できるようになります。 
* 最後の手順では、クロスデバイス アプリ ドメインを検証します。これには、登録したアプリのクロスデバイス アプリ ID のように機能するこのドメインの所有権をアプリが持っていることを証明する検証プロセスとしての役割があります。
![クロスデバイス エクスペリエンス – ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>アプリで受信した通知の処理

Microsoft Windows デベロッパー センター内でクロスデバイス エクスペリエンスが検証されたら、通知を受信したときにアプリがそれを処理できることを確認します。 

```ObjectiveC
`MCDConnectedDevicesProcessNotificationOperation* processOperation = [_platformManager.platform processNotification:notificationInfo];`
```