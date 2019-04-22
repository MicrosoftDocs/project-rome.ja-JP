---
title: MCDAppServiceResponseStatus
description: リモート アプリ サービスから応答メッセージの状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 395c2669af7178ef90ff7fd2dc8bafe9b1044028
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800334"
---
# <a name="enum-mcdappserviceresponsestatus"></a><span data-ttu-id="1a811-104">列挙型 `MCDAppServiceResponseStatus`</span><span class="sxs-lookup"><span data-stu-id="1a811-104">enum `MCDAppServiceResponseStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDAppServiceResponseStatus)
```

<span data-ttu-id="1a811-105">リモート アプリ サービスから応答メッセージの状態を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a811-105">Contains values that describe the status of a response message from a remote app service.</span></span>

|<span data-ttu-id="1a811-106">名前</span><span class="sxs-lookup"><span data-stu-id="1a811-106">Name</span></span>         | <span data-ttu-id="1a811-107">値</span><span class="sxs-lookup"><span data-stu-id="1a811-107">Value</span></span>  | <span data-ttu-id="1a811-108">説明</span><span class="sxs-lookup"><span data-stu-id="1a811-108">Description</span></span>    |                           
|--------|-------------|-----|
|<span data-ttu-id="1a811-109">MCDAppServiceResponseStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="1a811-109">MCDAppServiceResponseStatusSuccess</span></span> |<span data-ttu-id="1a811-110">0</span><span class="sxs-lookup"><span data-stu-id="1a811-110">0</span></span>| <span data-ttu-id="1a811-111">App service は正常に受信し、メッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="1a811-111">The app service successfully received and processed the message.</span></span>|
|<span data-ttu-id="1a811-112">MCDAppServiceResponseStatusFailure</span><span class="sxs-lookup"><span data-stu-id="1a811-112">MCDAppServiceResponseStatusFailure</span></span> |<span data-ttu-id="1a811-113">1</span><span class="sxs-lookup"><span data-stu-id="1a811-113">1</span></span>| <span data-ttu-id="1a811-114">App service は、受信とメッセージを処理できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1a811-114">The app service failed to receive and process the message.</span></span>|
|<span data-ttu-id="1a811-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="1a811-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span></span> |<span data-ttu-id="1a811-116">2</span><span class="sxs-lookup"><span data-stu-id="1a811-116">2</span></span>| <span data-ttu-id="1a811-117">App service では、十分なリソースが使用可能なために終了しました。</span><span class="sxs-lookup"><span data-stu-id="1a811-117">The app service exited because not enough resources were available.</span></span>|
|<span data-ttu-id="1a811-118">MCDAppServiceResponseStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="1a811-118">MCDAppServiceResponseStatusUnknown</span></span> |<span data-ttu-id="1a811-119">3</span><span class="sxs-lookup"><span data-stu-id="1a811-119">3</span></span>| <span data-ttu-id="1a811-120">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1a811-120">An unknown error occurred.</span></span>|
|<span data-ttu-id="1a811-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span><span class="sxs-lookup"><span data-stu-id="1a811-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span></span> |<span data-ttu-id="1a811-122">4</span><span class="sxs-lookup"><span data-stu-id="1a811-122">4</span></span>| <span data-ttu-id="1a811-123">メッセージの送信、デバイスは、ご利用いただけません。</span><span class="sxs-lookup"><span data-stu-id="1a811-123">The device to which the message was sent is not available.</span></span>|
|<span data-ttu-id="1a811-124">MCDAppServiceResponseStatusMessageTooLarge</span><span class="sxs-lookup"><span data-stu-id="1a811-124">MCDAppServiceResponseStatusMessageTooLarge</span></span> |<span data-ttu-id="1a811-125">5</span><span class="sxs-lookup"><span data-stu-id="1a811-125">5</span></span>| <span data-ttu-id="1a811-126">App service が大きすぎるため、メッセージを処理できませんでした。</span><span class="sxs-lookup"><span data-stu-id="1a811-126">The app service failed to process the message because it is too large.</span></span>|
|<span data-ttu-id="1a811-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="1a811-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span></span>|<span data-ttu-id="1a811-128">6</span><span class="sxs-lookup"><span data-stu-id="1a811-128">6</span></span>| <span data-ttu-id="1a811-129">応答が送信される前に、アプリ サービスの接続が閉じられました。</span><span class="sxs-lookup"><span data-stu-id="1a811-129">The app service connection was closed before a response was sent.</span></span>|