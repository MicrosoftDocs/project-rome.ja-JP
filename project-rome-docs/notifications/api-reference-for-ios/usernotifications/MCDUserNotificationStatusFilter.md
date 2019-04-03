---
title: MCDUserNotificationStatusFilter
description: 通知のリーダーを作成するときに、読み取り状態フィルターを示す値が含まれています。 のみ読み取りをアプリがすべての通知を受信するかどうかを指定しますまたは、未読のものだけです。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909144"
---
# <a name="enum-mcdusernotificationstatusfilter"></a>列挙型 `MCDUserNotificationStatusFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

通知のリーダーを作成するときに、読み取り状態フィルターを示す値が含まれています。 のみ読み取りをアプリがすべての通知を受信するかどうかを指定しますまたは、未読のものだけです。 

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusFilterAny | 0| 状態の値に関係なくすべての通知が含まれます。 |
|   MCDUserNotificationStatusFilterActive |1| 接続されているデバイス プラットフォームの通知のストアでアクティブ化された永続化を通知が含まれます。 |
|   MCDUserNotificationStatusFilterDeleted | 2| 削除済みの通知のみが含まれます。|