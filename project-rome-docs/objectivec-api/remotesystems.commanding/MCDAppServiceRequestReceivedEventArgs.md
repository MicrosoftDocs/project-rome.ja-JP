---
title: MCDAppServiceRequestReceivedEventArgs
description: 「要求を受信」のイベントに関連付けられたデータが含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5fa7a3b2742d5ecacd7c6a90e39e86f4c46f2218
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800644"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a><span data-ttu-id="0037e-104">クラス `MCDAppServiceRequestReceivedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="0037e-104">class `MCDAppServiceRequestReceivedEventArgs`</span></span> 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
<span data-ttu-id="0037e-105">「要求を受信」のイベントに関連付けられたデータが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0037e-105">Contains data associated with a "request received" event.</span></span>

## <a name="properties"></a><span data-ttu-id="0037e-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0037e-106">Properties</span></span>

### <a name="request"></a><span data-ttu-id="0037e-107">要求</span><span class="sxs-lookup"><span data-stu-id="0037e-107">request</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

<span data-ttu-id="0037e-108">リモート デバイスによって送信される要求。</span><span class="sxs-lookup"><span data-stu-id="0037e-108">The request sent by the remote device.</span></span>