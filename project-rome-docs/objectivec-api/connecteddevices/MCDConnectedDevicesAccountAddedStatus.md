---
title: MCDConnectedDevicesAccountAddedStatus
description: 追加アカウントの操作の状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801564"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a><span data-ttu-id="9f540-104">列挙型 `MCDConnectedDevicesAccountAddedStatus`</span><span class="sxs-lookup"><span data-stu-id="9f540-104">enum `MCDConnectedDevicesAccountAddedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
<span data-ttu-id="9f540-105">追加アカウントの操作の状態を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9f540-105">Contains the values that describe the add account operation status.</span></span>

## <a name="fields"></a><span data-ttu-id="9f540-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="9f540-106">Fields</span></span>

| <span data-ttu-id="9f540-107">名前</span><span class="sxs-lookup"><span data-stu-id="9f540-107">Name</span></span>                              |   <span data-ttu-id="9f540-108">値</span><span class="sxs-lookup"><span data-stu-id="9f540-108">Value</span></span>     | <span data-ttu-id="9f540-109">説明</span><span class="sxs-lookup"><span data-stu-id="9f540-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="9f540-110">MCDConnectedDevicesAccountAddedStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="9f540-110">MCDConnectedDevicesAccountAddedStatusSuccess</span></span> | <span data-ttu-id="9f540-111">0</span><span class="sxs-lookup"><span data-stu-id="9f540-111">0</span></span> | <span data-ttu-id="9f540-112">アカウントは、プラットフォームに正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="9f540-112">The account was successfully added to the platform.</span></span> |
| <span data-ttu-id="9f540-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="9f540-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span></span> | <span data-ttu-id="9f540-114">1</span><span class="sxs-lookup"><span data-stu-id="9f540-114">1</span></span> | <span data-ttu-id="9f540-115">ローマにネットワーク アクセスが検出されないために、アカウントの操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f540-115">The account operation failed since Rome detected no network access.</span></span> |
| <span data-ttu-id="9f540-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span><span class="sxs-lookup"><span data-stu-id="9f540-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span></span> | <span data-ttu-id="9f540-117">2</span><span class="sxs-lookup"><span data-stu-id="9f540-117">2</span></span> | <span data-ttu-id="9f540-118">ローマで web サービスにお問い合わせできなかったために、アカウントの操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f540-118">The account operation failed since Rome was unable to contact web services.</span></span> |
| <span data-ttu-id="9f540-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="9f540-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="9f540-120">3</span><span class="sxs-lookup"><span data-stu-id="9f540-120">3</span></span> | <span data-ttu-id="9f540-121">アカウントの操作では、アプリが AccessTokenRequested イベントをサブスクライブしていないために失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f540-121">The account operation failed since the app didn't subscribe to the AccessTokenRequested event.</span></span> |
| <span data-ttu-id="9f540-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="9f540-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="9f540-123">4</span><span class="sxs-lookup"><span data-stu-id="9f540-123">4</span></span> | <span data-ttu-id="9f540-124">要求されたときに、トークンをアプリが失敗したため、アカウントの操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f540-124">The account operation failed since the app failed to return a token when requested.</span></span> |
| <span data-ttu-id="9f540-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="9f540-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span></span> | <span data-ttu-id="9f540-126">5</span><span class="sxs-lookup"><span data-stu-id="9f540-126">5</span></span> | <span data-ttu-id="9f540-127">不明な理由により、アカウントの操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f540-127">The account operation failed for unknown reasons.</span></span> |
