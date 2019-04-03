---
title: MCDConnectedDevicesNotification
description: 通知を処理の結果。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 2a60e2cab26c3d2df39314aa5b61a65de1529356
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908714"
---
# <a name="class-mcdconnecteddevicesnotification"></a><span data-ttu-id="b57a1-104">クラス `MCDConnectedDevicesNotification`</span><span class="sxs-lookup"><span data-stu-id="b57a1-104">class `MCDConnectedDevicesNotification`</span></span> 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
<span data-ttu-id="b57a1-105">通知を処理の結果。</span><span class="sxs-lookup"><span data-stu-id="b57a1-105">Result of processing a notification.</span></span>

## <a name="methods"></a><span data-ttu-id="b57a1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b57a1-106">Methods</span></span>

### <a name="tryparse"></a><span data-ttu-id="b57a1-107">tryParse</span><span class="sxs-lookup"><span data-stu-id="b57a1-107">tryParse</span></span>

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

<span data-ttu-id="b57a1-108">APNS からの MCDConnectedDevicesNotification を解析する試行は、マップを書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="b57a1-108">Attempts to parse a MCDConnectedDevicesNotification from an APNS formatted map.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b57a1-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b57a1-109">Parameters</span></span> 
* `dictionary` 

<span data-ttu-id="b57a1-110">処理のため、接続しているデバイス プラットフォームに APNS 通知を受信するマップです。</span><span class="sxs-lookup"><span data-stu-id="b57a1-110">The map received from the APNS notification to the Connected Devices platform for processing.</span></span>
