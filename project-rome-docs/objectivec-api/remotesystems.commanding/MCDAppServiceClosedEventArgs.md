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
# <a name="class-mcdappserviceclosedeventargs"></a>クラス `MCDAppServiceClosedEventArgs` 

```
@interface MCDAppServiceClosedEventArgs : NSObject
```  

MCDAppServiceConnection が閉じられたことを通知し、終了イベントの背後にある理由を指定して MCDAppServiceConnection.serviceClosed によって返されます。

## <a name="properties"></a>プロパティ

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDAppServiceClosedStatus status;`

App service の終了のステータス。