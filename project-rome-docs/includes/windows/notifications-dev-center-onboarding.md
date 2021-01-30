---
ms.openlocfilehash: b7ef1272e292e5f6bdc2ffebe85609703c00bbd9
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98947084"
---
### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Microsoft Windows デベロッパー センターでクロスデバイス エクスペリエンスのためにアプリを登録する
次に、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録する必要があります。 これは、上記の手順で説明した MSA および AAD アプリ登録とは異なる手続きです。 このプロセスの主な目的は、プラットフォーム固有のアプリ ID を、Connected Devices Platform によって認識されるクロスプラットフォームのアプリ ID にマップすること、またそれと同時に、Microsoft Graph 通知において、各 OS プラットフォームに対応したネイティブのプッシュ通知サービスを使用して通知を送信するのを認可することです。 この場合は、Graph 通知が WNS (Windows 通知サービス) 経由で Windows UWP アプリ エンドポイントに通知を送信できるようにします。 次に示すように、デベロッパー センターのダッシュボードに移動し、左側のナビゲーション ウィンドウから [Cross-Device Experiences] (クロスデバイス エクスペリエンス) に移動して、[configuring a new cross-device app] (新しいクロスデバイス アプリの構成) を選択します。
![デベロッパー センター ダッシュボード – クロスデバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターのオンボーディング プロセスでは、次の手順が必要です。
* サポートされているプラットフォームの選択 – アプリがプレゼンスを持ち、クロスデバイス エクスペリエンスが有効化されるプラットフォームを選択します。 Graph 通知との統合の場合、Windows、Android、iOS から選択できます。 次のように表示されます。
![クロスデバイス エクスペリエンス – サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ ID の指定 – アプリがプレゼンスを持っているプラットフォームごとにアプリ ID を指定します。 次のように表示されます。
![クロスデバイス エクスペリエンス – アプリ ID](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> プラットフォームごとに (最大 10 個の) 異なる ID を追加できます。これは、同じアプリの複数のバージョン、または複数の異なるアプリがあり、同じユーザーをターゲットにしてアプリ サーバーから送信された同じ通知をこれらのアプリで受信できるようにしたい場合です。 

* MSA/AAD アプリ登録のアプリ ID を指定または選択します。 MSA または AAD アプリ登録に対応するこれらのクライアント ID は、前述した以前の MSA/AAD アプリ登録手順で取得しました。 次のように表示されます。 
![クロスデバイス エクスペリエンス – MSA および AAD アプリ登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)
* Graph 通知やその他の Connected Devices Platform の機能は、主要プラットフォームの各ネイティブ通知プラットフォーム、具体的には WNS (Windows UWP)、GCM (Android)、および APNS (iOS) を利用してアプリ クライアント エンドポイントに通知を送信します。 ユーザーをターゲットにした通知を発行したときに Graph 通知がアプリ サーバーの通知を配信できるよう、これらの通知プラットフォームの資格情報を指定します。 次のように表示されます。 
![クロスデバイス エクスペリエンス – プッシュ資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Windows UWP アプリの場合、WNS プッシュ通知の有効化は、Microsoft Graph 通知を使用するための前提条件です。 詳細については、[WNS の概要](/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)に関する記事を参照してください。 オンボーディングが完了したら、Windows デベロッパー センターから Connected Device Platform にプッシュ資格情報を提供できるようになります。 
* 最後の手順では、クロスデバイス アプリ ドメインを検証します。これには、登録したアプリのクロスデバイス アプリ ID のように機能するこのドメインの所有権をアプリが持っていることを証明する検証プロセスとしての役割があります。 次のように表示されます。  
![クロスデバイス エクスペリエンス – ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png) これで、オンボーディングの準備は万端です! 次のセクションに進んでください。