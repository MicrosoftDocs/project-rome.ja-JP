---
title: インクルード ファイル
description: インクルード ファイル
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: a6e92df6114443827b22dc85cf877d631e5fcfdf
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755785"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="c8dbe-103">認証とアカウント管理の設定</span><span class="sxs-lookup"><span data-stu-id="c8dbe-103">Set up authentication and account management</span></span>

<span data-ttu-id="c8dbe-104">Connected Devices Platform では、有効な OAuth トークンを登録プロセスで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8dbe-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="c8dbe-105">OAuth トークンの生成および管理には任意の方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8dbe-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="c8dbe-106">ただし、プラットフォームを初めて使用する開発者を支援し、利便性を高めるために、更新トークンを生成および管理する認証プロバイダーを [Android サンプルアプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)の一部として含めています。</span><span class="sxs-lookup"><span data-stu-id="c8dbe-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples) that generates and manages refresh tokens for your convenience.</span></span>

<span data-ttu-id="c8dbe-107">**[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** インターフェイスを独自に実装する場合は、次の情報に留意してください。</span><span class="sxs-lookup"><span data-stu-id="c8dbe-107">If you wish to implement the **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** interface yourself, take note of the following information:</span></span> 

<span data-ttu-id="c8dbe-108">MSA を使用している場合、サインイン要求に次のスコープを含める必要があります: `"wl.offline_access"`、`"ccs.ReadWrite"`、`"dds.read"`、`"dds.register"`、`"wns.connect"`、`"asimovrome.telemetry"`、および `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`。</span><span class="sxs-lookup"><span data-stu-id="c8dbe-108">If you're using an MSA, you will need to include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span> 

<span data-ttu-id="c8dbe-109">AAD アカウントを使用している場合、次の対象ユーザーを要求する必要があります: `"https://cdpcs.access.microsoft.com"`、`"https://cs.dds.microsoft.com"`、`"https://wns.windows.com/"`、および `"https://activity.microsoft.com"`。</span><span class="sxs-lookup"><span data-stu-id="c8dbe-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

> [!NOTE]
> <span data-ttu-id="c8dbe-110">Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c8dbe-110">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="c8dbe-111">提供されている **ConnectedDevicesAccountManager** の実装を使用するかどうかにかかわらず、AAD を使用している場合は、Azure portal のアプリの登録 (portal.azure.com > [Azure Active Directory] > [アプリの登録]) で次のアクセス許可を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8dbe-111">Whether you use the provided **ConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span> 
* <span data-ttu-id="c8dbe-112">Microsoft アクティビティ フィード サービス</span><span class="sxs-lookup"><span data-stu-id="c8dbe-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="c8dbe-113">このアプリのユーザー通知を配信および変更する</span><span class="sxs-lookup"><span data-stu-id="c8dbe-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="c8dbe-114">アプリのアクティビティを読み取ってユーザーのアクティビティ フィードに書き込む</span><span class="sxs-lookup"><span data-stu-id="c8dbe-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="c8dbe-115">Windows 通知サービス</span><span class="sxs-lookup"><span data-stu-id="c8dbe-115">Windows Notification Service</span></span>
  * <span data-ttu-id="c8dbe-116">デバイスを Windows 通知サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="c8dbe-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="c8dbe-117">Microsoft デバイス ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="c8dbe-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="c8dbe-118">デバイスの一覧を参照する</span><span class="sxs-lookup"><span data-stu-id="c8dbe-118">See your list of devices</span></span>
  * <span data-ttu-id="c8dbe-119">デバイスとアプリの一覧に追加される</span><span class="sxs-lookup"><span data-stu-id="c8dbe-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="c8dbe-120">Microsoft コマンド サービス</span><span class="sxs-lookup"><span data-stu-id="c8dbe-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="c8dbe-121">ユーザー デバイスと通信する</span><span class="sxs-lookup"><span data-stu-id="c8dbe-121">Communicate with user devices</span></span>
  * <span data-ttu-id="c8dbe-122">ユーザー デバイスを読み取る</span><span class="sxs-lookup"><span data-stu-id="c8dbe-122">Read user devices</span></span>
