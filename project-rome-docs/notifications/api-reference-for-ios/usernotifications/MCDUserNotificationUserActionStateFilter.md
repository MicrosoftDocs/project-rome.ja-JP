---
title: MCDUserNotificationUserActionStateFilter
description: ユーザーアクションの状態 (フィルター処理された通知の取得用) で通知を分類する値が含まれます。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800564"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a>enum`MCDUserNotificationUserActionStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

ユーザーアクションの状態 (フィルター処理された通知の取得用) で通知を分類する値が含まれます。

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateFilterAny|0| ユーザーの操作の状態に関係なく通知を含めます。|
|   MCDUserNotificationUserActionStateFilterNoInteraction |1| ユーザーによって処理されていない通知を含めます。|
|   MCDUserNotificationUserActionStateFilterActivated|2| ユーザーによってアクティブ化された通知を含めます。|
|   MCDUserNotificationUserActionStateFilterDismissed|3| ユーザーによって破棄された通知を含めます。|
|   MCDUserNotificationUserActionStateFilterSnoozed|4| ユーザーによって再通知された通知を含めます。|