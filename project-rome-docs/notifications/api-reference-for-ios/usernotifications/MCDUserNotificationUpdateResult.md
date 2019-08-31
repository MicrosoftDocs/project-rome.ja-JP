---
title: MCDUserNotificationUpdateResult
description: このクラスは、通知を更新しようとしたときの状態を表します。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 814d4373c47c8af00d3e003f730db804f48c5fb0
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801484"
---
# <a name="class-mcdusernotificationupdateresult"></a>講義`MCDUserNotificationUpdateResult`

```
@interface MCDUserNotificationUpdateResult : NSObject
```

このクラスは、通知を更新しようとしたときの状態を表します。

## <a name="properties"></a>Properties

### <a name="notificationid"></a>notificationId
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`

通知の ID。

### <a name="succeeded"></a>succeeded
`@property(nonatomic, readonly) Succeeded succeeded;`

操作が成功したかどうか。 