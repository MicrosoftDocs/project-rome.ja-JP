---
title: MCDAppServiceClosedEventArgs
description: MCDAppServiceConnection が閉じられたことを通知し、終了イベントの背後にある理由を指定して MCDAppServiceConnection.serviceClosed によって返されます。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: a115ea4cc753efac445a466dbdfbfb14bf184370
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801294"
---
# <a name="class-mcdappserviceclosedeventargs"></a><span data-ttu-id="2e19d-104">クラス `MCDAppServiceClosedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="2e19d-104">class `MCDAppServiceClosedEventArgs`</span></span> 

```
@interface MCDAppServiceClosedEventArgs : NSObject
```  

<span data-ttu-id="2e19d-105">MCDAppServiceConnection が閉じられたことを通知し、終了イベントの背後にある理由を指定して MCDAppServiceConnection.serviceClosed によって返されます。</span><span class="sxs-lookup"><span data-stu-id="2e19d-105">Returned by MCDAppServiceConnection.serviceClosed to inform that the MCDAppServiceConnection has been closed and provide a reason behind the close event.</span></span>

## <a name="properties"></a><span data-ttu-id="2e19d-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2e19d-106">Properties</span></span>

### <a name="status"></a><span data-ttu-id="2e19d-107">status</span><span class="sxs-lookup"><span data-stu-id="2e19d-107">status</span></span>
`@property(nonatomic, readonly) MCDAppServiceClosedStatus status;`

<span data-ttu-id="2e19d-108">App service の終了のステータス。</span><span class="sxs-lookup"><span data-stu-id="2e19d-108">The status of how the app service closed.</span></span>