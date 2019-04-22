---
title: MCDRemoteSystemDiscoveryTypeFilter
description: リモート システムの検出の種類に基づいてフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 8054d378f203d5cde29af6b4452cc03e15e24828
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907524"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a><span data-ttu-id="d3662-104">クラス `MCDRemoteSystemDiscoveryTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="d3662-104">class `MCDRemoteSystemDiscoveryTypeFilter`</span></span> 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="d3662-105">リモート システムの検出の種類に基づいてフィルター処理するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="d3662-105">A class used to filter remote systems based upon discovery type.</span></span>

## <a name="properties"></a><span data-ttu-id="d3662-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d3662-106">Properties</span></span>

### <a name="type"></a><span data-ttu-id="d3662-107">type</span><span class="sxs-lookup"><span data-stu-id="d3662-107">type</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

<span data-ttu-id="d3662-108">検出の種類をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="d3662-108">The discovery type to filter for.</span></span>

> <span data-ttu-id="d3662-109">注:Android では、接続されているデバイス プラットフォームでのみ使用できます Bluetooth Android 8.0 (Oreo) を実行しているシステムまたはそれ以降。</span><span class="sxs-lookup"><span data-stu-id="d3662-109">Note: On Android, the Connected Devices Platform can only use Bluetooth on systems running Android 8.0 (Oreo) or later.</span></span>

## <a name="constructors"></a><span data-ttu-id="d3662-110">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="d3662-110">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="d3662-111">filterWithType</span><span class="sxs-lookup"><span data-stu-id="d3662-111">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="d3662-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3662-112">Parameters</span></span> 
* <span data-ttu-id="d3662-113">`discoveryType` 検出の種類をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="d3662-113">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="d3662-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3662-114">Returns</span></span>
<span data-ttu-id="d3662-115">指定した型の値では、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d3662-115">A new instance of this class with the given type value.</span></span> <span data-ttu-id="d3662-116">値は、一度に複数のフィルターを適用するには、まとめて AND'ed を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d3662-116">Values can be AND'ed together to apply multiple filters at once.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="d3662-117">initWithType</span><span class="sxs-lookup"><span data-stu-id="d3662-117">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="d3662-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3662-118">Parameters</span></span> 
* <span data-ttu-id="d3662-119">`discoveryType` 検出の種類をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="d3662-119">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="d3662-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3662-120">Returns</span></span>
<span data-ttu-id="d3662-121">指定した型の値では、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="d3662-121">A new instance of this class with the given type value.</span></span> <span data-ttu-id="d3662-122">値は、一度に複数のフィルターを適用するには、まとめて AND'ed を指定できます。</span><span class="sxs-lookup"><span data-stu-id="d3662-122">Values can be AND'ed together to apply multiple filters at once.</span></span>