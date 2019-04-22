---
title: MCDUserDataFeedNotificationTypes
description: このクラスは、通知の種類を提供する担当
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 49f13fd2dbb13c439993f79a2b7275d4a705826a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801145"
---
# <a name="class-mcduserdatafeednotificationtypes"></a>クラス `MCDUserDataFeedNotificationTypes`

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

このクラスは、MCDUserDataFeedSyncScope.notificationType 有効な通知の種類を提供します。


## <a name="properties"></a>プロパティ

### <a name="notificationwithpayload"></a>notificationWithPayload
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

受信したプッシュ通知を表します。  ドメイン/サーバー制限以外のプッシュ通知を rescrictions はありません。

### <a name="notificationonly"></a>notificationOnly
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

場合でも、データがプッシュ通知に含まれている可能性がありますが、データを受信する同期のみをシステムに伝える通知にすべてのプッシュ通知を降格します。


### <a name="nonotification"></a>noNotification
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

新しいユーザー データの通知を防ぐため、UserDataFeed.startSync が呼び出されたときに、またはその他の方法でサーバーと対話するときに新しいデータの受信のみ
