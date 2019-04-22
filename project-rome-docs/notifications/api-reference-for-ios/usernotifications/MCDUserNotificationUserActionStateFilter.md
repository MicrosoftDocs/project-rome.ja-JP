---
title: MCDUserNotificationUserActionStateFilter
description: 分類 (フィルター選択された通知の取得) するためのユーザー アクションの状態を通知する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800564"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a>列挙型 `MCDUserNotificationUserActionStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

分類 (フィルター選択された通知の取得) するためのユーザー アクションの状態を通知する値が含まれています。

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateFilterAny|0| ユーザー アクションの状態に関係なく通知が含まれます。|
|   MCDUserNotificationUserActionStateFilterNoInteraction |1| ユーザーが処理済みいない通知が含まれます。|
|   MCDUserNotificationUserActionStateFilterActivated|2| ユーザーがアクティブ化されている通知が含まれます。|
|   MCDUserNotificationUserActionStateFilterDismissed|3| ユーザーが既に閉じられている通知が含まれます。|
|   MCDUserNotificationUserActionStateFilterSnoozed|4| ユーザーによって再されている通知が含まれます。|