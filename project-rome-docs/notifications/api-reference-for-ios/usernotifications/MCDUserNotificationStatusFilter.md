---
title: MCDUserNotificationStatusFilter
description: 通知のリーダーを作成するときに、読み取り状態フィルターを示す値が含まれています。 のみ読み取りをアプリがすべての通知を受信するかどうかを指定しますまたは、未読のものだけです。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801494"
---
# <a name="enum-mcdusernotificationstatusfilter"></a><span data-ttu-id="129a9-105">列挙型 `MCDUserNotificationStatusFilter`</span><span class="sxs-lookup"><span data-stu-id="129a9-105">enum `MCDUserNotificationStatusFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

<span data-ttu-id="129a9-106">通知のリーダーを作成するときに、読み取り状態フィルターを示す値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="129a9-106">Contains values that indicates a read state filter when creating a notification reader.</span></span> <span data-ttu-id="129a9-107">のみ読み取りをアプリがすべての通知を受信するかどうかを指定しますまたは、未読のものだけです。</span><span class="sxs-lookup"><span data-stu-id="129a9-107">This determines whether the app wants to receive all notifications, only read ones, or only unread ones.</span></span> 

|<span data-ttu-id="129a9-108">名前</span><span class="sxs-lookup"><span data-stu-id="129a9-108">Name</span></span> | <span data-ttu-id="129a9-109">値</span><span class="sxs-lookup"><span data-stu-id="129a9-109">Value</span></span> | <span data-ttu-id="129a9-110">説明</span><span class="sxs-lookup"><span data-stu-id="129a9-110">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="129a9-111">MCDUserNotificationStatusFilterAny</span><span class="sxs-lookup"><span data-stu-id="129a9-111">MCDUserNotificationStatusFilterAny</span></span> | <span data-ttu-id="129a9-112">0</span><span class="sxs-lookup"><span data-stu-id="129a9-112">0</span></span>| <span data-ttu-id="129a9-113">状態の値に関係なくすべての通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="129a9-113">Include all notifications regardless of status value.</span></span> |
|   <span data-ttu-id="129a9-114">MCDUserNotificationStatusFilterActive</span><span class="sxs-lookup"><span data-stu-id="129a9-114">MCDUserNotificationStatusFilterActive</span></span> |<span data-ttu-id="129a9-115">1</span><span class="sxs-lookup"><span data-stu-id="129a9-115">1</span></span>| <span data-ttu-id="129a9-116">接続されているデバイス プラットフォームの通知のストアでアクティブ化された永続化を通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="129a9-116">Include notifications that are active and persisted in Connected Devices Platform notification store.</span></span> |
|   <span data-ttu-id="129a9-117">MCDUserNotificationStatusFilterDeleted</span><span class="sxs-lookup"><span data-stu-id="129a9-117">MCDUserNotificationStatusFilterDeleted</span></span> | <span data-ttu-id="129a9-118">2</span><span class="sxs-lookup"><span data-stu-id="129a9-118">2</span></span>| <span data-ttu-id="129a9-119">削除済みの通知のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="129a9-119">Include deleted notifications only.</span></span>|