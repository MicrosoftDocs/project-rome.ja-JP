---
title: MCDUserNotificationUpdateResult
description: このクラスには、通知の更新の状態について説明します。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 814d4373c47c8af00d3e003f730db804f48c5fb0
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801484"
---
# <a name="class-mcdusernotificationupdateresult"></a><span data-ttu-id="9759b-104">クラス `MCDUserNotificationUpdateResult`</span><span class="sxs-lookup"><span data-stu-id="9759b-104">class `MCDUserNotificationUpdateResult`</span></span>

```
@interface MCDUserNotificationUpdateResult : NSObject
```

<span data-ttu-id="9759b-105">このクラスには、通知の更新の状態について説明します。</span><span class="sxs-lookup"><span data-stu-id="9759b-105">This class describes the status of an attempt to update a notification.</span></span>

## <a name="properties"></a><span data-ttu-id="9759b-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9759b-106">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="9759b-107">notificationId</span><span class="sxs-lookup"><span data-stu-id="9759b-107">notificationId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`

<span data-ttu-id="9759b-108">通知の ID。</span><span class="sxs-lookup"><span data-stu-id="9759b-108">The ID of the notification.</span></span>

### <a name="succeeded"></a><span data-ttu-id="9759b-109">succeeded</span><span class="sxs-lookup"><span data-stu-id="9759b-109">succeeded</span></span>
`@property(nonatomic, readonly) Succeeded succeeded;`

<span data-ttu-id="9759b-110">操作が成功したかどうか。</span><span class="sxs-lookup"><span data-stu-id="9759b-110">Whether the operation succeeded.</span></span> 