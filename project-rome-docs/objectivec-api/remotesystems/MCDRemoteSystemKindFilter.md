---
title: MCDRemoteSystemKindFilter
description: リモート システムのデバイスの種類に基づいてフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 162e8f881b532fae50f6d301149b50c5ddf344b5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907264"
---
# <a name="class-mcdremotesystemkindfilter"></a><span data-ttu-id="0c11f-104">クラス `MCDRemoteSystemKindFilter`</span><span class="sxs-lookup"><span data-stu-id="0c11f-104">class `MCDRemoteSystemKindFilter`</span></span> 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="0c11f-105">リモート システムのデバイスの種類に基づいてフィルター処理するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="0c11f-105">A class used to filter remote systems based upon device kind.</span></span>

## <a name="properties"></a><span data-ttu-id="0c11f-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0c11f-106">Properties</span></span>

### <a name="kinds"></a><span data-ttu-id="0c11f-107">種類</span><span class="sxs-lookup"><span data-stu-id="0c11f-107">kinds</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

<span data-ttu-id="0c11f-108">フィルター処理するためのデバイスの種類を示す文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="0c11f-108">An array of strings indicating the kinds of device to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="0c11f-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="0c11f-109">Constructors</span></span>

### <a name="filterwithkinds"></a><span data-ttu-id="0c11f-110">filterWithKinds</span><span class="sxs-lookup"><span data-stu-id="0c11f-110">filterWithKinds</span></span>
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="0c11f-111">種類でフィルター処理するこのクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="0c11f-111">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="0c11f-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c11f-112">Parameters</span></span> 
* `kinds`

 <span data-ttu-id="0c11f-113">フィルター処理するためのデバイスの種類を示す文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="0c11f-113">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="0c11f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="0c11f-114">Returns</span></span>
<span data-ttu-id="0c11f-115">種類でフィルター処理された MCDRemoteSystemKindFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="0c11f-115">Returns an MCDRemoteSystemKindFilter object filtered with kinds.</span></span>

### <a name="initwithkinds"></a><span data-ttu-id="0c11f-116">initWithKinds</span><span class="sxs-lookup"><span data-stu-id="0c11f-116">initWithKinds</span></span>
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="0c11f-117">種類でフィルター処理するこのクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="0c11f-117">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="0c11f-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c11f-118">Parameters</span></span> 
* `kinds` 

<span data-ttu-id="0c11f-119">フィルター処理するためのデバイスの種類を示す文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="0c11f-119">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="0c11f-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="0c11f-120">Returns</span></span>
<span data-ttu-id="0c11f-121">種類で初期化 MCDRemoteSystemKindFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="0c11f-121">Returns an MCDRemoteSystemKindFilter object initialized with kinds.</span></span>