---
title: MCDAppServiceRequestReceivedEventArgs
description: MCDAppServiceRequestReceivedEventArgs クラスについて説明します。 このクラスには、"要求を受信しました" イベントに関連付けられたデータが含まれています。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 9a4a64ae163a0cc553196914da2f42d8d32e6ade
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760766"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a><span data-ttu-id="88cd1-105">講義 `MCDAppServiceRequestReceivedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="88cd1-105">class `MCDAppServiceRequestReceivedEventArgs`</span></span> 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
<span data-ttu-id="88cd1-106">"要求を受信しました" イベントに関連付けられたデータを格納します。</span><span class="sxs-lookup"><span data-stu-id="88cd1-106">Contains data associated with a "request received" event.</span></span>

## <a name="properties"></a><span data-ttu-id="88cd1-107">Properties</span><span class="sxs-lookup"><span data-stu-id="88cd1-107">Properties</span></span>

### <a name="request"></a><span data-ttu-id="88cd1-108">request</span><span class="sxs-lookup"><span data-stu-id="88cd1-108">request</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

<span data-ttu-id="88cd1-109">リモートデバイスによって送信された要求。</span><span class="sxs-lookup"><span data-stu-id="88cd1-109">The request sent by the remote device.</span></span>