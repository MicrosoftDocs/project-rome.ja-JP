---
title: MCDUserNotificationReadStateFilter
description: 通知を (フィルター処理された通知の取得のために) 読み取り状態で分類する値を格納します。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801344"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a><span data-ttu-id="d1a07-104">enum`MCDUserNotificationReadStateFilter`</span><span class="sxs-lookup"><span data-stu-id="d1a07-104">enum `MCDUserNotificationReadStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

<span data-ttu-id="d1a07-105">通知を (フィルター処理された通知の取得のために) 読み取り状態で分類する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="d1a07-105">Contains values that categorize notifications by read state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="d1a07-106">名前</span><span class="sxs-lookup"><span data-stu-id="d1a07-106">Name</span></span> | <span data-ttu-id="d1a07-107">値</span><span class="sxs-lookup"><span data-stu-id="d1a07-107">Value</span></span> | <span data-ttu-id="d1a07-108">説明</span><span class="sxs-lookup"><span data-stu-id="d1a07-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="d1a07-109">MCDUserNotificationReadStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="d1a07-109">MCDUserNotificationReadStateFilterAny</span></span> | <span data-ttu-id="d1a07-110">0</span><span class="sxs-lookup"><span data-stu-id="d1a07-110">0</span></span> | <span data-ttu-id="d1a07-111">読み取り状態に関係なく通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="d1a07-111">Include notifications regardless of read state.</span></span>|
|   <span data-ttu-id="d1a07-112">MCDUserNotificationReadStateFilterUnread</span><span class="sxs-lookup"><span data-stu-id="d1a07-112">MCDUserNotificationReadStateFilterUnread</span></span> | <span data-ttu-id="d1a07-113">1</span><span class="sxs-lookup"><span data-stu-id="d1a07-113">1</span></span> | <span data-ttu-id="d1a07-114">まだ読み込まれていない通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="d1a07-114">Include notifications that haven't been read.</span></span>|
|   <span data-ttu-id="d1a07-115">MCDUserNotificationReadStateFilterRead</span><span class="sxs-lookup"><span data-stu-id="d1a07-115">MCDUserNotificationReadStateFilterRead</span></span> | <span data-ttu-id="d1a07-116">2</span><span class="sxs-lookup"><span data-stu-id="d1a07-116">2</span></span> | <span data-ttu-id="d1a07-117">読み取られた通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="d1a07-117">Include notifications that have been read.</span></span> |