---
title: MCDUserDataFeedNotificationTypes
description: このクラスは、通知の種類を提供する担当
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 49f13fd2dbb13c439993f79a2b7275d4a705826a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908914"
---
# <a name="class-mcduserdatafeednotificationtypes"></a><span data-ttu-id="13733-104">クラス `MCDUserDataFeedNotificationTypes`</span><span class="sxs-lookup"><span data-stu-id="13733-104">class `MCDUserDataFeedNotificationTypes`</span></span>

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

<span data-ttu-id="13733-105">このクラスは、MCDUserDataFeedSyncScope.notificationType 有効な通知の種類を提供します。</span><span class="sxs-lookup"><span data-stu-id="13733-105">This class provides the valid notification types for MCDUserDataFeedSyncScope.notificationType.</span></span>


## <a name="properties"></a><span data-ttu-id="13733-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="13733-106">Properties</span></span>

### <a name="notificationwithpayload"></a><span data-ttu-id="13733-107">notificationWithPayload</span><span class="sxs-lookup"><span data-stu-id="13733-107">notificationWithPayload</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

<span data-ttu-id="13733-108">受信したプッシュ通知を表します。</span><span class="sxs-lookup"><span data-stu-id="13733-108">Represents the incoming push notifications.</span></span>  <span data-ttu-id="13733-109">ドメイン/サーバー制限以外のプッシュ通知を rescrictions はありません。</span><span class="sxs-lookup"><span data-stu-id="13733-109">There are no rescrictions to push notifications other than domain/server restrictions.</span></span>

### <a name="notificationonly"></a><span data-ttu-id="13733-110">notificationOnly</span><span class="sxs-lookup"><span data-stu-id="13733-110">notificationOnly</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

<span data-ttu-id="13733-111">場合でも、データがプッシュ通知に含まれている可能性がありますが、データを受信する同期のみをシステムに伝える通知にすべてのプッシュ通知を降格します。</span><span class="sxs-lookup"><span data-stu-id="13733-111">Demote all push notifications to a notification only telling the system to sync to receive the data, even if the data could be contained in the push notification.</span></span>


### <a name="nonotification"></a><span data-ttu-id="13733-112">noNotification</span><span class="sxs-lookup"><span data-stu-id="13733-112">noNotification</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

<span data-ttu-id="13733-113">新しいユーザー データの通知を防ぐため、UserDataFeed.startSync が呼び出されたときに、またはその他の方法でサーバーと対話するときに新しいデータの受信のみ</span><span class="sxs-lookup"><span data-stu-id="13733-113">Prevent any notifications for new user data, only receive new data when UserDataFeed.startSync is called, or when interacting with the server in other ways</span></span>