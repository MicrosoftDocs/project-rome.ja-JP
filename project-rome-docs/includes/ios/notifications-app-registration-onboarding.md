---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 771ceeb1-638f-4fba-8c34-953870b5d855
ms.localizationpriority: medium
ms.openlocfilehash: 49538cfee916d048160bdd8cd1e82a7490b979d6
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58908934"
---
### <a name="msa-and-aad-authentication-registration"></a>MSA と AAD 認証の登録

MSA をあり、1 つを使用する実行されていない、上のレジスタ[account.microsoft.com](https://account.microsoft.com/account)します。

次に場合は、ユーザーの認証と identity framework として MSA を使用する必要がありますにアプリを登録 Microsoft 次の手順で、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)(Microsoft があるない場合開発者アカウントを作成する必要がいずれか最初)。 アプリのクライアント ID の文字列を受信する必要があります。場所を忘れないでくださいまたはこれを保存してください。 後でこのグラフの通知のオンボード中に使用されます。 MSA の認証を使用してアプリを Live SDK アプリケーションとして登録されている必要があることに注意してください。
![アプリケーション登録ポータル](../../notifications/media/msa_app_registration/app_registration_portal.png)

職場アカウントまたは学校アカウントの認証と identity framework として AAD を使用するアプリを作成している場合は、経由でアプリを登録する必要があります[Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)クライアント ID を取得するには 
 ![AAD 登録ポータル](../../notifications/media/aad_registration_portal/aad_registration_portal.png)グラフ通知およびその他の接続されているデバイス プラットフォームの機能を使用するために必要ないくつかのアクセス許可がある新しいアプリの登録を作成する場合。 以下をご覧ください。 
![AAD の登録ポータル: 設定 – 必要なアクセス許可](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)
* サインイン ユーザーのアクセス許可を追加します。
![必要なアクセス許可-AAD のユーザー プロファイル](../../notifications/media/aad_registration_portal/permissions_1_user.png)
* デバイス情報のコマンドのサービスのアクセス許可を追加します。
![必要なアクセス許可-デバイス](../../notifications/media/aad_registration_portal/permissions_2_devices.png)
* アクティビティ フィード サービスの Api の下の通知のグラフのアクセス許可を追加します。
![必要なアクセス許可-デバイス](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)
* 最後に、Windows で実行中の UWP アプリを含むクロス プラットフォーム アプリケーションを作成する場合 Windows 通知サービスのアクセス許可を追加することを確認してください。
![必要なアクセス許可-WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)
