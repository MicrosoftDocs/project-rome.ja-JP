---
title: MCDRemoteSystemAuthorizationKindFilter
description: リモート システムの承認の種類に基づいてフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: da68c7a0eacd2018332d5e2fe5c8e3c906f473f8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907644"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a><span data-ttu-id="6e165-104">クラス `MCDRemoteSystemAuthorizationKindFilter`</span><span class="sxs-lookup"><span data-stu-id="6e165-104">class `MCDRemoteSystemAuthorizationKindFilter`</span></span> 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="6e165-105">リモート システムの承認の種類に基づいてフィルター処理するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="6e165-105">A class used to filter remote systems based on authorization type.</span></span>

## <a name="properties"></a><span data-ttu-id="6e165-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6e165-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="6e165-107">種類</span><span class="sxs-lookup"><span data-stu-id="6e165-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

<span data-ttu-id="6e165-108">承認の種類をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="6e165-108">The authorization type to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="6e165-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="6e165-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="6e165-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="6e165-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="6e165-111">MCDRemoteSystemAuthorizationKind でフィルター処理するこのクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6e165-111">A new instance of this class filtered on MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="6e165-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e165-112">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="6e165-113">承認の種類をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="6e165-113">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="6e165-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e165-114">Returns</span></span>
<span data-ttu-id="6e165-115">指定された承認フィルターを使用して MCDRemoteSystemAuthorizationKindFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="6e165-115">Returns an MCDRemoteSystemAuthorizationKindFilter object with the provided authorization filter.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="6e165-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="6e165-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="6e165-117">MCDRemoteSystemAuthorizationKind でこのクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6e165-117">A new instance of this class with MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="6e165-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e165-118">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="6e165-119">承認の種類をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="6e165-119">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="6e165-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e165-120">Returns</span></span>
<span data-ttu-id="6e165-121">AuthorizationKind 初期化 MCDRemoteSystemAuthorizationKindFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="6e165-121">Returns an MCDRemoteSystemAuthorizationKindFilter object initialized with the authorizationKind.</span></span>