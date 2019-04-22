---
title: MCDRemoteSystemStatusTypeFilter
description: リモート システムの可用性の状態の種類に基づいてフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 201570c16a8eb9cf1a31e450b3408c8ab255fe1a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907124"
---
# <a name="class-mcdremotesystemstatustypefilter"></a><span data-ttu-id="61619-104">クラス `MCDRemoteSystemStatusTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="61619-104">class `MCDRemoteSystemStatusTypeFilter`</span></span>

```
@interface MCDRemoteSystemStatusTypeFilter : NSObject <MCDRemoteSystemFilter>
```

<span data-ttu-id="61619-105">リモート システムの可用性の状態の種類に基づいてフィルター処理するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="61619-105">A class used to filter remote systems based on availability status type.</span></span>

## <a name="properties"></a><span data-ttu-id="61619-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="61619-106">Properties</span></span>

### <a name="type"></a><span data-ttu-id="61619-107">type</span><span class="sxs-lookup"><span data-stu-id="61619-107">type</span></span>
<span data-ttu-id="61619-108">`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` このフィルターのインスタンスのリモート システムのステータスの種類です。</span><span class="sxs-lookup"><span data-stu-id="61619-108">`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` The remote system status type of this filter instance.</span></span>

## <a name="constructors"></a><span data-ttu-id="61619-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="61619-109">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="61619-110">filterWithType</span><span class="sxs-lookup"><span data-stu-id="61619-110">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a><span data-ttu-id="61619-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="61619-111">Parameters</span></span> 
* <span data-ttu-id="61619-112">`statusType` フィルター処理するための可用性ステータスの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="61619-112">`statusType` A value indicating the availability status type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="61619-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="61619-113">Returns</span></span>
<span data-ttu-id="61619-114">種類でフィルター処理 MCDRemoteSystemStatusTypeFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="61619-114">Returns an MCDRemoteSystemStatusTypeFilter object filtered by type.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="61619-115">initWithType</span><span class="sxs-lookup"><span data-stu-id="61619-115">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a><span data-ttu-id="61619-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="61619-116">Parameters</span></span> 
* `statusType` 

<span data-ttu-id="61619-117">フィルター処理するための可用性ステータスの種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="61619-117">A value indicating the availability status type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="61619-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="61619-118">Returns</span></span>
<span data-ttu-id="61619-119">型を使用して初期化 MCDRemoteSystemStatusTypeFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="61619-119">Returns an MCDRemoteSystemStatusTypeFilter object initialized with the type.</span></span>