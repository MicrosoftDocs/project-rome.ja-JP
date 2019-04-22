---
title: MCDAppServiceInfo
description: このクラスには、リモート デバイスまたはアプリケーションに属している app service について説明します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5cb01d664a07653387b523eeec68ebd50bbc2798
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801164"
---
# <a name="class-mcdappserviceinfo"></a><span data-ttu-id="522d5-104">クラス `MCDAppServiceInfo`</span><span class="sxs-lookup"><span data-stu-id="522d5-104">class `MCDAppServiceInfo`</span></span> 

```
@interface MCDAppServiceInfo : NSObject<NSCopying>
```  

<span data-ttu-id="522d5-105">このクラスには、リモート デバイスまたはアプリケーションに属している app service について説明します。</span><span class="sxs-lookup"><span data-stu-id="522d5-105">This class describes an app service that belongs to a remote device or application.</span></span>

## <a name="properties"></a><span data-ttu-id="522d5-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="522d5-106">Properties</span></span>

### <a name="name"></a><span data-ttu-id="522d5-107">name</span><span class="sxs-lookup"><span data-stu-id="522d5-107">name</span></span>
`@property(nonatomic, readonly, nullable) NSString* name;`

<span data-ttu-id="522d5-108">記述されている app service の名前。</span><span class="sxs-lookup"><span data-stu-id="522d5-108">The name of the app service being described.</span></span>

### <a name="packageid"></a><span data-ttu-id="522d5-109">PackageId</span><span class="sxs-lookup"><span data-stu-id="522d5-109">packageId</span></span>
`@property(nonatomic, readonly, nullable) NSString* packageId;`

<span data-ttu-id="522d5-110">記述されている app service のパッケージ ID。</span><span class="sxs-lookup"><span data-stu-id="522d5-110">The package ID of the app service being described.</span></span>

## <a name="constructors"></a><span data-ttu-id="522d5-111">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="522d5-111">Constructors</span></span>

### <a name="infowithname"></a><span data-ttu-id="522d5-112">infoWithName</span><span class="sxs-lookup"><span data-stu-id="522d5-112">infoWithName</span></span>
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name;`

<span data-ttu-id="522d5-113">情報と app service の名前を持つクラスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="522d5-113">Initialize the class with information and name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="522d5-114">パラメーター</span><span class="sxs-lookup"><span data-stu-id="522d5-114">Parameters</span></span> 
* `name` 

<span data-ttu-id="522d5-115">記述されている app service の名前。</span><span class="sxs-lookup"><span data-stu-id="522d5-115">The name of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="522d5-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="522d5-116">Returns</span></span>
<span data-ttu-id="522d5-117">指定された名前を含む MCDAppServiceInfo オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="522d5-117">Returns an MCDAppServiceInfo object containing the provided name.</span></span>

### <a name="initwithname"></a><span data-ttu-id="522d5-118">initWithName</span><span class="sxs-lookup"><span data-stu-id="522d5-118">initWithName</span></span>
`- (nullable instancetype)initWithName:(nonnull NSString*)name;`

<span data-ttu-id="522d5-119">App service の名前のクラスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="522d5-119">Initialize the class with the name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="522d5-120">パラメーター</span><span class="sxs-lookup"><span data-stu-id="522d5-120">Parameters</span></span> 
* `name` 

<span data-ttu-id="522d5-121">記述されている app service の名前。</span><span class="sxs-lookup"><span data-stu-id="522d5-121">The name of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="522d5-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="522d5-122">Returns</span></span>
<span data-ttu-id="522d5-123">指定された名前を使用して初期化 MCDAppServiceInfo オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="522d5-123">Returns an MCDAppServiceInfo object initialized with the provided name.</span></span>

### <a name="infowithname"></a><span data-ttu-id="522d5-124">infoWithName</span><span class="sxs-lookup"><span data-stu-id="522d5-124">infoWithName</span></span>
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

<span data-ttu-id="522d5-125">情報と app service の名前を持つクラスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="522d5-125">Initialize the class with information and name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="522d5-126">パラメーター</span><span class="sxs-lookup"><span data-stu-id="522d5-126">Parameters</span></span> 
* `name` 

<span data-ttu-id="522d5-127">記述されている app service の名前。</span><span class="sxs-lookup"><span data-stu-id="522d5-127">The name of the app service being described.</span></span>

* `packageId` 

<span data-ttu-id="522d5-128">記述されている app service のパッケージ ID。</span><span class="sxs-lookup"><span data-stu-id="522d5-128">The package ID of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="522d5-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="522d5-129">Returns</span></span>
<span data-ttu-id="522d5-130">指定された名前を含む MCDAppServiceInfo オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="522d5-130">Returns an MCDAppServiceInfo object containing the provided name.</span></span>

### <a name="initwithname"></a><span data-ttu-id="522d5-131">initWithName</span><span class="sxs-lookup"><span data-stu-id="522d5-131">initWithName</span></span>
`- (nullable instancetype)initWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

<span data-ttu-id="522d5-132">App service の名前のクラスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="522d5-132">Initialize the class with the name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="522d5-133">パラメーター</span><span class="sxs-lookup"><span data-stu-id="522d5-133">Parameters</span></span> 
* `name` 

<span data-ttu-id="522d5-134">記述されている app service の名前。</span><span class="sxs-lookup"><span data-stu-id="522d5-134">The name of the app service being described.</span></span>

* `packageId` 

<span data-ttu-id="522d5-135">記述されている app service のパッケージ ID。</span><span class="sxs-lookup"><span data-stu-id="522d5-135">The package ID of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="522d5-136">戻り値</span><span class="sxs-lookup"><span data-stu-id="522d5-136">Returns</span></span>
<span data-ttu-id="522d5-137">指定された名前を使用して初期化 MCDAppServiceInfo オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="522d5-137">Returns an MCDAppServiceInfo object initialized with the provided name.</span></span>
