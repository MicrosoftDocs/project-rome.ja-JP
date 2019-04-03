---
title: MCDUserNotificationUserActionStateFilter
description: 分類 (フィルター選択された通知の取得) するためのユーザー アクションの状態を通知する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907274"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a><span data-ttu-id="1c176-104">列挙型 `MCDUserNotificationUserActionStateFilter`</span><span class="sxs-lookup"><span data-stu-id="1c176-104">enum `MCDUserNotificationUserActionStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

<span data-ttu-id="1c176-105">分類 (フィルター選択された通知の取得) するためのユーザー アクションの状態を通知する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c176-105">Contains values that categorize notifications by user action state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="1c176-106">名前</span><span class="sxs-lookup"><span data-stu-id="1c176-106">Name</span></span> | <span data-ttu-id="1c176-107">値</span><span class="sxs-lookup"><span data-stu-id="1c176-107">Value</span></span> | <span data-ttu-id="1c176-108">説明</span><span class="sxs-lookup"><span data-stu-id="1c176-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="1c176-109">MCDUserNotificationUserActionStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="1c176-109">MCDUserNotificationUserActionStateFilterAny</span></span>|<span data-ttu-id="1c176-110">0</span><span class="sxs-lookup"><span data-stu-id="1c176-110">0</span></span>| <span data-ttu-id="1c176-111">ユーザー アクションの状態に関係なく通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c176-111">Include notifications regardless of user action state.</span></span>|
|   <span data-ttu-id="1c176-112">MCDUserNotificationUserActionStateFilterNoInteraction</span><span class="sxs-lookup"><span data-stu-id="1c176-112">MCDUserNotificationUserActionStateFilterNoInteraction</span></span> |<span data-ttu-id="1c176-113">1</span><span class="sxs-lookup"><span data-stu-id="1c176-113">1</span></span>| <span data-ttu-id="1c176-114">ユーザーが処理済みいない通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c176-114">Include notifications that have not been acted on by the user.</span></span>|
|   <span data-ttu-id="1c176-115">MCDUserNotificationUserActionStateFilterActivated</span><span class="sxs-lookup"><span data-stu-id="1c176-115">MCDUserNotificationUserActionStateFilterActivated</span></span>|<span data-ttu-id="1c176-116">2</span><span class="sxs-lookup"><span data-stu-id="1c176-116">2</span></span>| <span data-ttu-id="1c176-117">ユーザーがアクティブ化されている通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c176-117">Include notifications that have been activated by the user.</span></span>|
|   <span data-ttu-id="1c176-118">MCDUserNotificationUserActionStateFilterDismissed</span><span class="sxs-lookup"><span data-stu-id="1c176-118">MCDUserNotificationUserActionStateFilterDismissed</span></span>|<span data-ttu-id="1c176-119">3</span><span class="sxs-lookup"><span data-stu-id="1c176-119">3</span></span>| <span data-ttu-id="1c176-120">ユーザーが既に閉じられている通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c176-120">Include notifications that have been dismissed by the user.</span></span>|
|   <span data-ttu-id="1c176-121">MCDUserNotificationUserActionStateFilterSnoozed</span><span class="sxs-lookup"><span data-stu-id="1c176-121">MCDUserNotificationUserActionStateFilterSnoozed</span></span>|<span data-ttu-id="1c176-122">4</span><span class="sxs-lookup"><span data-stu-id="1c176-122">4</span></span>| <span data-ttu-id="1c176-123">ユーザーによって再されている通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1c176-123">Include notifications that have been snoozed by the user.</span></span>|