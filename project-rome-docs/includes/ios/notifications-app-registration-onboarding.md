---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 771ceeb1-638f-4fba-8c34-953870b5d855
ms.localizationpriority: medium
ms.openlocfilehash: 57a5f2a1e7c40ace95656f9b08994f861b8cc9af
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755709"
---
### <a name="msa-and-aad-authentication-registration"></a><span data-ttu-id="a503b-103">MSA と AAD 認証の登録</span><span class="sxs-lookup"><span data-stu-id="a503b-103">MSA and AAD Authentication Registration</span></span>

> [!NOTE]
> <span data-ttu-id="a503b-104">デバイスの Relay Api では、azure Active Directory (AAD) アカウントはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a503b-104">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="a503b-105">MSA をあり、1 つを使用する実行されていない、上のレジスタ[account.microsoft.com](https://account.microsoft.com/account)します。</span><span class="sxs-lookup"><span data-stu-id="a503b-105">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="a503b-106">次に場合は、ユーザーの認証と identity framework として MSA を使用する必要がありますにアプリを登録 Microsoft 次の手順で、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)(Microsoft があるない場合開発者アカウントを作成する必要がいずれか最初)。</span><span class="sxs-lookup"><span data-stu-id="a503b-106">Next, if you are using MSA as the authentication and identity framework for your users, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="a503b-107">アプリのクライアント ID の文字列を受信する必要があります。場所を忘れないでくださいまたはこれを保存してください。</span><span class="sxs-lookup"><span data-stu-id="a503b-107">You should receive a client ID string for your app; make sure to remember the location or save this.</span></span> <span data-ttu-id="a503b-108">後でこのグラフの通知のオンボード中に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a503b-108">Later this will be used during Graph Notifications onboarding.</span></span> <span data-ttu-id="a503b-109">MSA の認証を使用してアプリを Live SDK アプリケーションとして登録されている必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a503b-109">Note that an app using MSA authentication needs to be registered as a Live SDK application.</span></span>
<span data-ttu-id="a503b-110">![アプリケーション登録ポータル](../../notifications/media/msa_app_registration/app_registration_portal.png)</span><span class="sxs-lookup"><span data-stu-id="a503b-110">![Application Registration Portal](../../notifications/media/msa_app_registration/app_registration_portal.png)</span></span>

<span data-ttu-id="a503b-111">職場アカウントまたは学校アカウントの認証と identity framework として AAD を使用するアプリを作成している場合は、経由でアプリを登録する必要があります[Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)クライアント ID を取得するには</span><span class="sxs-lookup"><span data-stu-id="a503b-111">If you're writing an app that uses AAD as work account or school account authentication and identity framework, you must register your app via [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) in order to get the client ID.</span></span> 
 <span data-ttu-id="a503b-112">![AAD 登録ポータル](../../notifications/media/aad_registration_portal/aad_registration_portal.png)グラフ通知およびその他の接続されているデバイス プラットフォームの機能を使用するために必要ないくつかのアクセス許可がある新しいアプリの登録を作成する場合。</span><span class="sxs-lookup"><span data-stu-id="a503b-112">![AAD Registration Portal](../../notifications/media/aad_registration_portal/aad_registration_portal.png) When creating a new app registration, there are a few permissions required in order to use Graph Notifications and other connected device platform capabilities.</span></span> <span data-ttu-id="a503b-113">以下をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a503b-113">Please see below.</span></span> 
<span data-ttu-id="a503b-114">![AAD の登録ポータル: 設定 – 必要なアクセス許可](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)</span><span class="sxs-lookup"><span data-stu-id="a503b-114">![AAD Registration Portal – Setting – Required Permissions](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)</span></span>
* <span data-ttu-id="a503b-115">サインイン ユーザーのアクセス許可を追加します。</span><span class="sxs-lookup"><span data-stu-id="a503b-115">Add user sign-in permission.</span></span>
<span data-ttu-id="a503b-116">![必要なアクセス許可-AAD のユーザー プロファイル](../../notifications/media/aad_registration_portal/permissions_1_user.png)</span><span class="sxs-lookup"><span data-stu-id="a503b-116">![Required Permissions – AAD User Profile](../../notifications/media/aad_registration_portal/permissions_1_user.png)</span></span>
* <span data-ttu-id="a503b-117">デバイス情報のコマンドのサービスのアクセス許可を追加します。</span><span class="sxs-lookup"><span data-stu-id="a503b-117">Add Command Service permissions for device information.</span></span>
<span data-ttu-id="a503b-118">![必要なアクセス許可-デバイス](../../notifications/media/aad_registration_portal/permissions_2_devices.png)</span><span class="sxs-lookup"><span data-stu-id="a503b-118">![Required Permissions – Devices](../../notifications/media/aad_registration_portal/permissions_2_devices.png)</span></span>
* <span data-ttu-id="a503b-119">アクティビティ フィード サービスの Api の下の通知のグラフのアクセス許可を追加します。</span><span class="sxs-lookup"><span data-stu-id="a503b-119">Add Graph Notifications permission under Activity Feed Service APIs.</span></span>
<span data-ttu-id="a503b-120">![必要なアクセス許可-デバイス](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)</span><span class="sxs-lookup"><span data-stu-id="a503b-120">![Required Permissions – Devices](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)</span></span>
* <span data-ttu-id="a503b-121">最後に、Windows で実行中の UWP アプリを含むクロス プラットフォーム アプリケーションを作成する場合 Windows 通知サービスのアクセス許可を追加することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a503b-121">At the end, if you are writing cross-platform application including an UWP app running on Windows, make sure to add Windows Notification Service permission.</span></span>
<span data-ttu-id="a503b-122">![必要なアクセス許可-WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)</span><span class="sxs-lookup"><span data-stu-id="a503b-122">![Required Permissions – WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)</span></span>
