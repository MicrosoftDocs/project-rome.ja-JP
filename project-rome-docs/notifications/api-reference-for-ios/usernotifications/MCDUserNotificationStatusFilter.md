---
title: MCDUserNotificationStatusFilter
description: 通知のリーダーを作成するときに、読み取り状態フィルターを示す値が含まれています。 のみ読み取りをアプリがすべての通知を受信するかどうかを指定しますまたは、未読のものだけです。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909144"
---
# <a name="enum-mcdusernotificationstatusfilter"></a><span data-ttu-id="3a4d7-105">列挙型 `MCDUserNotificationStatusFilter`</span><span class="sxs-lookup"><span data-stu-id="3a4d7-105">enum `MCDUserNotificationStatusFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

<span data-ttu-id="3a4d7-106">通知のリーダーを作成するときに、読み取り状態フィルターを示す値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a4d7-106">Contains values that indicates a read state filter when creating a notification reader.</span></span> <span data-ttu-id="3a4d7-107">のみ読み取りをアプリがすべての通知を受信するかどうかを指定しますまたは、未読のものだけです。</span><span class="sxs-lookup"><span data-stu-id="3a4d7-107">This determines whether the app wants to receive all notifications, only read ones, or only unread ones.</span></span> 

|<span data-ttu-id="3a4d7-108">名前</span><span class="sxs-lookup"><span data-stu-id="3a4d7-108">Name</span></span> | <span data-ttu-id="3a4d7-109">値</span><span class="sxs-lookup"><span data-stu-id="3a4d7-109">Value</span></span> | <span data-ttu-id="3a4d7-110">説明</span><span class="sxs-lookup"><span data-stu-id="3a4d7-110">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="3a4d7-111">MCDUserNotificationStatusFilterAny</span><span class="sxs-lookup"><span data-stu-id="3a4d7-111">MCDUserNotificationStatusFilterAny</span></span> | <span data-ttu-id="3a4d7-112">0</span><span class="sxs-lookup"><span data-stu-id="3a4d7-112">0</span></span>| <span data-ttu-id="3a4d7-113">状態の値に関係なくすべての通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3a4d7-113">Include all notifications regardless of status value.</span></span> |
|   <span data-ttu-id="3a4d7-114">MCDUserNotificationStatusFilterActive</span><span class="sxs-lookup"><span data-stu-id="3a4d7-114">MCDUserNotificationStatusFilterActive</span></span> |<span data-ttu-id="3a4d7-115">1</span><span class="sxs-lookup"><span data-stu-id="3a4d7-115">1</span></span>| <span data-ttu-id="3a4d7-116">接続されているデバイス プラットフォームの通知のストアでアクティブ化された永続化を通知が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3a4d7-116">Include notifications that are active and persisted in Connected Devices Platform notification store.</span></span> |
|   <span data-ttu-id="3a4d7-117">MCDUserNotificationStatusFilterDeleted</span><span class="sxs-lookup"><span data-stu-id="3a4d7-117">MCDUserNotificationStatusFilterDeleted</span></span> | <span data-ttu-id="3a4d7-118">2</span><span class="sxs-lookup"><span data-stu-id="3a4d7-118">2</span></span>| <span data-ttu-id="3a4d7-119">削除済みの通知のみが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3a4d7-119">Include deleted notifications only.</span></span>|