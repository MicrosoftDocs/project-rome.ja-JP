---
title: MCDUserNotificationReadStateFilter
description: (フィルター選択された通知の取得) の読み取りの状態が通知を分類する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801344"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a><span data-ttu-id="81c73-104">列挙型 `MCDUserNotificationReadStateFilter`</span><span class="sxs-lookup"><span data-stu-id="81c73-104">enum `MCDUserNotificationReadStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

<span data-ttu-id="81c73-105">(フィルター選択された通知の取得) の読み取りの状態が通知を分類する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="81c73-105">Contains values that categorize notifications by read state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="81c73-106">名前</span><span class="sxs-lookup"><span data-stu-id="81c73-106">Name</span></span> | <span data-ttu-id="81c73-107">値</span><span class="sxs-lookup"><span data-stu-id="81c73-107">Value</span></span> | <span data-ttu-id="81c73-108">説明</span><span class="sxs-lookup"><span data-stu-id="81c73-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="81c73-109">MCDUserNotificationReadStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="81c73-109">MCDUserNotificationReadStateFilterAny</span></span> | <span data-ttu-id="81c73-110">0</span><span class="sxs-lookup"><span data-stu-id="81c73-110">0</span></span> | <span data-ttu-id="81c73-111">読み取り状態に関係なく通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="81c73-111">Include notifications regardless of read state.</span></span>|
|   <span data-ttu-id="81c73-112">MCDUserNotificationReadStateFilterUnread</span><span class="sxs-lookup"><span data-stu-id="81c73-112">MCDUserNotificationReadStateFilterUnread</span></span> | <span data-ttu-id="81c73-113">1</span><span class="sxs-lookup"><span data-stu-id="81c73-113">1</span></span> | <span data-ttu-id="81c73-114">未読の通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="81c73-114">Include notifications that haven't been read.</span></span>|
|   <span data-ttu-id="81c73-115">MCDUserNotificationReadStateFilterRead</span><span class="sxs-lookup"><span data-stu-id="81c73-115">MCDUserNotificationReadStateFilterRead</span></span> | <span data-ttu-id="81c73-116">2</span><span class="sxs-lookup"><span data-stu-id="81c73-116">2</span></span> | <span data-ttu-id="81c73-117">読み取られた通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="81c73-117">Include notifications that have been read.</span></span> |