---
title: MCDUserNotificationReadStateFilter
description: (フィルター選択された通知の取得) の読み取りの状態が通知を分類する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801344"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a>列挙型 `MCDUserNotificationReadStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

(フィルター選択された通知の取得) の読み取りの状態が通知を分類する値が含まれています。

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationReadStateFilterAny | 0 | 読み取り状態に関係なく通知が含まれます。|
|   MCDUserNotificationReadStateFilterUnread | 1 | 未読の通知が含まれます。|
|   MCDUserNotificationReadStateFilterRead | 2 | 読み取られた通知が含まれます。 |