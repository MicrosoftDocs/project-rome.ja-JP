---
title: MCDRemoteSystemAppRegistrationPublishStatus
description: URI を使用して、リモート アプリの起動の状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 32c3e473938925f12838bf6dc5ccc3e98a3394a6
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907544"
---
# <a name="enum-mcdremotesystemappregistrationpublishstatus"></a><span data-ttu-id="f431d-104">列挙型 `MCDRemoteSystemAppRegistrationPublishStatus`</span><span class="sxs-lookup"><span data-stu-id="f431d-104">enum `MCDRemoteSystemAppRegistrationPublishStatus`</span></span>

`typedef NS_ENUM(NSInteger, MCDRemoteSystemAppRegistrationPublishStatus)`

<span data-ttu-id="f431d-105">発行操作の状態を示す列挙です。</span><span class="sxs-lookup"><span data-stu-id="f431d-105">Enumeration indicating the status of the publish operation.</span></span>
<span data-ttu-id="f431d-106">エラー状態では、アプリ開発者の発行を再試行する必要のある一時的な状態を示します。</span><span class="sxs-lookup"><span data-stu-id="f431d-106">The error statuses indicate transient conditions where the app developer may want to retry publishing.</span></span>

| <span data-ttu-id="f431d-107">名前</span><span class="sxs-lookup"><span data-stu-id="f431d-107">Name</span></span>    |<span data-ttu-id="f431d-108">値</span><span class="sxs-lookup"><span data-stu-id="f431d-108">Value</span></span>   |<span data-ttu-id="f431d-109">説明</span><span class="sxs-lookup"><span data-stu-id="f431d-109">Description</span></span>   |                  
|------ |------- |--|
|<span data-ttu-id="f431d-110">MCDRemoteSystemAppRegistrationPublishStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="f431d-110">MCDRemoteSystemAppRegistrationPublishStatusSuccess</span></span> | <span data-ttu-id="f431d-111">0</span><span class="sxs-lookup"><span data-stu-id="f431d-111">0</span></span> | <span data-ttu-id="f431d-112">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="f431d-112">Operation completed successfully.</span></span>|
|<span data-ttu-id="f431d-113">MCDRemoteSystemAppRegistrationPublishStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="f431d-113">MCDRemoteSystemAppRegistrationPublishStatusErrorNoNetwork</span></span> | <span data-ttu-id="f431d-114">1</span><span class="sxs-lookup"><span data-stu-id="f431d-114">1</span></span> | <span data-ttu-id="f431d-115">ネットワークは使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="f431d-115">Network was unavailable.</span></span> |
|<span data-ttu-id="f431d-116">MCDRemoteSystemAppRegistrationPublishStatusErrorWebFailure</span><span class="sxs-lookup"><span data-stu-id="f431d-116">MCDRemoteSystemAppRegistrationPublishStatusErrorWebFailure</span></span> | <span data-ttu-id="f431d-117">2</span><span class="sxs-lookup"><span data-stu-id="f431d-117">2</span></span> | <span data-ttu-id="f431d-118">Web サービスが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f431d-118">A web service failed.</span></span>|
|<span data-ttu-id="f431d-119">MCDRemoteSystemAppRegistrationPublishStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="f431d-119">MCDRemoteSystemAppRegistrationPublishStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="f431d-120">3</span><span class="sxs-lookup"><span data-stu-id="f431d-120">3</span></span> | <span data-ttu-id="f431d-121">トークン要求のサブスクライバーが応答しません。</span><span class="sxs-lookup"><span data-stu-id="f431d-121">No token request subscribers responded.</span></span>|
|<span data-ttu-id="f431d-122">MCDRemoteSystemAppRegistrationPublishStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="f431d-122">MCDRemoteSystemAppRegistrationPublishStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="f431d-123">4</span><span class="sxs-lookup"><span data-stu-id="f431d-123">4</span></span> | <span data-ttu-id="f431d-124">トークンの要求が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="f431d-124">The token request failed.</span></span>|
|<span data-ttu-id="f431d-125">MCDRemoteSystemAppRegistrationPublishStatusErrorAccountNotFound</span><span class="sxs-lookup"><span data-stu-id="f431d-125">MCDRemoteSystemAppRegistrationPublishStatusErrorAccountNotFound</span></span> | <span data-ttu-id="f431d-126">5</span><span class="sxs-lookup"><span data-stu-id="f431d-126">5</span></span> | <span data-ttu-id="f431d-127">情報を発行するアカウントが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="f431d-127">Account to publish information for was not found.</span></span>|
|<span data-ttu-id="f431d-128">MCDRemoteSystemAppRegistrationPublishStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="f431d-128">MCDRemoteSystemAppRegistrationPublishStatusErrorUnknown</span></span> | <span data-ttu-id="f431d-129">6</span><span class="sxs-lookup"><span data-stu-id="f431d-129">6</span></span> | <span data-ttu-id="f431d-130">操作には、不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f431d-130">Operation encountered an unknown error.</span></span>|