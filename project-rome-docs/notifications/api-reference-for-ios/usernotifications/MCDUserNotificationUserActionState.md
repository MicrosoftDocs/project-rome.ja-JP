---
title: MCDUserNotificationUserActionState
description: 通知をユーザーが実行されるアクションを記述する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907784"
---
# <a name="enum-mcdusernotificationuseractionstate"></a><span data-ttu-id="fd311-104">列挙型 `MCDUserNotificationUserActionState`</span><span class="sxs-lookup"><span data-stu-id="fd311-104">enum `MCDUserNotificationUserActionState`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

<span data-ttu-id="fd311-105">通知をユーザーが実行されるアクションを記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fd311-105">Contains values describing the action a user has taken on a notification.</span></span>

|<span data-ttu-id="fd311-106">名前</span><span class="sxs-lookup"><span data-stu-id="fd311-106">Name</span></span> | <span data-ttu-id="fd311-107">値</span><span class="sxs-lookup"><span data-stu-id="fd311-107">Value</span></span> | <span data-ttu-id="fd311-108">説明</span><span class="sxs-lookup"><span data-stu-id="fd311-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="fd311-109">MCDUserNotificationUserActionStateNoInteraction</span><span class="sxs-lookup"><span data-stu-id="fd311-109">MCDUserNotificationUserActionStateNoInteraction</span></span> |<span data-ttu-id="fd311-110">0</span><span class="sxs-lookup"><span data-stu-id="fd311-110">0</span></span>| <span data-ttu-id="fd311-111">ユーザーは、任意のアクションを実行していません。</span><span class="sxs-lookup"><span data-stu-id="fd311-111">The user hasn't taken any action.</span></span>|
|   <span data-ttu-id="fd311-112">MCDUserNotificationUserActionStateActivated</span><span class="sxs-lookup"><span data-stu-id="fd311-112">MCDUserNotificationUserActionStateActivated</span></span>|<span data-ttu-id="fd311-113">1</span><span class="sxs-lookup"><span data-stu-id="fd311-113">1</span></span>|<span data-ttu-id="fd311-114">ユーザーは、通知をアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="fd311-114">The user has activated the notification.</span></span>|
|   <span data-ttu-id="fd311-115">MCDUserNotificationUserActionStateDismissed</span><span class="sxs-lookup"><span data-stu-id="fd311-115">MCDUserNotificationUserActionStateDismissed</span></span>|<span data-ttu-id="fd311-116">2</span><span class="sxs-lookup"><span data-stu-id="fd311-116">2</span></span>| <span data-ttu-id="fd311-117">ユーザーが通知を閉じる。</span><span class="sxs-lookup"><span data-stu-id="fd311-117">The user has dismissed the notification.</span></span>|
|   <span data-ttu-id="fd311-118">MCDUserNotificationUserActionStateSnoozed</span><span class="sxs-lookup"><span data-stu-id="fd311-118">MCDUserNotificationUserActionStateSnoozed</span></span>|<span data-ttu-id="fd311-119">3</span><span class="sxs-lookup"><span data-stu-id="fd311-119">3</span></span>| <span data-ttu-id="fd311-120">ユーザーは、通知を再います。</span><span class="sxs-lookup"><span data-stu-id="fd311-120">The user has snoozed the notification.</span></span>|
