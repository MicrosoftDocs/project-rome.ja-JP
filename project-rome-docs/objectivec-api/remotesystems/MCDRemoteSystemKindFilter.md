---
title: MCDRemoteSystemKindFilter
description: MCDRemoteSystemKindFilter クラスについて説明します。 このクラスは、デバイスの種類に基づいてリモートシステムをフィルター処理するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: eb0799fe3c2c9831c7963d2d062f39fbf458689e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760676"
---
# <a name="class-mcdremotesystemkindfilter"></a><span data-ttu-id="c9cf5-105">講義 `MCDRemoteSystemKindFilter`</span><span class="sxs-lookup"><span data-stu-id="c9cf5-105">class `MCDRemoteSystemKindFilter`</span></span> 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="c9cf5-106">デバイスの種類に基づいてリモートシステムをフィルター処理するために使用されるクラス。</span><span class="sxs-lookup"><span data-stu-id="c9cf5-106">A class used to filter remote systems based upon device kind.</span></span>

## <a name="properties"></a><span data-ttu-id="c9cf5-107">Properties</span><span class="sxs-lookup"><span data-stu-id="c9cf5-107">Properties</span></span>

### <a name="kinds"></a><span data-ttu-id="c9cf5-108">さまざま</span><span class="sxs-lookup"><span data-stu-id="c9cf5-108">kinds</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

<span data-ttu-id="c9cf5-109">フィルター処理の対象となるデバイスの種類を示す文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="c9cf5-109">An array of strings indicating the kinds of device to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="c9cf5-110">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="c9cf5-110">Constructors</span></span>

### <a name="filterwithkinds"></a><span data-ttu-id="c9cf5-111">filterWithKinds</span><span class="sxs-lookup"><span data-stu-id="c9cf5-111">filterWithKinds</span></span>
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="c9cf5-112">種類に基づいてフィルター処理された、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="c9cf5-112">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="c9cf5-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9cf5-113">Parameters</span></span> 
* `kinds`

 <span data-ttu-id="c9cf5-114">フィルター処理の対象となるデバイスの種類を示す文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="c9cf5-114">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="c9cf5-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="c9cf5-115">Returns</span></span>
<span data-ttu-id="c9cf5-116">種類を指定してフィルター処理された MCDRemoteSystemKindFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="c9cf5-116">Returns an MCDRemoteSystemKindFilter object filtered with kinds.</span></span>

### <a name="initwithkinds"></a><span data-ttu-id="c9cf5-117">initWithKinds</span><span class="sxs-lookup"><span data-stu-id="c9cf5-117">initWithKinds</span></span>
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="c9cf5-118">種類に基づいてフィルター処理された、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="c9cf5-118">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="c9cf5-119">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9cf5-119">Parameters</span></span> 
* `kinds` 

<span data-ttu-id="c9cf5-120">フィルター処理の対象となるデバイスの種類を示す文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="c9cf5-120">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="c9cf5-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="c9cf5-121">Returns</span></span>
<span data-ttu-id="c9cf5-122">種類で初期化された MCDRemoteSystemKindFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="c9cf5-122">Returns an MCDRemoteSystemKindFilter object initialized with kinds.</span></span>