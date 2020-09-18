---
title: MCDRemoteSystemKinds
description: MCDRemoteSystemKinds クラスについて説明します。 このクラスには、リモートシステムデバイスの種類を表す文字列フィールドが含まれています。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 978188b1a17c1acdd257fdc97c64fd17b3a1f618
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760666"
---
# <a name="class-mcdremotesystemkinds"></a><span data-ttu-id="f1fc6-105">講義 `MCDRemoteSystemKinds`</span><span class="sxs-lookup"><span data-stu-id="f1fc6-105">class `MCDRemoteSystemKinds`</span></span> 

```
@interface MCDRemoteSystemKinds : NSObject
```

<span data-ttu-id="f1fc6-106">リモートシステムデバイスの種類を表す文字列フィールドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-106">Contains string fields that represent remote system device types.</span></span>

## <a name="properties"></a><span data-ttu-id="f1fc6-107">Properties</span><span class="sxs-lookup"><span data-stu-id="f1fc6-107">Properties</span></span>

### <a name="desktop"></a><span data-ttu-id="f1fc6-108">デスクトップ</span><span class="sxs-lookup"><span data-stu-id="f1fc6-108">desktop</span></span>
`@property(class, readonly, readonly, nonnull) NSString* desktop;`

<span data-ttu-id="f1fc6-109">デスクトップデバイスの種類の正規名。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-109">The canonical name for the desktop device type.</span></span>

### <a name="holographic"></a><span data-ttu-id="f1fc6-110">holographic</span><span class="sxs-lookup"><span data-stu-id="f1fc6-110">holographic</span></span>
`@property(class, readonly, readonly, nonnull) NSString* holographic;`

<span data-ttu-id="f1fc6-111">Holographic デバイスタイプの正規名。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-111">The canonical name for the holographic device type.</span></span>

### <a name="hub"></a><span data-ttu-id="f1fc6-112">ハブ</span><span class="sxs-lookup"><span data-stu-id="f1fc6-112">hub</span></span>
`@property(class, readonly, readonly, nonnull) NSString* hub;`

<span data-ttu-id="f1fc6-113">ハブデバイスタイプの正規名。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-113">The canonical name for the hub device type.</span></span>

### <a name="phone"></a><span data-ttu-id="f1fc6-114">phone</span><span class="sxs-lookup"><span data-stu-id="f1fc6-114">phone</span></span>
`@property(class, readonly, readonly, nonnull) NSString* phone;`

<span data-ttu-id="f1fc6-115">Phone デバイスタイプの正規名。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-115">The canonical name for the phone device type.</span></span>

### <a name="xbox"></a><span data-ttu-id="f1fc6-116">本体</span><span class="sxs-lookup"><span data-stu-id="f1fc6-116">xbox</span></span>
`@property(class, readonly, readonly, nonnull) NSString* xbox;`

<span data-ttu-id="f1fc6-117">Xbox デバイスタイプの正規名。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-117">The canonical name for the xbox device type.</span></span>

### <a name="laptop"></a><span data-ttu-id="f1fc6-118">本体</span><span class="sxs-lookup"><span data-stu-id="f1fc6-118">laptop</span></span>
`@property(class, readonly, readonly, nonnull) NSString* laptop;`

<span data-ttu-id="f1fc6-119">ラップトップデバイスの標準の名前。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-119">The canonical name for the laptop device type.</span></span>

> <span data-ttu-id="f1fc6-120">**注:** Surface Book を含むすべての Microsoft Surface デバイスは、タブレットデバイスと見なされます。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-120">**Note:** All Microsoft Surface devices, including the Surface Book, are considered tablet devices.</span></span>

### <a name="iot"></a><span data-ttu-id="f1fc6-121">iot</span><span class="sxs-lookup"><span data-stu-id="f1fc6-121">iot</span></span>
`@property(class, readonly, readonly, nonnull) NSString* iot;`

<span data-ttu-id="f1fc6-122">IoT デバイスの標準の名前。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-122">The canonical name for the IoT device type.</span></span>

### <a name="tablet"></a><span data-ttu-id="f1fc6-123">タブレット</span><span class="sxs-lookup"><span data-stu-id="f1fc6-123">tablet</span></span>
`@property(class, readonly, readonly, nonnull) NSString* tablet;`

<span data-ttu-id="f1fc6-124">タブレットデバイスの標準の名前。</span><span class="sxs-lookup"><span data-stu-id="f1fc6-124">The canonical name for the tablet device type.</span></span>
