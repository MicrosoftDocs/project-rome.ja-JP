---
title: MCDAppServiceClosedStatus
description: リモート アプリ サービスへの接続を閉じたを記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 9a56ee489175cb065fde281acb4ae8a345fb851b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907724"
---
# <a name="enum-mcdappserviceclosedstatus"></a><span data-ttu-id="da102-104">列挙型 `MCDAppServiceClosedStatus`</span><span class="sxs-lookup"><span data-stu-id="da102-104">enum `MCDAppServiceClosedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDAppServiceClosedStatus)
```

<span data-ttu-id="da102-105">リモート アプリ サービスへの接続を閉じたを記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="da102-105">Contains values that describe a closed connection to a remote app service.</span></span>

|<span data-ttu-id="da102-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="da102-106">Member</span></span>   |<span data-ttu-id="da102-107">Value</span><span class="sxs-lookup"><span data-stu-id="da102-107">Value</span></span>   |<span data-ttu-id="da102-108">説明</span><span class="sxs-lookup"><span data-stu-id="da102-108">Description</span></span>   |
|--------|-------|-------------|
|<span data-ttu-id="da102-109">MCDAppServiceClosedStatusCompleted</span><span class="sxs-lookup"><span data-stu-id="da102-109">MCDAppServiceClosedStatusCompleted</span></span> |<span data-ttu-id="da102-110">0</span><span class="sxs-lookup"><span data-stu-id="da102-110">0</span></span>| <span data-ttu-id="da102-111">App service のエンドポイントが正常に終了します。</span><span class="sxs-lookup"><span data-stu-id="da102-111">The endpoint for the app service closed gracefully.</span></span>|
|<span data-ttu-id="da102-112">MCDAppServiceClosedStatusCanceled</span><span class="sxs-lookup"><span data-stu-id="da102-112">MCDAppServiceClosedStatusCanceled</span></span> |<span data-ttu-id="da102-113">1</span><span class="sxs-lookup"><span data-stu-id="da102-113">1</span></span>| <span data-ttu-id="da102-114">App service のエンドポイントは、クライアントまたはシステムによって終了されました。</span><span class="sxs-lookup"><span data-stu-id="da102-114">The endpoint for the app service was closed by the client or the system.</span></span>|
|<span data-ttu-id="da102-115">MCDAppServiceClosedStatusResourceLimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="da102-115">MCDAppServiceClosedStatusResourceLimitsExceeded</span></span> |<span data-ttu-id="da102-116">2</span><span class="sxs-lookup"><span data-stu-id="da102-116">2</span></span>| <span data-ttu-id="da102-117">エンドポイントは、リソースが不足したため、app service のエンドポイントが閉じられました。</span><span class="sxs-lookup"><span data-stu-id="da102-117">The endpoint for the app service was closed because the endpoint ran out of resources.</span></span>|
|<span data-ttu-id="da102-118">MCDAppServiceClosedStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="da102-118">MCDAppServiceClosedStatusUnknown</span></span> |<span data-ttu-id="da102-119">3</span><span class="sxs-lookup"><span data-stu-id="da102-119">3</span></span>| <span data-ttu-id="da102-120">不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="da102-120">An unknown error occurred.</span></span>|