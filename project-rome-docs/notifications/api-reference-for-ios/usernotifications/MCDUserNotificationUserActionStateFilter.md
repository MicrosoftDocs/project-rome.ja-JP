---
title: MCDUserNotificationUserActionStateFilter
description: ユーザーアクションの状態 (フィルター処理された通知の取得用) で通知を分類する値が含まれます。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800564"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a><span data-ttu-id="b519f-104">enum`MCDUserNotificationUserActionStateFilter`</span><span class="sxs-lookup"><span data-stu-id="b519f-104">enum `MCDUserNotificationUserActionStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

<span data-ttu-id="b519f-105">ユーザーアクションの状態 (フィルター処理された通知の取得用) で通知を分類する値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b519f-105">Contains values that categorize notifications by user action state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="b519f-106">名前</span><span class="sxs-lookup"><span data-stu-id="b519f-106">Name</span></span> | <span data-ttu-id="b519f-107">値</span><span class="sxs-lookup"><span data-stu-id="b519f-107">Value</span></span> | <span data-ttu-id="b519f-108">説明</span><span class="sxs-lookup"><span data-stu-id="b519f-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="b519f-109">MCDUserNotificationUserActionStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="b519f-109">MCDUserNotificationUserActionStateFilterAny</span></span>|<span data-ttu-id="b519f-110">0</span><span class="sxs-lookup"><span data-stu-id="b519f-110">0</span></span>| <span data-ttu-id="b519f-111">ユーザーの操作の状態に関係なく通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="b519f-111">Include notifications regardless of user action state.</span></span>|
|   <span data-ttu-id="b519f-112">MCDUserNotificationUserActionStateFilterNoInteraction</span><span class="sxs-lookup"><span data-stu-id="b519f-112">MCDUserNotificationUserActionStateFilterNoInteraction</span></span> |<span data-ttu-id="b519f-113">1</span><span class="sxs-lookup"><span data-stu-id="b519f-113">1</span></span>| <span data-ttu-id="b519f-114">ユーザーによって処理されていない通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="b519f-114">Include notifications that have not been acted on by the user.</span></span>|
|   <span data-ttu-id="b519f-115">MCDUserNotificationUserActionStateFilterActivated</span><span class="sxs-lookup"><span data-stu-id="b519f-115">MCDUserNotificationUserActionStateFilterActivated</span></span>|<span data-ttu-id="b519f-116">2</span><span class="sxs-lookup"><span data-stu-id="b519f-116">2</span></span>| <span data-ttu-id="b519f-117">ユーザーによってアクティブ化された通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="b519f-117">Include notifications that have been activated by the user.</span></span>|
|   <span data-ttu-id="b519f-118">MCDUserNotificationUserActionStateFilterDismissed</span><span class="sxs-lookup"><span data-stu-id="b519f-118">MCDUserNotificationUserActionStateFilterDismissed</span></span>|<span data-ttu-id="b519f-119">3</span><span class="sxs-lookup"><span data-stu-id="b519f-119">3</span></span>| <span data-ttu-id="b519f-120">ユーザーによって破棄された通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="b519f-120">Include notifications that have been dismissed by the user.</span></span>|
|   <span data-ttu-id="b519f-121">MCDUserNotificationUserActionStateFilterSnoozed</span><span class="sxs-lookup"><span data-stu-id="b519f-121">MCDUserNotificationUserActionStateFilterSnoozed</span></span>|<span data-ttu-id="b519f-122">4</span><span class="sxs-lookup"><span data-stu-id="b519f-122">4</span></span>| <span data-ttu-id="b519f-123">ユーザーによって再通知された通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="b519f-123">Include notifications that have been snoozed by the user.</span></span>|