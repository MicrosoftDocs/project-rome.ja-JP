---
title: MCDUserNotificationStatus
description: 通知を削除するかどうかを決定する値が含まれています。 削除済みの通知は、通知ストアでは引き続きとプラットフォームのクリーンアップが発生する前に、リーダーによって返されます。 これらの通知の通知のリーダーに表示されないようにするのには、対応するリーダー フィルター UserNotificationStatusFilter を適用できます。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907244"
---
# <a name="enum-mcdusernotificationstatus"></a>列挙型 `MCDUserNotificationStatus`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

通知を削除するかどうかを決定する値が含まれています。 削除済みの通知は、通知ストアでは引き続きとプラットフォームのクリーンアップが発生する前に、リーダーによって返されます。 これらの通知の通知のリーダーに表示されないようにするのには、対応するリーダー フィルター UserNotificationStatusFilter を適用できます。 

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusActive |0| 通知は、まだアクティブで接続されているデバイス プラットフォームのストア内で永続化されました。 |
|   MCDUserNotificationStatusDeleted | 1| 通知が削除されました。|