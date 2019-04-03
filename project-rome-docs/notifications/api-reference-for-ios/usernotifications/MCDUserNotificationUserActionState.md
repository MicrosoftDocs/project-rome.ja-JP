---
title: MCDUserNotificationUserActionState
description: 通知をユーザーが実行されるアクションを記述する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907784"
---
# <a name="enum-mcdusernotificationuseractionstate"></a>列挙型 `MCDUserNotificationUserActionState`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

通知をユーザーが実行されるアクションを記述する値が含まれています。

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateNoInteraction |0| ユーザーは、任意のアクションを実行していません。|
|   MCDUserNotificationUserActionStateActivated|1|ユーザーは、通知をアクティブ化します。|
|   MCDUserNotificationUserActionStateDismissed|2| ユーザーが通知を閉じる。|
|   MCDUserNotificationUserActionStateSnoozed|3| ユーザーは、通知を再います。|
