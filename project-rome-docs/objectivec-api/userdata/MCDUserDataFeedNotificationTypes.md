---
title: MCDUserDataFeedNotificationTypes
description: MCDUserDataFeedNotificationTypes クラスについて説明します。 このクラスは、通知の種類を提供します。
keywords: microsoft、windows、ユーザーアクティビティ、iOS、iPhone、、接続デバイス、プロジェクトローマ
ms.openlocfilehash: a9bb9b41309e32a429926c52769da9bc767ef5bc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760986"
---
# <a name="class-mcduserdatafeednotificationtypes"></a>講義 `MCDUserDataFeedNotificationTypes`

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

このクラスは、MCDUserDataFeedSyncScope の有効な通知の種類を提供します。


## <a name="properties"></a>Properties

### <a name="notificationwithpayload"></a>notificationWithPayload
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

受信プッシュ通知を表します。  ドメイン/サーバーの制限以外のプッシュ通知には、何も行われません。

### <a name="notificationonly"></a>notificationOnly
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

プッシュ通知にデータが含まれていてもデータを受信するようにシステムに指示するだけで、すべてのプッシュ通知を通知に降格します。


### <a name="nonotification"></a>noNotification
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

新しいユーザーデータの通知を禁止する、UserDataFeed が呼び出されたとき、または他の方法でサーバーと対話するときに、新しいデータのみを受信する
