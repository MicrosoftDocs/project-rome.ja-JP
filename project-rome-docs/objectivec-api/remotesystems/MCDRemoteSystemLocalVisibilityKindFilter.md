---
title: MCDRemoteSystemLocalVisibilityKindFilter
description: リモート システムの探索時に、ローカル (呼び出し) アプリケーションの表示優先順位を設定するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: b54614c1ee0a820e605df05768c164d07a5a9464
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800674"
---
# <a name="class-mcdremotesystemlocalvisibilitykindfilter"></a><span data-ttu-id="8ffae-104">クラス `MCDRemoteSystemLocalVisibilityKindFilter`</span><span class="sxs-lookup"><span data-stu-id="8ffae-104">class `MCDRemoteSystemLocalVisibilityKindFilter`</span></span> 

```
@interface MCDRemoteSystemLocalVisibilityKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="8ffae-105">リモート システムの探索時に、ローカル (呼び出し) アプリケーションの表示優先順位を設定するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="8ffae-105">A class used to set the local (calling) application visibility preference when discovering remote systems.</span></span>

## <a name="properties"></a><span data-ttu-id="8ffae-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8ffae-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="8ffae-107">種類</span><span class="sxs-lookup"><span data-stu-id="8ffae-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemLocalVisibilityKind kind;`

<span data-ttu-id="8ffae-108">フィルター処理の可視性の設定。</span><span class="sxs-lookup"><span data-stu-id="8ffae-108">The visibility setting to filter with.</span></span>

## <a name="constructors"></a><span data-ttu-id="8ffae-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="8ffae-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="8ffae-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="8ffae-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="8ffae-111">作成して、このクラスのインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="8ffae-111">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8ffae-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ffae-112">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="8ffae-113">フィルターにローカル アプリの可視性の設定を示す MCDRemoteSystemLocalVisibilityKind 値。</span><span class="sxs-lookup"><span data-stu-id="8ffae-113">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="8ffae-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="8ffae-114">Returns</span></span>
<span data-ttu-id="8ffae-115">種類でフィルター処理された MCDRemoteSystemLocalVisibilityKind オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8ffae-115">Returns an MCDRemoteSystemLocalVisibilityKind object filtered by kind.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="8ffae-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="8ffae-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="8ffae-117">作成して、このクラスのインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="8ffae-117">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8ffae-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ffae-118">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="8ffae-119">フィルターにローカル アプリの可視性の設定を示す MCDRemoteSystemLocalVisibilityKind 値。</span><span class="sxs-lookup"><span data-stu-id="8ffae-119">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="8ffae-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="8ffae-120">Returns</span></span>
<span data-ttu-id="8ffae-121">種類で初期化 MCDRemoteSystemLocalVisibilityKind オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8ffae-121">Returns an MCDRemoteSystemLocalVisibilityKind object initialized with kind.</span></span>