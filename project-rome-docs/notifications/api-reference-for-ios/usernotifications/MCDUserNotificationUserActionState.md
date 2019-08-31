---
title: MCDUserNotificationUserActionState
description: ユーザーが通知に対して行ったアクションを記述する値を格納します。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800804"
---
# <a name="enum-mcdusernotificationuseractionstate"></a>enum`MCDUserNotificationUserActionState`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

ユーザーが通知に対して行ったアクションを記述する値を格納します。

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateNoInteraction |0| ユーザーは何の操作も行っていません。|
|   MCDUserNotificationUserActionStateActivated|1|ユーザーが通知をアクティブ化しました。|
|   MCDUserNotificationUserActionStateDismissed|2| ユーザーが通知を閉じました。|
|   MCDUserNotificationUserActionStateSnoozed|3| ユーザーが通知を再通知しました。|
