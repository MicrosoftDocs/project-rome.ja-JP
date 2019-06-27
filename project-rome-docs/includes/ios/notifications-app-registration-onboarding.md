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
### <a name="msa-and-aad-authentication-registration"></a><span data-ttu-id="aa1d5-103">MSA および AAD 認証登録</span><span class="sxs-lookup"><span data-stu-id="aa1d5-103">MSA and AAD Authentication Registration</span></span>

> [!NOTE]
> <span data-ttu-id="aa1d5-104">Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-104">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="aa1d5-105">MSA をまだ所有しておらず、使用したい場合は、[account.microsoft.com](https://account.microsoft.com/account) で登録してください。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-105">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="aa1d5-106">次に、ユーザー用の認証および ID フレームワークとして MSA を使用している場合、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)の指示に従って、アプリを Microsoft に登録する必要があります (Microsoft 開発者アカウントを所有していない場合は、最初に作成する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-106">Next, if you are using MSA as the authentication and identity framework for your users, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="aa1d5-107">アプリのクライアント ID 文字列が届くはずです。必ず、場所を覚えておくか保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-107">You should receive a client ID string for your app; make sure to remember the location or save this.</span></span> <span data-ttu-id="aa1d5-108">これは後で Graph 通知のオンボーディング中に使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-108">Later this will be used during Graph Notifications onboarding.</span></span> <span data-ttu-id="aa1d5-109">MSA 認証を使用するアプリは Live SDK アプリケーションとして登録する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-109">Note that an app using MSA authentication needs to be registered as a Live SDK application.</span></span>
<span data-ttu-id="aa1d5-110">![アプリケーション登録ポータル](../../notifications/media/msa_app_registration/app_registration_portal.png)</span><span class="sxs-lookup"><span data-stu-id="aa1d5-110">![Application Registration Portal](../../notifications/media/msa_app_registration/app_registration_portal.png)</span></span>

<span data-ttu-id="aa1d5-111">職場アカウントまたは学校アカウントの認証および ID フレームワークとして AAD を使用するアプリを作成している場合は、クライアント ID を取得するために [Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)経由でアプリを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-111">If you're writing an app that uses AAD as work account or school account authentication and identity framework, you must register your app via [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) in order to get the client ID.</span></span> 
 <span data-ttu-id="aa1d5-112">![AAD 登録ポータル](../../notifications/media/aad_registration_portal/aad_registration_portal.png) 新しいアプリ登録を作成するとき、Graph 通知やその他の Connected Devices Platform の機能を使用するために必要なアクセス許可がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-112">![AAD Registration Portal](../../notifications/media/aad_registration_portal/aad_registration_portal.png) When creating a new app registration, there are a few permissions required in order to use Graph Notifications and other connected device platform capabilities.</span></span> <span data-ttu-id="aa1d5-113">下記を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-113">Please see below.</span></span> 
<span data-ttu-id="aa1d5-114">![AAD 登録ポータル – 設定 – 必要なアクセス許可](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)</span><span class="sxs-lookup"><span data-stu-id="aa1d5-114">![AAD Registration Portal – Setting – Required Permissions](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)</span></span>
* <span data-ttu-id="aa1d5-115">ユーザーのサインインのアクセス許可を追加します。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-115">Add user sign-in permission.</span></span>
<span data-ttu-id="aa1d5-116">![必要なアクセス許可 – AAD ユーザー プロファイル](../../notifications/media/aad_registration_portal/permissions_1_user.png)</span><span class="sxs-lookup"><span data-stu-id="aa1d5-116">![Required Permissions – AAD User Profile](../../notifications/media/aad_registration_portal/permissions_1_user.png)</span></span>
* <span data-ttu-id="aa1d5-117">デバイス情報に対するコマンド サービスのアクセス許可を追加します。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-117">Add Command Service permissions for device information.</span></span>
<span data-ttu-id="aa1d5-118">![必要なアクセス許可 – デバイス](../../notifications/media/aad_registration_portal/permissions_2_devices.png)</span><span class="sxs-lookup"><span data-stu-id="aa1d5-118">![Required Permissions – Devices](../../notifications/media/aad_registration_portal/permissions_2_devices.png)</span></span>
* <span data-ttu-id="aa1d5-119">アクティビティ フィード サービス API の下に Graph 通知のアクセス許可を追加します。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-119">Add Graph Notifications permission under Activity Feed Service APIs.</span></span>
<span data-ttu-id="aa1d5-120">![必要なアクセス許可 – デバイス](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)</span><span class="sxs-lookup"><span data-stu-id="aa1d5-120">![Required Permissions – Devices](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)</span></span>
* <span data-ttu-id="aa1d5-121">最後に、Windows で動作する UWP アプリを含むクロスプラットフォーム アプリケーションを作成している場合は、Windows 通知サービスのアクセス許可を必ず追加してください。</span><span class="sxs-lookup"><span data-stu-id="aa1d5-121">At the end, if you are writing cross-platform application including an UWP app running on Windows, make sure to add Windows Notification Service permission.</span></span>
<span data-ttu-id="aa1d5-122">![必要なアクセス許可 – WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)</span><span class="sxs-lookup"><span data-stu-id="aa1d5-122">![Required Permissions – WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)</span></span>
