---
title: MCDRemoteSystemPlatformFilter
description: リモート システムが実行されている OS プラットフォームに基づくフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 1b82d7b3a1626489a83196bf949567b3ce7b94f0
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801224"
---
# <a name="class-mcdremotesystemplatformfilter"></a><span data-ttu-id="7af3f-104">クラス `MCDRemoteSystemPlatformFilter`</span><span class="sxs-lookup"><span data-stu-id="7af3f-104">class `MCDRemoteSystemPlatformFilter`</span></span> 

```
@interface MCDRemoteSystemPlatformFilter : NSObject<MCDRemoteSystemFilter> 
```  

<span data-ttu-id="7af3f-105">リモート システムが実行されている OS プラットフォームに基づくフィルター処理するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="7af3f-105">A class used to filter remote systems based on the OS platform they are running.</span></span>

## <a name="properties"></a><span data-ttu-id="7af3f-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7af3f-106">Properties</span></span>

### <a name="platform"></a><span data-ttu-id="7af3f-107">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="7af3f-107">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="7af3f-108">フィルター処理するためのプラットフォームを示す MCDRemoteSystemPlatform 値。</span><span class="sxs-lookup"><span data-stu-id="7af3f-108">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="7af3f-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="7af3f-109">Constructors</span></span>

### <a name="filterwithplatform"></a><span data-ttu-id="7af3f-110">filterWithPlatform</span><span class="sxs-lookup"><span data-stu-id="7af3f-110">filterWithPlatform</span></span>
`+ (nullable instancetype)filterWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a><span data-ttu-id="7af3f-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7af3f-111">Parameters</span></span> 
* `platform` 

<span data-ttu-id="7af3f-112">フィルター処理するためのプラットフォームを示す MCDRemoteSystemPlatform 値。</span><span class="sxs-lookup"><span data-stu-id="7af3f-112">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="7af3f-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="7af3f-113">Returns</span></span>
<span data-ttu-id="7af3f-114">プラットフォームでフィルター処理された MCDRemoteSystemPlatformFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="7af3f-114">Returns an MCDRemoteSystemPlatformFilter object filtered by platform.</span></span>

### <a name="initwithplatform"></a><span data-ttu-id="7af3f-115">initWithPlatform</span><span class="sxs-lookup"><span data-stu-id="7af3f-115">initWithPlatform</span></span>
`- (nullable instancetype)initWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a><span data-ttu-id="7af3f-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7af3f-116">Parameters</span></span> 
* `platform` 

<span data-ttu-id="7af3f-117">フィルター処理するためのプラットフォームを示す MCDRemoteSystemPlatform 値。</span><span class="sxs-lookup"><span data-stu-id="7af3f-117">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="7af3f-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="7af3f-118">Returns</span></span>
<span data-ttu-id="7af3f-119">プラットフォームでフィルターを使用した初期化 MCDRemoteSystemPlatformFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="7af3f-119">Returns an MCDRemoteSystemPlatformFilter object initialized with a filter by platform.</span></span>