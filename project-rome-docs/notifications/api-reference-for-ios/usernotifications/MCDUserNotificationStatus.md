---
title: MCDUserNotificationStatus
description: 通知が削除されたかどうかを示す値を格納します。 削除された通知は通知ストアに残りますが、プラットフォームのクリーンアップが発生する前にリーダーによって返されます。 これらの通知が通知リーダーに表示されないように、対応するリーダーフィルター UserNotificationStatusFilter を適用できます。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800814"
---
# <a name="enum-mcdusernotificationstatus"></a>enum`MCDUserNotificationStatus`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

通知が削除されたかどうかを示す値を格納します。 削除された通知は通知ストアに残りますが、プラットフォームのクリーンアップが発生する前にリーダーによって返されます。 これらの通知が通知リーダーに表示されないように、対応するリーダーフィルター UserNotificationStatusFilter を適用できます。 

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusActive |0| 通知はまだアクティブであり、接続されているデバイスのプラットフォームストア内に保持されます。 |
|   MCDUserNotificationStatusDeleted | 1| 通知が削除されました。|