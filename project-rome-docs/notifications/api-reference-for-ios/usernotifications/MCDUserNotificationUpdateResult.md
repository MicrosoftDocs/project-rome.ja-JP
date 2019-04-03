---
title: MCDUserNotificationUpdateResult
description: このクラスには、通知の更新の状態について説明します。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 814d4373c47c8af00d3e003f730db804f48c5fb0
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907974"
---
# <a name="class-mcdusernotificationupdateresult"></a><span data-ttu-id="02e90-104">クラス `MCDUserNotificationUpdateResult`</span><span class="sxs-lookup"><span data-stu-id="02e90-104">class `MCDUserNotificationUpdateResult`</span></span>

```
@interface MCDUserNotificationUpdateResult : NSObject
```

<span data-ttu-id="02e90-105">このクラスには、通知の更新の状態について説明します。</span><span class="sxs-lookup"><span data-stu-id="02e90-105">This class describes the status of an attempt to update a notification.</span></span>

## <a name="properties"></a><span data-ttu-id="02e90-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="02e90-106">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="02e90-107">notificationId</span><span class="sxs-lookup"><span data-stu-id="02e90-107">notificationId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`

<span data-ttu-id="02e90-108">通知の ID。</span><span class="sxs-lookup"><span data-stu-id="02e90-108">The ID of the notification.</span></span>

### <a name="succeeded"></a><span data-ttu-id="02e90-109">成功しました</span><span class="sxs-lookup"><span data-stu-id="02e90-109">succeeded</span></span>
`@property(nonatomic, readonly) Succeeded succeeded;`

<span data-ttu-id="02e90-110">操作が成功したかどうか。</span><span class="sxs-lookup"><span data-stu-id="02e90-110">Whether the operation succeeded.</span></span> 