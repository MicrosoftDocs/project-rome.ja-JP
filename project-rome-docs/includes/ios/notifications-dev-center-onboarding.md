---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58909294"
---
### <a name="register-your-app-for-push-notifications"></a>プッシュ通知をアプリを登録します。

アプリケーションを Apple の登録[Apple Push Notification](https://developer.apple.com/notifications/)をサポートします。 送信側を必要に応じて、後で受信した ID とサーバーのキーをメモしてください。

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

> [!WARNING]
> この手順はのみからデータにアクセスしたり、非 Windows デバイスの要求を作成するプロジェクト ローマ機能を使用するかどうかに必要です。 Windows デバイスのみを対象に場合、この手順を完了する必要はありません。

アプリケーションを登録、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。 これは、上記 MSA と AAD のアプリ登録から別のプロシージャです。 このプロセスの主な目的は、接続されているデバイス プラットフォームによって認識されるクロス プラットフォーム アプリの id によるプラットフォームの特定のアプリ id にマップします。 この手順は、アプリを利用するモバイル プラットフォームに対応するネイティブのプッシュ通知サービスを使用して通知の送信も有効になります。 Ios の APNS – Apple Push Notification Service を使用して iOS アプリのエンドポイントに送信される通知できます。

Dev Center のダッシュ ボードに移動して、左側にあるナビゲーション ウィンドウで、クロス デバイス エクスペリエンスに移動して新しいクロス デバイス アプリの構成を選択します。
![デベロッパー センター ダッシュ ボード-クロス デバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターで、オンボード プロセスには、次の手順が必要です。

* サポートされているプラットフォームを選択します: アプリが存在する必要があり、クロス デバイス エクスペリエンスを有効にするプラットフォームを選択します。 グラフの通知の統合の場合は、Windows、Android、iOS、お使いのプラットフォームに応じてから選択できます。 ![クロス デバイス エクスペリエンス: サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ Id を提供: を使用する各プラットフォームのアプリ Id を提供します。 IOS アプリの場合は、これは、プロジェクトを作成したときに、アプリに割り当てたパッケージ名です。 プラットフォームごと (最大 10 個) の異なる Id を追加することに注意してください: これは、同じアプリ、または異なる場合でも、同じユーザーを対象としたアプリケーション サーバーによって送信された同じ通知を受信できるようにアプリの複数のバージョンがある場合。 ![クロス デバイス エクスペリエンス: アプリ Id](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* 指定するか、前 MSA/AAD アプリ登録の手順で取得した MSA または AAD アプリの登録からのアプリ Id を選択します。 ![クロス デバイス エクスペリエンス: MSA と AAD アプリの登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* ユーザーを対象とした通知を発行するときに、アプリ サーバーからの通知の配信を有効にするアプリ (WNS の Windows、android では、FCM や iOS の APNS) に関連するネイティブ通知プラットフォームの資格情報を指定します。 ![クロス デバイス エクスペリエンス: プッシュの資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* 最後に、アプリがドメインの所有権ととして使用できますが、クロス デバイス id、アプリのことを確認するためのクロス デバイス アプリ ドメインを確認します。 ![クロス デバイス エクスペリエンス: ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
