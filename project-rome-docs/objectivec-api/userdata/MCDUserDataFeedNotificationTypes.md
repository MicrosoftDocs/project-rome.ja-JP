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
# <a name="class-mcduserdatafeednotificationtypes"></a><span data-ttu-id="5f3d9-105">講義 `MCDUserDataFeedNotificationTypes`</span><span class="sxs-lookup"><span data-stu-id="5f3d9-105">class `MCDUserDataFeedNotificationTypes`</span></span>

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

<span data-ttu-id="5f3d9-106">このクラスは、MCDUserDataFeedSyncScope の有効な通知の種類を提供します。</span><span class="sxs-lookup"><span data-stu-id="5f3d9-106">This class provides the valid notification types for MCDUserDataFeedSyncScope.notificationType.</span></span>


## <a name="properties"></a><span data-ttu-id="5f3d9-107">Properties</span><span class="sxs-lookup"><span data-stu-id="5f3d9-107">Properties</span></span>

### <a name="notificationwithpayload"></a><span data-ttu-id="5f3d9-108">notificationWithPayload</span><span class="sxs-lookup"><span data-stu-id="5f3d9-108">notificationWithPayload</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

<span data-ttu-id="5f3d9-109">受信プッシュ通知を表します。</span><span class="sxs-lookup"><span data-stu-id="5f3d9-109">Represents the incoming push notifications.</span></span>  <span data-ttu-id="5f3d9-110">ドメイン/サーバーの制限以外のプッシュ通知には、何も行われません。</span><span class="sxs-lookup"><span data-stu-id="5f3d9-110">There are no rescrictions to push notifications other than domain/server restrictions.</span></span>

### <a name="notificationonly"></a><span data-ttu-id="5f3d9-111">notificationOnly</span><span class="sxs-lookup"><span data-stu-id="5f3d9-111">notificationOnly</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

<span data-ttu-id="5f3d9-112">プッシュ通知にデータが含まれていてもデータを受信するようにシステムに指示するだけで、すべてのプッシュ通知を通知に降格します。</span><span class="sxs-lookup"><span data-stu-id="5f3d9-112">Demote all push notifications to a notification only telling the system to sync to receive the data, even if the data could be contained in the push notification.</span></span>


### <a name="nonotification"></a><span data-ttu-id="5f3d9-113">noNotification</span><span class="sxs-lookup"><span data-stu-id="5f3d9-113">noNotification</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

<span data-ttu-id="5f3d9-114">新しいユーザーデータの通知を禁止する、UserDataFeed が呼び出されたとき、または他の方法でサーバーと対話するときに、新しいデータのみを受信する</span><span class="sxs-lookup"><span data-stu-id="5f3d9-114">Prevent any notifications for new user data, only receive new data when UserDataFeed.startSync is called, or when interacting with the server in other ways</span></span>
