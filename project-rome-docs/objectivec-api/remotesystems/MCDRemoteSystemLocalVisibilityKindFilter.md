---
title: MCDRemoteSystemLocalVisibilityKindFilter
description: リモート システムの探索時に、ローカル (呼び出し) アプリケーションの表示優先順位を設定するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: b54614c1ee0a820e605df05768c164d07a5a9464
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909574"
---
# <a name="class-mcdremotesystemlocalvisibilitykindfilter"></a><span data-ttu-id="2775c-104">クラス `MCDRemoteSystemLocalVisibilityKindFilter`</span><span class="sxs-lookup"><span data-stu-id="2775c-104">class `MCDRemoteSystemLocalVisibilityKindFilter`</span></span> 

```
@interface MCDRemoteSystemLocalVisibilityKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="2775c-105">リモート システムの探索時に、ローカル (呼び出し) アプリケーションの表示優先順位を設定するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="2775c-105">A class used to set the local (calling) application visibility preference when discovering remote systems.</span></span>

## <a name="properties"></a><span data-ttu-id="2775c-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2775c-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="2775c-107">種類</span><span class="sxs-lookup"><span data-stu-id="2775c-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemLocalVisibilityKind kind;`

<span data-ttu-id="2775c-108">フィルター処理の可視性の設定。</span><span class="sxs-lookup"><span data-stu-id="2775c-108">The visibility setting to filter with.</span></span>

## <a name="constructors"></a><span data-ttu-id="2775c-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="2775c-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="2775c-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="2775c-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="2775c-111">作成して、このクラスのインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="2775c-111">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="2775c-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2775c-112">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="2775c-113">フィルターにローカル アプリの可視性の設定を示す MCDRemoteSystemLocalVisibilityKind 値。</span><span class="sxs-lookup"><span data-stu-id="2775c-113">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="2775c-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="2775c-114">Returns</span></span>
<span data-ttu-id="2775c-115">種類でフィルター処理された MCDRemoteSystemLocalVisibilityKind オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="2775c-115">Returns an MCDRemoteSystemLocalVisibilityKind object filtered by kind.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="2775c-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="2775c-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="2775c-117">作成して、このクラスのインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="2775c-117">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="2775c-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2775c-118">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="2775c-119">フィルターにローカル アプリの可視性の設定を示す MCDRemoteSystemLocalVisibilityKind 値。</span><span class="sxs-lookup"><span data-stu-id="2775c-119">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="2775c-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="2775c-120">Returns</span></span>
<span data-ttu-id="2775c-121">種類で初期化 MCDRemoteSystemLocalVisibilityKind オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="2775c-121">Returns an MCDRemoteSystemLocalVisibilityKind object initialized with kind.</span></span>