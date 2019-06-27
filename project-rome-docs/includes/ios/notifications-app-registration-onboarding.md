---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 771ceeb1-638f-4fba-8c34-953870b5d855
ms.localizationpriority: medium
ms.openlocfilehash: 57a5f2a1e7c40ace95656f9b08994f861b8cc9af
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755709"
---
### <a name="msa-and-aad-authentication-registration"></a>MSA および AAD 認証登録

> [!NOTE]
> Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。

MSA をまだ所有しておらず、使用したい場合は、[account.microsoft.com](https://account.microsoft.com/account) で登録してください。

次に、ユーザー用の認証および ID フレームワークとして MSA を使用している場合、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)の指示に従って、アプリを Microsoft に登録する必要があります (Microsoft 開発者アカウントを所有していない場合は、最初に作成する必要があります)。 アプリのクライアント ID 文字列が届くはずです。必ず、場所を覚えておくか保存しておいてください。 これは後で Graph 通知のオンボーディング中に使用されます。 MSA 認証を使用するアプリは Live SDK アプリケーションとして登録する必要があることに注意してください。
![アプリケーション登録ポータル](../../notifications/media/msa_app_registration/app_registration_portal.png)

職場アカウントまたは学校アカウントの認証および ID フレームワークとして AAD を使用するアプリを作成している場合は、クライアント ID を取得するために [Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)経由でアプリを登録する必要があります。 
 ![AAD 登録ポータル](../../notifications/media/aad_registration_portal/aad_registration_portal.png) 新しいアプリ登録を作成するとき、Graph 通知やその他の Connected Devices Platform の機能を使用するために必要なアクセス許可がいくつかあります。 下記を参照してください。 
![AAD 登録ポータル – 設定 – 必要なアクセス許可](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)
* ユーザーのサインインのアクセス許可を追加します。
![必要なアクセス許可 – AAD ユーザー プロファイル](../../notifications/media/aad_registration_portal/permissions_1_user.png)
* デバイス情報に対するコマンド サービスのアクセス許可を追加します。
![必要なアクセス許可 – デバイス](../../notifications/media/aad_registration_portal/permissions_2_devices.png)
* アクティビティ フィード サービス API の下に Graph 通知のアクセス許可を追加します。
![必要なアクセス許可 – デバイス](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)
* 最後に、Windows で動作する UWP アプリを含むクロスプラットフォーム アプリケーションを作成している場合は、Windows 通知サービスのアクセス許可を必ず追加してください。
![必要なアクセス許可 – WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)
