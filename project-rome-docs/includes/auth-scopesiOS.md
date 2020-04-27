---
title: インクルード ファイル
description: インクルード ファイル
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b8a0de450431adce084919290d49f6326d23d51b
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755796"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="e006e-103">認証とアカウント管理の設定</span><span class="sxs-lookup"><span data-stu-id="e006e-103">Set up authentication and account management</span></span>

<span data-ttu-id="e006e-104">Connected Devices Platform では、有効な OAuth トークンを登録プロセスで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e006e-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="e006e-105">OAuth トークンの生成および管理には任意の方法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e006e-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="e006e-106">ただし、プラットフォームを初めて使用する開発者を支援するために、アプリで更新トークンの生成と管理に使用できる認証プロバイダーを [iOS サンプルアプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample)の一部として含めています。</span><span class="sxs-lookup"><span data-stu-id="e006e-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) that you can use to generate and manage refresh tokens in your app.</span></span>

<span data-ttu-id="e006e-107">提供されたコードを使用しない場合、 **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** インターフェイスを自身で実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e006e-107">If you do not use the provided code, you will need to implement the **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface yourself.</span></span>

<span data-ttu-id="e006e-108">MSA を使用している場合、サインイン要求に次のスコープを含めます: `"wl.offline_access"`、`"ccs.ReadWrite"`、`"dds.read"`、`"dds.register"`、`"wns.connect"`、`"asimovrome.telemetry"`、および `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`。</span><span class="sxs-lookup"><span data-stu-id="e006e-108">If you're using an MSA, include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span>

> [!NOTE]
> <span data-ttu-id="e006e-109">Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e006e-109">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="e006e-110">AAD アカウントを使用している場合、次の対象ユーザーを要求する必要があります: `"https://cdpcs.access.microsoft.com"`、`"https://cs.dds.microsoft.com"`、`"https://wns.windows.com/"`、および `"https://activity.microsoft.com"`。</span><span class="sxs-lookup"><span data-stu-id="e006e-110">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="e006e-111">提供されている **MCDConnectedDevicesAccountManager** の実装を使用するかどうかにかかわらず、AAD を使用している場合は、Azure portal のアプリの登録 (portal.azure.com > [Azure Active Directory] > [アプリの登録]) で次のアクセス許可を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e006e-111">Whether you use the provided **MCDConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span>
* <span data-ttu-id="e006e-112">Microsoft アクティビティ フィード サービス</span><span class="sxs-lookup"><span data-stu-id="e006e-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="e006e-113">このアプリのユーザー通知を配信および変更する</span><span class="sxs-lookup"><span data-stu-id="e006e-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="e006e-114">アプリのアクティビティを読み取ってユーザーのアクティビティ フィードに書き込む</span><span class="sxs-lookup"><span data-stu-id="e006e-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="e006e-115">Windows 通知サービス</span><span class="sxs-lookup"><span data-stu-id="e006e-115">Windows Notification Service</span></span>
  * <span data-ttu-id="e006e-116">デバイスを Windows 通知サービスに接続する</span><span class="sxs-lookup"><span data-stu-id="e006e-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="e006e-117">Microsoft デバイス ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="e006e-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="e006e-118">デバイスの一覧を参照する</span><span class="sxs-lookup"><span data-stu-id="e006e-118">See your list of devices</span></span>
  * <span data-ttu-id="e006e-119">デバイスとアプリの一覧に追加される</span><span class="sxs-lookup"><span data-stu-id="e006e-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="e006e-120">Microsoft コマンド サービス</span><span class="sxs-lookup"><span data-stu-id="e006e-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="e006e-121">ユーザー デバイスと通信する</span><span class="sxs-lookup"><span data-stu-id="e006e-121">Communicate with user devices</span></span>
  * <span data-ttu-id="e006e-122">ユーザー デバイスを読み取る</span><span class="sxs-lookup"><span data-stu-id="e006e-122">Read user devices</span></span>
