---
title: MCDRemoteSystemDiscoveryTypeFilter
description: MCDRemoteSystemDiscoveryTypeFilter クラスについて説明します。 このクラスは、検出の種類に基づいてリモートシステムをフィルター処理するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: a38036811fda38df944e67e431f864c33d1c335d
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760696"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a><span data-ttu-id="dd0df-105">講義 `MCDRemoteSystemDiscoveryTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="dd0df-105">class `MCDRemoteSystemDiscoveryTypeFilter`</span></span> 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="dd0df-106">探索の種類に基づいてリモートシステムをフィルター処理するために使用されるクラス。</span><span class="sxs-lookup"><span data-stu-id="dd0df-106">A class used to filter remote systems based upon discovery type.</span></span>

## <a name="properties"></a><span data-ttu-id="dd0df-107">Properties</span><span class="sxs-lookup"><span data-stu-id="dd0df-107">Properties</span></span>

### <a name="type"></a><span data-ttu-id="dd0df-108">type</span><span class="sxs-lookup"><span data-stu-id="dd0df-108">type</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

<span data-ttu-id="dd0df-109">フィルター処理の対象となる検出の種類。</span><span class="sxs-lookup"><span data-stu-id="dd0df-109">The discovery type to filter for.</span></span>

> <span data-ttu-id="dd0df-110">注: Android では、接続されているデバイスプラットフォームは、Android 8.0 (Oreo) 以降を実行しているシステムでのみ Bluetooth を使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd0df-110">Note: On Android, the Connected Devices Platform can only use Bluetooth on systems running Android 8.0 (Oreo) or later.</span></span>

## <a name="constructors"></a><span data-ttu-id="dd0df-111">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="dd0df-111">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="dd0df-112">filterWithType</span><span class="sxs-lookup"><span data-stu-id="dd0df-112">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="dd0df-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd0df-113">Parameters</span></span> 
* <span data-ttu-id="dd0df-114">`discoveryType` フィルター処理の対象となる検出の種類。</span><span class="sxs-lookup"><span data-stu-id="dd0df-114">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="dd0df-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="dd0df-115">Returns</span></span>
<span data-ttu-id="dd0df-116">指定された型の値を持つ、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="dd0df-116">A new instance of this class with the given type value.</span></span> <span data-ttu-id="dd0df-117">一度に複数のフィルターを適用するために、値を組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd0df-117">Values can be AND'ed together to apply multiple filters at once.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="dd0df-118">initWithType</span><span class="sxs-lookup"><span data-stu-id="dd0df-118">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="dd0df-119">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd0df-119">Parameters</span></span> 
* <span data-ttu-id="dd0df-120">`discoveryType` フィルター処理の対象となる検出の種類。</span><span class="sxs-lookup"><span data-stu-id="dd0df-120">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="dd0df-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="dd0df-121">Returns</span></span>
<span data-ttu-id="dd0df-122">指定された型の値を持つ、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="dd0df-122">A new instance of this class with the given type value.</span></span> <span data-ttu-id="dd0df-123">一度に複数のフィルターを適用するために、値を組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="dd0df-123">Values can be AND'ed together to apply multiple filters at once.</span></span>