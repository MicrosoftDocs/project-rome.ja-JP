---
title: MCDConnectedDevicesAccountAddedStatus
description: 追加アカウントの操作の状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907204"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a><span data-ttu-id="79a24-104">列挙型 `MCDConnectedDevicesAccountAddedStatus`</span><span class="sxs-lookup"><span data-stu-id="79a24-104">enum `MCDConnectedDevicesAccountAddedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
<span data-ttu-id="79a24-105">追加アカウントの操作の状態を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="79a24-105">Contains the values that describe the add account operation status.</span></span>

## <a name="fields"></a><span data-ttu-id="79a24-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="79a24-106">Fields</span></span>

| <span data-ttu-id="79a24-107">名前</span><span class="sxs-lookup"><span data-stu-id="79a24-107">Name</span></span>                              |   <span data-ttu-id="79a24-108">値</span><span class="sxs-lookup"><span data-stu-id="79a24-108">Value</span></span>     | <span data-ttu-id="79a24-109">説明</span><span class="sxs-lookup"><span data-stu-id="79a24-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="79a24-110">MCDConnectedDevicesAccountAddedStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="79a24-110">MCDConnectedDevicesAccountAddedStatusSuccess</span></span> | <span data-ttu-id="79a24-111">0</span><span class="sxs-lookup"><span data-stu-id="79a24-111">0</span></span> | <span data-ttu-id="79a24-112">アカウントは、プラットフォームに正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="79a24-112">The account was successfully added to the platform.</span></span> |
| <span data-ttu-id="79a24-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="79a24-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span></span> | <span data-ttu-id="79a24-114">1</span><span class="sxs-lookup"><span data-stu-id="79a24-114">1</span></span> | <span data-ttu-id="79a24-115">ローマにネットワーク アクセスが検出されないために、アカウントの操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="79a24-115">The account operation failed since Rome detected no network access.</span></span> |
| <span data-ttu-id="79a24-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span><span class="sxs-lookup"><span data-stu-id="79a24-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span></span> | <span data-ttu-id="79a24-117">2</span><span class="sxs-lookup"><span data-stu-id="79a24-117">2</span></span> | <span data-ttu-id="79a24-118">ローマで web サービスにお問い合わせできなかったために、アカウントの操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="79a24-118">The account operation failed since Rome was unable to contact web services.</span></span> |
| <span data-ttu-id="79a24-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="79a24-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="79a24-120">3</span><span class="sxs-lookup"><span data-stu-id="79a24-120">3</span></span> | <span data-ttu-id="79a24-121">アカウントの操作では、アプリが AccessTokenRequested イベントをサブスクライブしていないために失敗しました。</span><span class="sxs-lookup"><span data-stu-id="79a24-121">The account operation failed since the app didn't subscribe to the AccessTokenRequested event.</span></span> |
| <span data-ttu-id="79a24-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="79a24-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="79a24-123">4</span><span class="sxs-lookup"><span data-stu-id="79a24-123">4</span></span> | <span data-ttu-id="79a24-124">要求されたときに、トークンをアプリが失敗したため、アカウントの操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="79a24-124">The account operation failed since the app failed to return a token when requested.</span></span> |
| <span data-ttu-id="79a24-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="79a24-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span></span> | <span data-ttu-id="79a24-126">5</span><span class="sxs-lookup"><span data-stu-id="79a24-126">5</span></span> | <span data-ttu-id="79a24-127">不明な理由により、アカウントの操作が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="79a24-127">The account operation failed for unknown reasons.</span></span> |
