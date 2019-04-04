---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: f085486eece082366dddc00d86f0c4959d09a5cf
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907304"
---
### <a name="register-your-app-for-push-notifications"></a>プッシュ通知をアプリを登録します。

Google にアプリケーションを登録[Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client)をサポートします。 送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。

登録されると、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。

```Java
mNotificationRegistration = new ConnectedDevicesNotificationRegistration();
mNotificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
mNotificationRegistration.setToken(token);
mNotificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
mNotificationRegistration.setAppDisplayName("SampleApp");
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスのアプリを登録します。

> [!IMPORTANT]
> この手順はのみからデータにアクセスしたり、非 Windows デバイスの要求を作成するプロジェクト ローマ機能を使用するかどうかに必要です。 Windows デバイスのみを対象に場合、この手順を完了する必要はありません。

Dev Center のダッシュ ボードに移動して、左側にあるナビゲーション ウィンドウで、クロス デバイス エクスペリエンスに移動して次のように示すように、新しいクロス デバイス アプリの構成を選択します。
![デベロッパー センター ダッシュ ボード-クロス デバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターで、オンボード プロセスには、次の手順が必要です。
* サポートされているプラットフォームを選択します: アプリが存在する必要があり、クロス デバイス エクスペリエンスを有効にするプラットフォームを選択します。 グラフの通知の統合の場合は、Windows、Android、および iOS から選択できます。
![クロス デバイス エクスペリエンス: サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ Id を提供: 各アプリが、プレゼンスがプラットフォームにアプリ Id を提供します。 Android アプリは、これは、プロジェクトを作成したときに、アプリに割り当てたパッケージ名です。 プロジェクトの概要の下、Firebase コンソールで、パッケージ名が見つかりません] [全般]-> [です。 プラットフォームごと (最大 10 個) の異なる Id を追加することがあります-これは、同じアプリ、または異なる場合でも、同じユーザーを対象としたアプリケーション サーバーによって送信された同じ通知を受信できるようにアプリの複数のバージョンがある場合、します。 
![クロス デバイス エクスペリエンス: アプリ Id](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* 指定するか、MSA または AAD アプリの登録からアプリ Id を選択します。 MSA または AAD アプリの登録に対応するこれらのクライアント Id は、上記の前の MSA/AAD アプリ登録の手順で取得されました。 
![クロス デバイス エクスペリエンス: MSA と AAD アプリの登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* グラフの通知およびその他のデバイス プラットフォームの接続されている機能の各クライアントのエンドポイント、つまり、アプリに通知を送信する WNS (Windows UWP) 用、FCM (Android) 用、および APNS (iOS) 用の主要なプラットフォームでネイティブ通知プラットフォームを活用します. これらの通知プラットフォームにユーザーを対象とした通知を発行するときに、アプリ サーバーの通知を配信するグラフの通知を有効にするための資格情報を提供します。 Android では、[クラウド メッセージング サービスを有効にする](https://firebase.google.com/docs/cloud-messaging/android/client)は Microsoft Graph の通知を使用する前提条件です。 また、注意が必要な送信者 ID が、Firebase Cloud Messaging Sender ID と API キーに対応するは、レガシ サーバー キーに対応します。 Firebase コンソールで見つかります両方プロジェクト->-> 設定 の Cloud Messaging タブで、スクリーン ショットに示すようにします。
![クロス デバイス エクスペリエンス: プッシュの資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* 最後の手順では、アプリではこのドメインの所有権に登録されているアプリのクロス デバイス アプリ id のように機能することを証明する検証プロセスとして機能するクロス デバイス アプリ ドメインを確認します。
![クロス デバイス エクスペリエンス: ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
