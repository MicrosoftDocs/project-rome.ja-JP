---
title: MCDUserNotificationUserActionStateFilter
description: 分類 (フィルター選択された通知の取得) するためのユーザー アクションの状態を通知する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800564"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a><span data-ttu-id="0047c-104">列挙型 `MCDUserNotificationUserActionStateFilter`</span><span class="sxs-lookup"><span data-stu-id="0047c-104">enum `MCDUserNotificationUserActionStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

<span data-ttu-id="0047c-105">分類 (フィルター選択された通知の取得) するためのユーザー アクションの状態を通知する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0047c-105">Contains values that categorize notifications by user action state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="0047c-106">名前</span><span class="sxs-lookup"><span data-stu-id="0047c-106">Name</span></span> | <span data-ttu-id="0047c-107">値</span><span class="sxs-lookup"><span data-stu-id="0047c-107">Value</span></span> | <span data-ttu-id="0047c-108">説明</span><span class="sxs-lookup"><span data-stu-id="0047c-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="0047c-109">MCDUserNotificationUserActionStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="0047c-109">MCDUserNotificationUserActionStateFilterAny</span></span>|<span data-ttu-id="0047c-110">0</span><span class="sxs-lookup"><span data-stu-id="0047c-110">0</span></span>| <span data-ttu-id="0047c-111">ユーザー アクションの状態に関係なく通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0047c-111">Include notifications regardless of user action state.</span></span>|
|   <span data-ttu-id="0047c-112">MCDUserNotificationUserActionStateFilterNoInteraction</span><span class="sxs-lookup"><span data-stu-id="0047c-112">MCDUserNotificationUserActionStateFilterNoInteraction</span></span> |<span data-ttu-id="0047c-113">1</span><span class="sxs-lookup"><span data-stu-id="0047c-113">1</span></span>| <span data-ttu-id="0047c-114">ユーザーが処理済みいない通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0047c-114">Include notifications that have not been acted on by the user.</span></span>|
|   <span data-ttu-id="0047c-115">MCDUserNotificationUserActionStateFilterActivated</span><span class="sxs-lookup"><span data-stu-id="0047c-115">MCDUserNotificationUserActionStateFilterActivated</span></span>|<span data-ttu-id="0047c-116">2</span><span class="sxs-lookup"><span data-stu-id="0047c-116">2</span></span>| <span data-ttu-id="0047c-117">ユーザーがアクティブ化されている通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0047c-117">Include notifications that have been activated by the user.</span></span>|
|   <span data-ttu-id="0047c-118">MCDUserNotificationUserActionStateFilterDismissed</span><span class="sxs-lookup"><span data-stu-id="0047c-118">MCDUserNotificationUserActionStateFilterDismissed</span></span>|<span data-ttu-id="0047c-119">3</span><span class="sxs-lookup"><span data-stu-id="0047c-119">3</span></span>| <span data-ttu-id="0047c-120">ユーザーが既に閉じられている通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0047c-120">Include notifications that have been dismissed by the user.</span></span>|
|   <span data-ttu-id="0047c-121">MCDUserNotificationUserActionStateFilterSnoozed</span><span class="sxs-lookup"><span data-stu-id="0047c-121">MCDUserNotificationUserActionStateFilterSnoozed</span></span>|<span data-ttu-id="0047c-122">4</span><span class="sxs-lookup"><span data-stu-id="0047c-122">4</span></span>| <span data-ttu-id="0047c-123">ユーザーによって再されている通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0047c-123">Include notifications that have been snoozed by the user.</span></span>|