---
title: MCDUserNotificationStatus
description: 通知を削除するかどうかを決定する値が含まれています。 削除済みの通知は、通知ストアでは引き続きとプラットフォームのクリーンアップが発生する前に、リーダーによって返されます。 これらの通知の通知のリーダーに表示されないようにするのには、対応するリーダー フィルター UserNotificationStatusFilter を適用できます。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907244"
---
# <a name="enum-mcdusernotificationstatus"></a><span data-ttu-id="7e595-106">列挙型 `MCDUserNotificationStatus`</span><span class="sxs-lookup"><span data-stu-id="7e595-106">enum `MCDUserNotificationStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

<span data-ttu-id="7e595-107">通知を削除するかどうかを決定する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7e595-107">Contains values that determines whether the notification is deleted or not.</span></span> <span data-ttu-id="7e595-108">削除済みの通知は、通知ストアでは引き続きとプラットフォームのクリーンアップが発生する前に、リーダーによって返されます。</span><span class="sxs-lookup"><span data-stu-id="7e595-108">Deleted notifications will still be in the notification store and be returned by the reader before the platform cleanup happens.</span></span> <span data-ttu-id="7e595-109">これらの通知の通知のリーダーに表示されないようにするのには、対応するリーダー フィルター UserNotificationStatusFilter を適用できます。</span><span class="sxs-lookup"><span data-stu-id="7e595-109">A corresponding reader filter UserNotificationStatusFilter can be applied to prevent these notifications from showing up in notification reader.</span></span> 

|<span data-ttu-id="7e595-110">名前</span><span class="sxs-lookup"><span data-stu-id="7e595-110">Name</span></span> | <span data-ttu-id="7e595-111">値</span><span class="sxs-lookup"><span data-stu-id="7e595-111">Value</span></span> | <span data-ttu-id="7e595-112">説明</span><span class="sxs-lookup"><span data-stu-id="7e595-112">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="7e595-113">MCDUserNotificationStatusActive</span><span class="sxs-lookup"><span data-stu-id="7e595-113">MCDUserNotificationStatusActive</span></span> |<span data-ttu-id="7e595-114">0</span><span class="sxs-lookup"><span data-stu-id="7e595-114">0</span></span>| <span data-ttu-id="7e595-115">通知は、まだアクティブで接続されているデバイス プラットフォームのストア内で永続化されました。</span><span class="sxs-lookup"><span data-stu-id="7e595-115">The notification is still active and persisted inside Connected Devices Platform store.</span></span> |
|   <span data-ttu-id="7e595-116">MCDUserNotificationStatusDeleted</span><span class="sxs-lookup"><span data-stu-id="7e595-116">MCDUserNotificationStatusDeleted</span></span> | <span data-ttu-id="7e595-117">1</span><span class="sxs-lookup"><span data-stu-id="7e595-117">1</span></span>| <span data-ttu-id="7e595-118">通知が削除されました。</span><span class="sxs-lookup"><span data-stu-id="7e595-118">The notification has been deleted.</span></span>|