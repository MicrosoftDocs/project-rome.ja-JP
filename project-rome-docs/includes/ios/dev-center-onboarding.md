---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: b03420e0229bed45fba5a079b955d62165a6b642
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907604"
---
## <a name="preliminary-setup-for-push-notifications"></a>プッシュ通知の暫定的なセットアップ

### <a name="register-your-app-for-push-notifications"></a>プッシュ通知をアプリを登録します。

アプリケーションを Apple の登録[Apple Push Notification](https://developer.apple.com/notifications/)をサポートします。 送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。 

登録されると、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスのアプリを登録します。
IOS デバイスへの通信が必要な場合は、Microsoft Windows デベロッパー センターに登録する必要があります。  次に、アプリケーションを登録する必要があります、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。 これは、上記 MSA と AAD のアプリ登録から別のプロシージャです。 このプロセスの主な目的は、接続されているデバイス プラットフォームによって認識され、同時に、ネイティブのプッシュ通知を使用して通知を送信するプラットフォームを承認するクロス プラットフォーム アプリの id によるプラットフォームの特定のアプリ id にマップするには各モバイル プラットフォームに対応するサービス。 この場合、APNs – Apple Push Notification Service を使用して iOS アプリのエンドポイントへの通信ができます。 Dev Center のダッシュ ボードに移動して、左側にあるナビゲーション ウィンドウで、クロス デバイス エクスペリエンスに移動して新しいクロス デバイス アプリの構成を選択します。
![デベロッパー センター ダッシュ ボード-クロス デバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターで、オンボード プロセスには、次の手順が必要です。
* サポートされているプラットフォームを選択します: アプリが存在する必要があり、クロス デバイス エクスペリエンスを有効にするプラットフォームを選択します。 Windows、Android、および iOS から選択できます。
![クロス デバイス エクスペリエンス: サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ Id を提供: 各アプリが、プレゼンスがプラットフォームにアプリ Id を提供します。
![クロス デバイス エクスペリエンス: アプリ Id](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> プラットフォームごと (最大 10 個) の異なる Id を追加することがあります-これは、同じアプリ、または異なる場合でも、同じユーザーを対象としたアプリケーション サーバーによって送信された同じ通知を受信できるようにアプリの複数のバージョンがある場合、します。 
> [!TIP] 
> IOS アプリの場合は、これは、プロジェクトを作成したときに、アプリに割り当てたパッケージ名です。 

* 指定するか、MSA または AAD アプリの登録からアプリ Id を選択します。 MSA または AAD アプリの登録に対応するこれらのクライアント Id は、上記の前の MSA/AAD アプリ登録の手順で取得されました。
![クロス デバイス エクスペリエンス: MSA と AAD アプリの登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)
* デバイス プラットフォームの機能活用して各エンドポイント、つまり、WNS (Windows UWP) 用、GCM (Android) 用および APNs (iOS) のアプリのクライアントに通知を送信する主要なプラットフォームでネイティブ通知プラットフォームの接続されています。 ユーザーを対象とした通知を発行するときに、アプリ サーバーの通知を配信するプラットフォームを有効にするには、これらの通知プラットフォーム用の資格情報を提供します。 
![クロス デバイス エクスペリエンス: プッシュの資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> IOS、APNs の有効化は iOS デバイスへの通信をするうえで必須です。 参照してください[APNs の概要](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1)の詳細。 オンボードを完了すると接続されているデバイス プラットフォームに Windows デベロッパー センターを使用してプッシュの資格情報を提供できます。 
* 最後の手順では、アプリではこのドメインの所有権に登録されているアプリのクロス デバイス アプリ id のように機能することを証明する検証プロセスとして機能するクロス デバイス アプリ ドメインを確認します。
![クロス デバイス エクスペリエンス: ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>アプリで受信した通知を処理します。

Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスが検証されるでやり取りされるようにアプリが通知を処理できますを確認します。 

```ObjectiveC
`MCDConnectedDevicesProcessNotificationOperation* processOperation = [_platformManager.platform processNotification:notificationInfo];`
```