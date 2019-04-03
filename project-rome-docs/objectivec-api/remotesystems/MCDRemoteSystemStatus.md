---
title: MCDRemoteSystemStatus
description: リモート システムの可用性を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 4a69961b12def736733e1b6a78d376d57b2fa33f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907584"
---
# <a name="enum-mcdremotesystemstatus"></a><span data-ttu-id="34bf0-104">列挙型 `MCDRemoteSystemStatus`</span><span class="sxs-lookup"><span data-stu-id="34bf0-104">enum `MCDRemoteSystemStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
<span data-ttu-id="34bf0-105">リモート システムの可用性を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="34bf0-105">Contains values that describe the availability of a remote system.</span></span> <span data-ttu-id="34bf0-106">IOS アプリの値に**MCDRemoteSystemStatusUnknown**は常に発生する; 他の値は Windows システムで利用できるのみです。</span><span class="sxs-lookup"><span data-stu-id="34bf0-106">On iOS apps, a value of **MCDRemoteSystemStatusUnknown** will always be encountered; other values are only available on Windows systems.</span></span>

## <a name="fields"></a><span data-ttu-id="34bf0-107">フィールド</span><span class="sxs-lookup"><span data-stu-id="34bf0-107">Fields</span></span>

| <span data-ttu-id="34bf0-108">名前</span><span class="sxs-lookup"><span data-stu-id="34bf0-108">Name</span></span>                              | <span data-ttu-id="34bf0-109">値</span><span class="sxs-lookup"><span data-stu-id="34bf0-109">Value</span></span> | <span data-ttu-id="34bf0-110">説明</span><span class="sxs-lookup"><span data-stu-id="34bf0-110">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="34bf0-111">MCDRemoteSystemStatusUnavailable</span><span class="sxs-lookup"><span data-stu-id="34bf0-111">MCDRemoteSystemStatusUnavailable</span></span> | <span data-ttu-id="34bf0-112">0</span><span class="sxs-lookup"><span data-stu-id="34bf0-112">0</span></span> | <span data-ttu-id="34bf0-113">リモート システムが利用不可と報告されます。</span><span class="sxs-lookup"><span data-stu-id="34bf0-113">The remote system is reported as unavailable.</span></span> |
| <span data-ttu-id="34bf0-114">MCDRemoteSystemStatusDiscoveringAvailablilty</span><span class="sxs-lookup"><span data-stu-id="34bf0-114">MCDRemoteSystemStatusDiscoveringAvailablilty</span></span> | <span data-ttu-id="34bf0-115">1</span><span class="sxs-lookup"><span data-stu-id="34bf0-115">1</span></span> | <span data-ttu-id="34bf0-116">リモート システムのステータスを特定する複素数 (検出プロセス中に発生します)。</span><span class="sxs-lookup"><span data-stu-id="34bf0-116">The status of the remote system is being determined (occurs during the discovery process).</span></span> |
| <span data-ttu-id="34bf0-117">MCDRemoteSystemStatusAvailable</span><span class="sxs-lookup"><span data-stu-id="34bf0-117">MCDRemoteSystemStatusAvailable</span></span> | <span data-ttu-id="34bf0-118">2</span><span class="sxs-lookup"><span data-stu-id="34bf0-118">2</span></span> | <span data-ttu-id="34bf0-119">リモート システムが利用可能として報告されます。</span><span class="sxs-lookup"><span data-stu-id="34bf0-119">The remote system is reported as available.</span></span> |
| <span data-ttu-id="34bf0-120">MCDRemoteSystemStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="34bf0-120">MCDRemoteSystemStatusUnknown</span></span> | <span data-ttu-id="34bf0-121">3</span><span class="sxs-lookup"><span data-stu-id="34bf0-121">3</span></span> | <span data-ttu-id="34bf0-122">状態が不明です。</span><span class="sxs-lookup"><span data-stu-id="34bf0-122">The status is unknown.</span></span> |
