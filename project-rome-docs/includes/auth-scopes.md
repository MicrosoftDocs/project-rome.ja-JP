---
title: インクルード ファイル
description: インクルード ファイル
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: a6e92df6114443827b22dc85cf877d631e5fcfdf
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755785"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="e811d-103">認証とアカウントの管理を設定します。</span><span class="sxs-lookup"><span data-stu-id="e811d-103">Set up authentication and account management</span></span>

<span data-ttu-id="e811d-104">接続されているデバイス プラットフォームでは、登録プロセスで使用される有効な OAuth トークンが必要です。</span><span class="sxs-lookup"><span data-stu-id="e811d-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="e811d-105">ご希望の生成と OAuth トークンを管理する方法を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="e811d-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="e811d-106">ただし、ため開発者は、プラットフォームの使用を開始、認証プロバイダーの一部として含まれています、 [Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)を生成し、必要に応じて更新トークンを管理します。</span><span class="sxs-lookup"><span data-stu-id="e811d-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples) that generates and manages refresh tokens for your convenience.</span></span>

<span data-ttu-id="e811d-107">実装する場合、 **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** インターフェイスを自分で、次の情報をメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="e811d-107">If you wish to implement the **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** interface yourself, take note of the following information:</span></span> 

<span data-ttu-id="e811d-108">MSA を使用している場合は、サインイン要求に、次のスコープを含める必要があります。: `"wl.offline_access"`、 `"ccs.ReadWrite"`、 `"dds.read"`、 `"dds.register"`、 `"wns.connect"`、 `"asimovrome.telemetry"`、および`"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`します。</span><span class="sxs-lookup"><span data-stu-id="e811d-108">If you're using an MSA, you will need to include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span> 

<span data-ttu-id="e811d-109">AAD アカウントを使用している場合は次のユーザーを要求する必要があります: `"https://cdpcs.access.microsoft.com"`、 `"https://cs.dds.microsoft.com"`、 `"https://wns.windows.com/"`、および`"https://activity.microsoft.com"`します。</span><span class="sxs-lookup"><span data-stu-id="e811d-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

> [!NOTE]
> <span data-ttu-id="e811d-110">デバイスの Relay Api では、azure Active Directory (AAD) アカウントはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e811d-110">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="e811d-111">指定されたを使用するかどうか**ConnectedDevicesAccountManager**実装または AAD アプリの登録、Azure portal で次のアクセス許可を指定する必要がありますを使用している場合、not (portal.azure.com > AzureActive Directory > アプリの登録)。</span><span class="sxs-lookup"><span data-stu-id="e811d-111">Whether you use the provided **ConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span> 
* <span data-ttu-id="e811d-112">Microsoft アクティビティ フィードのサービス</span><span class="sxs-lookup"><span data-stu-id="e811d-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="e811d-113">配信し、このアプリのユーザー通知の変更</span><span class="sxs-lookup"><span data-stu-id="e811d-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="e811d-114">読み取りおよび書き込みユーザーのアクティビティ フィードにアプリの動作</span><span class="sxs-lookup"><span data-stu-id="e811d-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="e811d-115">Windows 通知サービス</span><span class="sxs-lookup"><span data-stu-id="e811d-115">Windows Notification Service</span></span>
  * <span data-ttu-id="e811d-116">デバイスを Windows 通知サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="e811d-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="e811d-117">デバイスの Microsoft ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="e811d-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="e811d-118">デバイスの一覧を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e811d-118">See your list of devices</span></span>
  * <span data-ttu-id="e811d-119">デバイスとアプリの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="e811d-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="e811d-120">Microsoft Command サービス</span><span class="sxs-lookup"><span data-stu-id="e811d-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="e811d-121">ユーザーのデバイスと通信します。</span><span class="sxs-lookup"><span data-stu-id="e811d-121">Communicate with user devices</span></span>
  * <span data-ttu-id="e811d-122">ユーザー デバイスを読み取り</span><span class="sxs-lookup"><span data-stu-id="e811d-122">Read user devices</span></span>
