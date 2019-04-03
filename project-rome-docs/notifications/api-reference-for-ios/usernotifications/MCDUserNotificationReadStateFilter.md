---
title: MCDUserNotificationReadStateFilter
description: (フィルター選択された通知の取得) の読み取りの状態が通知を分類する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907694"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a><span data-ttu-id="fe925-104">列挙型 `MCDUserNotificationReadStateFilter`</span><span class="sxs-lookup"><span data-stu-id="fe925-104">enum `MCDUserNotificationReadStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

<span data-ttu-id="fe925-105">(フィルター選択された通知の取得) の読み取りの状態が通知を分類する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fe925-105">Contains values that categorize notifications by read state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="fe925-106">名前</span><span class="sxs-lookup"><span data-stu-id="fe925-106">Name</span></span> | <span data-ttu-id="fe925-107">値</span><span class="sxs-lookup"><span data-stu-id="fe925-107">Value</span></span> | <span data-ttu-id="fe925-108">説明</span><span class="sxs-lookup"><span data-stu-id="fe925-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="fe925-109">MCDUserNotificationReadStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="fe925-109">MCDUserNotificationReadStateFilterAny</span></span> | <span data-ttu-id="fe925-110">0</span><span class="sxs-lookup"><span data-stu-id="fe925-110">0</span></span> | <span data-ttu-id="fe925-111">読み取り状態に関係なく通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fe925-111">Include notifications regardless of read state.</span></span>|
|   <span data-ttu-id="fe925-112">MCDUserNotificationReadStateFilterUnread</span><span class="sxs-lookup"><span data-stu-id="fe925-112">MCDUserNotificationReadStateFilterUnread</span></span> | <span data-ttu-id="fe925-113">1</span><span class="sxs-lookup"><span data-stu-id="fe925-113">1</span></span> | <span data-ttu-id="fe925-114">未読の通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fe925-114">Include notifications that haven't been read.</span></span>|
|   <span data-ttu-id="fe925-115">MCDUserNotificationReadStateFilterRead</span><span class="sxs-lookup"><span data-stu-id="fe925-115">MCDUserNotificationReadStateFilterRead</span></span> | <span data-ttu-id="fe925-116">2</span><span class="sxs-lookup"><span data-stu-id="fe925-116">2</span></span> | <span data-ttu-id="fe925-117">読み取られた通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fe925-117">Include notifications that have been read.</span></span> |