---
title: インクルード ファイル
description: インクルード ファイル
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: 1aa6b0d971feb7d2f9f8d31708fda31d05b5aca9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907904"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="1304d-103">認証とアカウントの管理を設定します。</span><span class="sxs-lookup"><span data-stu-id="1304d-103">Set up authentication and account management</span></span>

<span data-ttu-id="1304d-104">接続されているデバイス プラットフォームでは、登録プロセスで使用される有効な OAuth トークンが必要です。</span><span class="sxs-lookup"><span data-stu-id="1304d-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="1304d-105">ご希望の生成と OAuth トークンを管理する方法を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="1304d-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="1304d-106">ただし、ため開発者は、プラットフォームの使用を開始、認証プロバイダーの一部として含まれています、 [iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample)を生成し、アプリでの更新トークンの管理を行えます。</span><span class="sxs-lookup"><span data-stu-id="1304d-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) that you can use to generate and manage refresh tokens in your app.</span></span>

<span data-ttu-id="1304d-107">提供されたコードを使用しない場合は、実装する必要があります。、 **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** インターフェイスを自分でします。</span><span class="sxs-lookup"><span data-stu-id="1304d-107">If you do not use the provided code, you will need to implement the **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface yourself.</span></span>

<span data-ttu-id="1304d-108">MSA を使用している場合は、サインイン要求に、次のスコープを含める: `"wl.offline_access"`、 `"ccs.ReadWrite"`、 `"dds.read"`、 `"dds.register"`、 `"wns.connect"`、 `"asimovrome.telemetry"`、および`"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`します。</span><span class="sxs-lookup"><span data-stu-id="1304d-108">If you're using an MSA, include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span>

<span data-ttu-id="1304d-109">AAD アカウントを使用している場合は次のユーザーを要求する必要があります: `"https://cdpcs.access.microsoft.com"`、 `"https://cs.dds.microsoft.com"`、 `"https://wns.windows.com/"`、および`"https://activity.microsoft.com"`します。</span><span class="sxs-lookup"><span data-stu-id="1304d-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="1304d-110">指定されたを使用するかどうか**MCDConnectedDevicesAccountManager**実装または AAD アプリの登録、Azure portal で次のアクセス許可を指定する必要がありますを使用している場合、not (portal.azure.com >Azure Active Directory > アプリの登録)。</span><span class="sxs-lookup"><span data-stu-id="1304d-110">Whether you use the provided **MCDConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span>
* <span data-ttu-id="1304d-111">Microsoft アクティビティ フィードのサービス</span><span class="sxs-lookup"><span data-stu-id="1304d-111">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="1304d-112">配信し、このアプリのユーザー通知の変更</span><span class="sxs-lookup"><span data-stu-id="1304d-112">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="1304d-113">読み取りおよび書き込みユーザーのアクティビティ フィードにアプリの動作</span><span class="sxs-lookup"><span data-stu-id="1304d-113">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="1304d-114">Windows 通知サービス</span><span class="sxs-lookup"><span data-stu-id="1304d-114">Windows Notification Service</span></span>
  * <span data-ttu-id="1304d-115">デバイスを Windows 通知サービスに接続します。</span><span class="sxs-lookup"><span data-stu-id="1304d-115">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="1304d-116">デバイスの Microsoft ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="1304d-116">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="1304d-117">デバイスの一覧を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1304d-117">See your list of devices</span></span>
  * <span data-ttu-id="1304d-118">デバイスとアプリの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="1304d-118">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="1304d-119">Microsoft Command サービス</span><span class="sxs-lookup"><span data-stu-id="1304d-119">Microsoft Command Service</span></span>
  * <span data-ttu-id="1304d-120">ユーザーのデバイスと通信します。</span><span class="sxs-lookup"><span data-stu-id="1304d-120">Communicate with user devices</span></span>
  * <span data-ttu-id="1304d-121">ユーザー デバイスを読み取り</span><span class="sxs-lookup"><span data-stu-id="1304d-121">Read user devices</span></span>
