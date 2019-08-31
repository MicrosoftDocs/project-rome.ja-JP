---
title: MCDUserNotificationReadStateFilter
description: 通知を (フィルター処理された通知の取得のために) 読み取り状態で分類する値を格納します。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801344"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a>enum`MCDUserNotificationReadStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

通知を (フィルター処理された通知の取得のために) 読み取り状態で分類する値を格納します。

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|   MCDUserNotificationReadStateFilterAny | 0 | 読み取り状態に関係なく通知を含めます。|
|   MCDUserNotificationReadStateFilterUnread | 1 | まだ読み込まれていない通知を含めます。|
|   MCDUserNotificationReadStateFilterRead | 2 | 読み取られた通知を含めます。 |