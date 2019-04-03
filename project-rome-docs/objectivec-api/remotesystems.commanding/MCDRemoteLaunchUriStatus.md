---
title: MCDRemoteLaunchUriStatus
description: URI を使用して、リモート アプリの起動の状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 1a0302cd570b8cb25476a8188e3bcb1667707461
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907144"
---
# <a name="enum-mcdremotelaunchuristatus"></a><span data-ttu-id="2034d-104">列挙型 `MCDRemoteLaunchUriStatus`</span><span class="sxs-lookup"><span data-stu-id="2034d-104">enum `MCDRemoteLaunchUriStatus`</span></span>

`typedef NS_ENUM(NSInteger, MCDRemoteLaunchUriStatus)`

<span data-ttu-id="2034d-105">URI を使用して、リモート アプリの起動の状態を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2034d-105">Contains values that describe the status of a remote app launch using a URI.</span></span>


| <span data-ttu-id="2034d-106">名前</span><span class="sxs-lookup"><span data-stu-id="2034d-106">Name</span></span>    |<span data-ttu-id="2034d-107">値</span><span class="sxs-lookup"><span data-stu-id="2034d-107">Value</span></span>   |<span data-ttu-id="2034d-108">説明</span><span class="sxs-lookup"><span data-stu-id="2034d-108">Description</span></span>   |                  
|------ |------- |--|
|<span data-ttu-id="2034d-109">MCDRemoteLaunchUriStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="2034d-109">MCDRemoteLaunchUriStatusUnknown</span></span> | <span data-ttu-id="2034d-110">0</span><span class="sxs-lookup"><span data-stu-id="2034d-110">0</span></span>| <span data-ttu-id="2034d-111">状態が不明です。</span><span class="sxs-lookup"><span data-stu-id="2034d-111">The status is unknown.</span></span>|
|<span data-ttu-id="2034d-112">MCDRemoteLaunchUriStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="2034d-112">MCDRemoteLaunchUriStatusSuccess</span></span> | <span data-ttu-id="2034d-113">1</span><span class="sxs-lookup"><span data-stu-id="2034d-113">1</span></span>| <span data-ttu-id="2034d-114">リモートからの起動に成功しました。</span><span class="sxs-lookup"><span data-stu-id="2034d-114">The remote launch was successful.</span></span>|
|<span data-ttu-id="2034d-115">MCDRemoteLaunchUriStatusAppUnavailable</span><span class="sxs-lookup"><span data-stu-id="2034d-115">MCDRemoteLaunchUriStatusAppUnavailable</span></span> | <span data-ttu-id="2034d-116">2</span><span class="sxs-lookup"><span data-stu-id="2034d-116">2</span></span> | <span data-ttu-id="2034d-117">対象となるアプリでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="2034d-117">The target app is unavailable.</span></span>|
|<span data-ttu-id="2034d-118">MCDRemoteLaunchUriStatusProtocolUnavailable</span><span class="sxs-lookup"><span data-stu-id="2034d-118">MCDRemoteLaunchUriStatusProtocolUnavailable</span></span> | <span data-ttu-id="2034d-119">3</span><span class="sxs-lookup"><span data-stu-id="2034d-119">3</span></span> | <span data-ttu-id="2034d-120">対象となるアプリでは、この URI はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2034d-120">The target app does not support this URI.</span></span>|
|<span data-ttu-id="2034d-121">MCDRemoteLaunchUriStatusRemoteSystemUnavailable</span><span class="sxs-lookup"><span data-stu-id="2034d-121">MCDRemoteLaunchUriStatusRemoteSystemUnavailable</span></span> | <span data-ttu-id="2034d-122">4</span><span class="sxs-lookup"><span data-stu-id="2034d-122">4</span></span> | <span data-ttu-id="2034d-123">メッセージの送信、デバイスは、ご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="2034d-123">The device to which the message was sent is unavailable.</span></span>|
|<span data-ttu-id="2034d-124">MCDRemoteLaunchUriStatusValueSetTooLarge</span><span class="sxs-lookup"><span data-stu-id="2034d-124">MCDRemoteLaunchUriStatusValueSetTooLarge</span></span> | <span data-ttu-id="2034d-125">5</span><span class="sxs-lookup"><span data-stu-id="2034d-125">5</span></span> | <span data-ttu-id="2034d-126">対象となるアプリに送信される、データ バンドルが大きすぎます。</span><span class="sxs-lookup"><span data-stu-id="2034d-126">The data bundle sent to the target app was too large.</span></span>|
|<span data-ttu-id="2034d-127">MCDRemoteLaunchUriStatusDeniedByLocalSystem</span><span class="sxs-lookup"><span data-stu-id="2034d-127">MCDRemoteLaunchUriStatusDeniedByLocalSystem</span></span> | <span data-ttu-id="2034d-128">6</span><span class="sxs-lookup"><span data-stu-id="2034d-128">6</span></span> | <span data-ttu-id="2034d-129">クライアント システムがリモート システム プラットフォームを使用できないように設定します。</span><span class="sxs-lookup"><span data-stu-id="2034d-129">The client system has prevented use of the Remote Systems Platform.</span></span>|
|<span data-ttu-id="2034d-130">MCDRemoteLaunchUriStatusDeniedByRemoteSystem</span><span class="sxs-lookup"><span data-stu-id="2034d-130">MCDRemoteLaunchUriStatusDeniedByRemoteSystem</span></span> | <span data-ttu-id="2034d-131">7</span><span class="sxs-lookup"><span data-stu-id="2034d-131">7</span></span> | <span data-ttu-id="2034d-132">ターゲット デバイスがリモート システム プラットフォームを使用できないように設定します。</span><span class="sxs-lookup"><span data-stu-id="2034d-132">The target device has prevented use of the Remote Systems Platform.</span></span>|