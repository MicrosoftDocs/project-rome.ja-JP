---
title: MCDRemoteSystemAuthorizationKindFilter
description: MCDRemoteSystemAuthorizationKindFilter クラスについて説明します。 このクラスは、承認の種類に基づいてリモートシステムをフィルター処理するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: a48c9aeacf262146a12da6fd691e853cb7dde199
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760706"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a><span data-ttu-id="8a19d-105">講義 `MCDRemoteSystemAuthorizationKindFilter`</span><span class="sxs-lookup"><span data-stu-id="8a19d-105">class `MCDRemoteSystemAuthorizationKindFilter`</span></span> 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="8a19d-106">承認の種類に基づいてリモートシステムをフィルター処理するために使用されるクラス。</span><span class="sxs-lookup"><span data-stu-id="8a19d-106">A class used to filter remote systems based on authorization type.</span></span>

## <a name="properties"></a><span data-ttu-id="8a19d-107">Properties</span><span class="sxs-lookup"><span data-stu-id="8a19d-107">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="8a19d-108">kind</span><span class="sxs-lookup"><span data-stu-id="8a19d-108">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

<span data-ttu-id="8a19d-109">フィルター処理の対象となる承認の種類。</span><span class="sxs-lookup"><span data-stu-id="8a19d-109">The authorization type to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="8a19d-110">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="8a19d-110">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="8a19d-111">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="8a19d-111">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="8a19d-112">MCDRemoteSystemAuthorizationKind でフィルター処理された、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8a19d-112">A new instance of this class filtered on MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8a19d-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a19d-113">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="8a19d-114">フィルター処理の対象となる承認の種類。</span><span class="sxs-lookup"><span data-stu-id="8a19d-114">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="8a19d-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a19d-115">Returns</span></span>
<span data-ttu-id="8a19d-116">指定された承認フィルターを持つ MCDRemoteSystemAuthorizationKindFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8a19d-116">Returns an MCDRemoteSystemAuthorizationKindFilter object with the provided authorization filter.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="8a19d-117">initWithKind</span><span class="sxs-lookup"><span data-stu-id="8a19d-117">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="8a19d-118">MCDRemoteSystemAuthorizationKind を持つこのクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8a19d-118">A new instance of this class with MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8a19d-119">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a19d-119">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="8a19d-120">フィルター処理の対象となる承認の種類。</span><span class="sxs-lookup"><span data-stu-id="8a19d-120">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="8a19d-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a19d-121">Returns</span></span>
<span data-ttu-id="8a19d-122">AuthorizationKind で初期化された MCDRemoteSystemAuthorizationKindFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8a19d-122">Returns an MCDRemoteSystemAuthorizationKindFilter object initialized with the authorizationKind.</span></span>