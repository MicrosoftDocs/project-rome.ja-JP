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
# <a name="class-mcdusernotificationupdateresult"></a><span data-ttu-id="9280b-104">講義`MCDUserNotificationUpdateResult`</span><span class="sxs-lookup"><span data-stu-id="9280b-104">class `MCDUserNotificationUpdateResult`</span></span>

```
@interface MCDUserNotificationUpdateResult : NSObject
```

<span data-ttu-id="9280b-105">このクラスは、通知を更新しようとしたときの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="9280b-105">This class describes the status of an attempt to update a notification.</span></span>

## <a name="properties"></a><span data-ttu-id="9280b-106">Properties</span><span class="sxs-lookup"><span data-stu-id="9280b-106">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="9280b-107">notificationId</span><span class="sxs-lookup"><span data-stu-id="9280b-107">notificationId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`

<span data-ttu-id="9280b-108">通知の ID。</span><span class="sxs-lookup"><span data-stu-id="9280b-108">The ID of the notification.</span></span>

### <a name="succeeded"></a><span data-ttu-id="9280b-109">succeeded</span><span class="sxs-lookup"><span data-stu-id="9280b-109">succeeded</span></span>
`@property(nonatomic, readonly) Succeeded succeeded;`

<span data-ttu-id="9280b-110">操作が成功したかどうか。</span><span class="sxs-lookup"><span data-stu-id="9280b-110">Whether the operation succeeded.</span></span> 