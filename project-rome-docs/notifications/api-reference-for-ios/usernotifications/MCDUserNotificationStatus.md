---
title: MCDUserNotificationStatus
description: 通知が削除されたかどうかを示す値を格納します。 削除された通知は通知ストアに残りますが、プラットフォームのクリーンアップが発生する前にリーダーによって返されます。 これらの通知が通知リーダーに表示されないように、対応するリーダーフィルター UserNotificationStatusFilter を適用できます。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800814"
---
# <a name="enum-mcdusernotificationstatus"></a><span data-ttu-id="7e068-106">enum`MCDUserNotificationStatus`</span><span class="sxs-lookup"><span data-stu-id="7e068-106">enum `MCDUserNotificationStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

<span data-ttu-id="7e068-107">通知が削除されたかどうかを示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="7e068-107">Contains values that determines whether the notification is deleted or not.</span></span> <span data-ttu-id="7e068-108">削除された通知は通知ストアに残りますが、プラットフォームのクリーンアップが発生する前にリーダーによって返されます。</span><span class="sxs-lookup"><span data-stu-id="7e068-108">Deleted notifications will still be in the notification store and be returned by the reader before the platform cleanup happens.</span></span> <span data-ttu-id="7e068-109">これらの通知が通知リーダーに表示されないように、対応するリーダーフィルター UserNotificationStatusFilter を適用できます。</span><span class="sxs-lookup"><span data-stu-id="7e068-109">A corresponding reader filter UserNotificationStatusFilter can be applied to prevent these notifications from showing up in notification reader.</span></span> 

|<span data-ttu-id="7e068-110">名前</span><span class="sxs-lookup"><span data-stu-id="7e068-110">Name</span></span> | <span data-ttu-id="7e068-111">値</span><span class="sxs-lookup"><span data-stu-id="7e068-111">Value</span></span> | <span data-ttu-id="7e068-112">説明</span><span class="sxs-lookup"><span data-stu-id="7e068-112">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="7e068-113">MCDUserNotificationStatusActive</span><span class="sxs-lookup"><span data-stu-id="7e068-113">MCDUserNotificationStatusActive</span></span> |<span data-ttu-id="7e068-114">0</span><span class="sxs-lookup"><span data-stu-id="7e068-114">0</span></span>| <span data-ttu-id="7e068-115">通知はまだアクティブであり、接続されているデバイスのプラットフォームストア内に保持されます。</span><span class="sxs-lookup"><span data-stu-id="7e068-115">The notification is still active and persisted inside Connected Devices Platform store.</span></span> |
|   <span data-ttu-id="7e068-116">MCDUserNotificationStatusDeleted</span><span class="sxs-lookup"><span data-stu-id="7e068-116">MCDUserNotificationStatusDeleted</span></span> | <span data-ttu-id="7e068-117">1</span><span class="sxs-lookup"><span data-stu-id="7e068-117">1</span></span>| <span data-ttu-id="7e068-118">通知が削除されました。</span><span class="sxs-lookup"><span data-stu-id="7e068-118">The notification has been deleted.</span></span>|