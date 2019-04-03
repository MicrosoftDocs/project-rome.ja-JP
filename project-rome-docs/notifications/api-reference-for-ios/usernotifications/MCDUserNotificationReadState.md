---
title: MCDUserNotificationReadState
description: 通知の読み取りの状態を記述する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: cdadac58bad0f642d9c1b482cf5aa5cbab15ee1b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909084"
---
# <a name="enum-mcdusernotificationreadstate"></a><span data-ttu-id="6398e-104">列挙型 `MCDUserNotificationReadState`</span><span class="sxs-lookup"><span data-stu-id="6398e-104">enum `MCDUserNotificationReadState`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadState)
```

<span data-ttu-id="6398e-105">通知の読み取りの状態を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6398e-105">Contains values that describe the read state of a notification.</span></span>

|<span data-ttu-id="6398e-106">名前</span><span class="sxs-lookup"><span data-stu-id="6398e-106">Name</span></span> | <span data-ttu-id="6398e-107">値</span><span class="sxs-lookup"><span data-stu-id="6398e-107">Value</span></span> | <span data-ttu-id="6398e-108">説明</span><span class="sxs-lookup"><span data-stu-id="6398e-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="6398e-109">MCDUserNotificationReadStateUnread</span><span class="sxs-lookup"><span data-stu-id="6398e-109">MCDUserNotificationReadStateUnread</span></span> |<span data-ttu-id="6398e-110">0</span><span class="sxs-lookup"><span data-stu-id="6398e-110">0</span></span>| <span data-ttu-id="6398e-111">通知がない読み取られました。</span><span class="sxs-lookup"><span data-stu-id="6398e-111">The notification has not been read.</span></span> |
|   <span data-ttu-id="6398e-112">MCDUserNotificationReadStateRead</span><span class="sxs-lookup"><span data-stu-id="6398e-112">MCDUserNotificationReadStateRead</span></span> | <span data-ttu-id="6398e-113">1</span><span class="sxs-lookup"><span data-stu-id="6398e-113">1</span></span>| <span data-ttu-id="6398e-114">通知が読み取られました。</span><span class="sxs-lookup"><span data-stu-id="6398e-114">The notification has been read.</span></span>|