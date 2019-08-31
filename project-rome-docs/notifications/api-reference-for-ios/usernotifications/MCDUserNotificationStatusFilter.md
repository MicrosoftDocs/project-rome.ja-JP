---
title: MCDUserNotificationStatusFilter
description: 通知リーダーを作成するときの読み取り状態フィルターを示す値を格納します。 これにより、アプリがすべての通知を受信するか、読み取り専用にするか、または未読のものだけを受信するかを決定します。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801494"
---
# <a name="enum-mcdusernotificationstatusfilter"></a>enum`MCDUserNotificationStatusFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

通知リーダーを作成するときの読み取り状態フィルターを示す値を格納します。 これにより、アプリがすべての通知を受信するか、読み取り専用にするか、または未読のものだけを受信するかを決定します。 

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusFilterAny | 0| 状態の値に関係なく、すべての通知を含めます。 |
|   MCDUserNotificationStatusFilterActive |1| 接続されているデバイスのプラットフォーム通知ストアにアクティブで永続化されている通知を含めます。 |
|   MCDUserNotificationStatusFilterDeleted | 2| 削除された通知のみを含めます。|