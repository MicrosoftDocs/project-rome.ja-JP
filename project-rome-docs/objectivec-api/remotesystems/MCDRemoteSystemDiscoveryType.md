---
title: MCDRemoteSystemDiscoveryType
description: 含むリモート システムを記述する値が検出されることができます。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: dc94b92311cb666fd2ffd3949b3d4d66a49e6e5b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800504"
---
# <a name="enum-mcdremotesystemdiscoverytype"></a><span data-ttu-id="a1ef8-104">列挙型 `MCDRemoteSystemDiscoveryType`</span><span class="sxs-lookup"><span data-stu-id="a1ef8-104">enum `MCDRemoteSystemDiscoveryType`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemDiscoveryType)
```  

<span data-ttu-id="a1ef8-105">含むリモート システムを記述する値が検出されることができます。</span><span class="sxs-lookup"><span data-stu-id="a1ef8-105">Contains values that describe how remote systems are able to be discovered.</span></span> 

## <a name="fields"></a><span data-ttu-id="a1ef8-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="a1ef8-106">Fields</span></span>

| <span data-ttu-id="a1ef8-107">名前</span><span class="sxs-lookup"><span data-stu-id="a1ef8-107">Name</span></span>                              | <span data-ttu-id="a1ef8-108">値</span><span class="sxs-lookup"><span data-stu-id="a1ef8-108">Value</span></span> | <span data-ttu-id="a1ef8-109">説明</span><span class="sxs-lookup"><span data-stu-id="a1ef8-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="a1ef8-110">MCDRemoteSystemDiscoveryTypeAny</span><span class="sxs-lookup"><span data-stu-id="a1ef8-110">MCDRemoteSystemDiscoveryTypeAny</span></span>   | <span data-ttu-id="a1ef8-111">0</span><span class="sxs-lookup"><span data-stu-id="a1ef8-111">0</span></span>     | <span data-ttu-id="a1ef8-112">リモート システムでは、任意の接続を探索可能です。</span><span class="sxs-lookup"><span data-stu-id="a1ef8-112">Remote systems are discoverable through any connection.</span></span>  |
| <span data-ttu-id="a1ef8-113">MCDRemoteSystemDiscoveryTypeProximal</span><span class="sxs-lookup"><span data-stu-id="a1ef8-113">MCDRemoteSystemDiscoveryTypeProximal</span></span> | <span data-ttu-id="a1ef8-114">1</span><span class="sxs-lookup"><span data-stu-id="a1ef8-114">1</span></span>     | <span data-ttu-id="a1ef8-115">リモート システムは、ローカルなどの位接続検出のみ</span><span class="sxs-lookup"><span data-stu-id="a1ef8-115">Remote systems are only discoverable through a proximal connection, such as a local</span></span>
<span data-ttu-id="a1ef8-116">ネットワーク接続または Bluetooth 接続します。</span><span class="sxs-lookup"><span data-stu-id="a1ef8-116">network or Bluetooth connection.</span></span> |
| <span data-ttu-id="a1ef8-117">MCDRemoteSystemDiscoveryTypeCloud</span><span class="sxs-lookup"><span data-stu-id="a1ef8-117">MCDRemoteSystemDiscoveryTypeCloud</span></span> | <span data-ttu-id="a1ef8-118">2</span><span class="sxs-lookup"><span data-stu-id="a1ef8-118">2</span></span>     | <span data-ttu-id="a1ef8-119">リモート システムでは、クラウド接続検出のみです。</span><span class="sxs-lookup"><span data-stu-id="a1ef8-119">Remote systems are only discoverable through cloud connection.</span></span> |
| <span data-ttu-id="a1ef8-120">MCDRemoteSystemDiscoveryTypeSpatiallyProximal</span><span class="sxs-lookup"><span data-stu-id="a1ef8-120">MCDRemoteSystemDiscoveryTypeSpatiallyProximal</span></span> | <span data-ttu-id="a1ef8-121">3</span><span class="sxs-lookup"><span data-stu-id="a1ef8-121">3</span></span>     | <span data-ttu-id="a1ef8-122">リモート システムが、位接続を介してといる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1ef8-122">Remote systems are discoverable through a proximal connection and are expected to be</span></span>
<span data-ttu-id="a1ef8-123">(たとえば Bluetooth 範囲) でクライアント デバイス空間的に近い。</span><span class="sxs-lookup"><span data-stu-id="a1ef8-123">spatially near to the client device (in Bluetooth range, for example).</span></span>  |

