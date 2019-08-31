---
title: MCDUserNotificationUserActionState
description: ユーザーが通知に対して行ったアクションを記述する値を格納します。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800804"
---
# <a name="enum-mcdusernotificationuseractionstate"></a><span data-ttu-id="b2c00-104">enum`MCDUserNotificationUserActionState`</span><span class="sxs-lookup"><span data-stu-id="b2c00-104">enum `MCDUserNotificationUserActionState`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

<span data-ttu-id="b2c00-105">ユーザーが通知に対して行ったアクションを記述する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="b2c00-105">Contains values describing the action a user has taken on a notification.</span></span>

|<span data-ttu-id="b2c00-106">名前</span><span class="sxs-lookup"><span data-stu-id="b2c00-106">Name</span></span> | <span data-ttu-id="b2c00-107">値</span><span class="sxs-lookup"><span data-stu-id="b2c00-107">Value</span></span> | <span data-ttu-id="b2c00-108">説明</span><span class="sxs-lookup"><span data-stu-id="b2c00-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="b2c00-109">MCDUserNotificationUserActionStateNoInteraction</span><span class="sxs-lookup"><span data-stu-id="b2c00-109">MCDUserNotificationUserActionStateNoInteraction</span></span> |<span data-ttu-id="b2c00-110">0</span><span class="sxs-lookup"><span data-stu-id="b2c00-110">0</span></span>| <span data-ttu-id="b2c00-111">ユーザーは何の操作も行っていません。</span><span class="sxs-lookup"><span data-stu-id="b2c00-111">The user hasn't taken any action.</span></span>|
|   <span data-ttu-id="b2c00-112">MCDUserNotificationUserActionStateActivated</span><span class="sxs-lookup"><span data-stu-id="b2c00-112">MCDUserNotificationUserActionStateActivated</span></span>|<span data-ttu-id="b2c00-113">1</span><span class="sxs-lookup"><span data-stu-id="b2c00-113">1</span></span>|<span data-ttu-id="b2c00-114">ユーザーが通知をアクティブ化しました。</span><span class="sxs-lookup"><span data-stu-id="b2c00-114">The user has activated the notification.</span></span>|
|   <span data-ttu-id="b2c00-115">MCDUserNotificationUserActionStateDismissed</span><span class="sxs-lookup"><span data-stu-id="b2c00-115">MCDUserNotificationUserActionStateDismissed</span></span>|<span data-ttu-id="b2c00-116">2</span><span class="sxs-lookup"><span data-stu-id="b2c00-116">2</span></span>| <span data-ttu-id="b2c00-117">ユーザーが通知を閉じました。</span><span class="sxs-lookup"><span data-stu-id="b2c00-117">The user has dismissed the notification.</span></span>|
|   <span data-ttu-id="b2c00-118">MCDUserNotificationUserActionStateSnoozed</span><span class="sxs-lookup"><span data-stu-id="b2c00-118">MCDUserNotificationUserActionStateSnoozed</span></span>|<span data-ttu-id="b2c00-119">3</span><span class="sxs-lookup"><span data-stu-id="b2c00-119">3</span></span>| <span data-ttu-id="b2c00-120">ユーザーが通知を再通知しました。</span><span class="sxs-lookup"><span data-stu-id="b2c00-120">The user has snoozed the notification.</span></span>|
