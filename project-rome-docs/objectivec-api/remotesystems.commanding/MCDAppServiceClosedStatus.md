---
title: MCDAppServiceClosedStatus
description: リモート アプリ サービスへの接続を閉じたを記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 9a56ee489175cb065fde281acb4ae8a345fb851b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800774"
---
# <a name="enum-mcdappserviceclosedstatus"></a>列挙型 `MCDAppServiceClosedStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceClosedStatus)
```

リモート アプリ サービスへの接続を閉じたを記述する値が含まれています。

|Member   |値   |説明   |
|--------|-------|-------------|
|MCDAppServiceClosedStatusCompleted |0| App service のエンドポイントが正常に終了します。|
|MCDAppServiceClosedStatusCanceled |1| App service のエンドポイントは、クライアントまたはシステムによって終了されました。|
|MCDAppServiceClosedStatusResourceLimitsExceeded |2| エンドポイントは、リソースが不足したため、app service のエンドポイントが閉じられました。|
|MCDAppServiceClosedStatusUnknown |3| 不明なエラーが発生しました。|