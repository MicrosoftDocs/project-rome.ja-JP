---
title: MCDAppServiceClosedStatus
description: リモート アプリ サービスへの接続を閉じたを記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 9a56ee489175cb065fde281acb4ae8a345fb851b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907724"
---
# <a name="enum-mcdappserviceclosedstatus"></a>列挙型 `MCDAppServiceClosedStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceClosedStatus)
```

リモート アプリ サービスへの接続を閉じたを記述する値が含まれています。

|メンバー   |Value   |説明   |
|--------|-------|-------------|
|MCDAppServiceClosedStatusCompleted |0| App service のエンドポイントが正常に終了します。|
|MCDAppServiceClosedStatusCanceled |1| App service のエンドポイントは、クライアントまたはシステムによって終了されました。|
|MCDAppServiceClosedStatusResourceLimitsExceeded |2| エンドポイントは、リソースが不足したため、app service のエンドポイントが閉じられました。|
|MCDAppServiceClosedStatusUnknown |3| 不明なエラーが発生しました。|