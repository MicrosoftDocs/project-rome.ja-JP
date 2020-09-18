---
title: MCDConnectedDevicesNotification
description: MCDConnectedDevicesNotification クラスについて説明します。 このクラスは、通知を処理した結果です。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: c05ac896113b8196d1dd3854a14ef5730552435f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761016"
---
# <a name="class-mcdconnecteddevicesnotification"></a><span data-ttu-id="d58be-105">講義 `MCDConnectedDevicesNotification`</span><span class="sxs-lookup"><span data-stu-id="d58be-105">class `MCDConnectedDevicesNotification`</span></span> 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
<span data-ttu-id="d58be-106">通知を処理した結果。</span><span class="sxs-lookup"><span data-stu-id="d58be-106">Result of processing a notification.</span></span>

## <a name="methods"></a><span data-ttu-id="d58be-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="d58be-107">Methods</span></span>

### <a name="tryparse"></a><span data-ttu-id="d58be-108"><C3></span><span class="sxs-lookup"><span data-stu-id="d58be-108">tryParse</span></span>

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

<span data-ttu-id="d58be-109">APNS 形式のマップから MCDConnectedDevicesNotification の解析を試みます。</span><span class="sxs-lookup"><span data-stu-id="d58be-109">Attempts to parse a MCDConnectedDevicesNotification from an APNS formatted map.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d58be-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d58be-110">Parameters</span></span> 
* `dictionary` 

<span data-ttu-id="d58be-111">処理のために APNS 通知から接続されたデバイスプラットフォームに受信したマップ。</span><span class="sxs-lookup"><span data-stu-id="d58be-111">The map received from the APNS notification to the Connected Devices platform for processing.</span></span>
