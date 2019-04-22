---
title: MCDUserNotificationReadState
description: 通知の読み取りの状態を記述する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: cdadac58bad0f642d9c1b482cf5aa5cbab15ee1b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801284"
---
# <a name="enum-mcdusernotificationreadstate"></a><span data-ttu-id="05828-104">列挙型 `MCDUserNotificationReadState`</span><span class="sxs-lookup"><span data-stu-id="05828-104">enum `MCDUserNotificationReadState`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadState)
```

<span data-ttu-id="05828-105">通知の読み取りの状態を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="05828-105">Contains values that describe the read state of a notification.</span></span>

|<span data-ttu-id="05828-106">名前</span><span class="sxs-lookup"><span data-stu-id="05828-106">Name</span></span> | <span data-ttu-id="05828-107">値</span><span class="sxs-lookup"><span data-stu-id="05828-107">Value</span></span> | <span data-ttu-id="05828-108">説明</span><span class="sxs-lookup"><span data-stu-id="05828-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="05828-109">MCDUserNotificationReadStateUnread</span><span class="sxs-lookup"><span data-stu-id="05828-109">MCDUserNotificationReadStateUnread</span></span> |<span data-ttu-id="05828-110">0</span><span class="sxs-lookup"><span data-stu-id="05828-110">0</span></span>| <span data-ttu-id="05828-111">通知がない読み取られました。</span><span class="sxs-lookup"><span data-stu-id="05828-111">The notification has not been read.</span></span> |
|   <span data-ttu-id="05828-112">MCDUserNotificationReadStateRead</span><span class="sxs-lookup"><span data-stu-id="05828-112">MCDUserNotificationReadStateRead</span></span> | <span data-ttu-id="05828-113">1</span><span class="sxs-lookup"><span data-stu-id="05828-113">1</span></span>| <span data-ttu-id="05828-114">通知が読み取られました。</span><span class="sxs-lookup"><span data-stu-id="05828-114">The notification has been read.</span></span>|