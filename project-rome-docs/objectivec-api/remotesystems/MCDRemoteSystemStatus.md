---
title: MCDRemoteSystemStatus
description: MCDRemoteSystemStatus 列挙型について説明します。 この列挙には、リモートシステムの可用性を表す値が含まれます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 71e4216c949506f45f26a7c035ff043a55168b23
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760656"
---
# <a name="enum-mcdremotesystemstatus"></a><span data-ttu-id="dd1f1-105">enum `MCDRemoteSystemStatus`</span><span class="sxs-lookup"><span data-stu-id="dd1f1-105">enum `MCDRemoteSystemStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
<span data-ttu-id="dd1f1-106">リモートシステムの可用性を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="dd1f1-106">Contains values that describe the availability of a remote system.</span></span> <span data-ttu-id="dd1f1-107">IOS アプリでは、 **MCDRemoteSystemStatusUnknown** の値が常に検出されます。その他の値は、Windows システムでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd1f1-107">On iOS apps, a value of **MCDRemoteSystemStatusUnknown** will always be encountered; other values are only available on Windows systems.</span></span>

## <a name="fields"></a><span data-ttu-id="dd1f1-108">フィールド</span><span class="sxs-lookup"><span data-stu-id="dd1f1-108">Fields</span></span>

| <span data-ttu-id="dd1f1-109">名前</span><span class="sxs-lookup"><span data-stu-id="dd1f1-109">Name</span></span>                              | <span data-ttu-id="dd1f1-110">[値]</span><span class="sxs-lookup"><span data-stu-id="dd1f1-110">Value</span></span> | <span data-ttu-id="dd1f1-111">説明</span><span class="sxs-lookup"><span data-stu-id="dd1f1-111">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="dd1f1-112">MCDRemoteSystemStatusUnavailable</span><span class="sxs-lookup"><span data-stu-id="dd1f1-112">MCDRemoteSystemStatusUnavailable</span></span> | <span data-ttu-id="dd1f1-113">0</span><span class="sxs-lookup"><span data-stu-id="dd1f1-113">0</span></span> | <span data-ttu-id="dd1f1-114">リモートシステムは使用不可として報告されます。</span><span class="sxs-lookup"><span data-stu-id="dd1f1-114">The remote system is reported as unavailable.</span></span> |
| <span data-ttu-id="dd1f1-115">MCDRemoteSystemStatusDiscoveringAvailablilty</span><span class="sxs-lookup"><span data-stu-id="dd1f1-115">MCDRemoteSystemStatusDiscoveringAvailablilty</span></span> | <span data-ttu-id="dd1f1-116">1</span><span class="sxs-lookup"><span data-stu-id="dd1f1-116">1</span></span> | <span data-ttu-id="dd1f1-117">リモートシステムの状態が特定されている (検出プロセス中に発生する)。</span><span class="sxs-lookup"><span data-stu-id="dd1f1-117">The status of the remote system is being determined (occurs during the discovery process).</span></span> |
| <span data-ttu-id="dd1f1-118">MCDRemoteSystemStatusAvailable</span><span class="sxs-lookup"><span data-stu-id="dd1f1-118">MCDRemoteSystemStatusAvailable</span></span> | <span data-ttu-id="dd1f1-119">2</span><span class="sxs-lookup"><span data-stu-id="dd1f1-119">2</span></span> | <span data-ttu-id="dd1f1-120">リモートシステムが使用可能として報告されます。</span><span class="sxs-lookup"><span data-stu-id="dd1f1-120">The remote system is reported as available.</span></span> |
| <span data-ttu-id="dd1f1-121">MCDRemoteSystemStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="dd1f1-121">MCDRemoteSystemStatusUnknown</span></span> | <span data-ttu-id="dd1f1-122">3</span><span class="sxs-lookup"><span data-stu-id="dd1f1-122">3</span></span> | <span data-ttu-id="dd1f1-123">状態が不明です。</span><span class="sxs-lookup"><span data-stu-id="dd1f1-123">The status is unknown.</span></span> |
