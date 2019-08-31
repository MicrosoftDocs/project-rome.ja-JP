---
title: MCDUserNotificationStatusFilter
description: 通知リーダーを作成するときの読み取り状態フィルターを示す値を格納します。 これにより、アプリがすべての通知を受信するか、読み取り専用にするか、または未読のものだけを受信するかを決定します。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801494"
---
# <a name="enum-mcdusernotificationstatusfilter"></a><span data-ttu-id="4846d-105">enum`MCDUserNotificationStatusFilter`</span><span class="sxs-lookup"><span data-stu-id="4846d-105">enum `MCDUserNotificationStatusFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

<span data-ttu-id="4846d-106">通知リーダーを作成するときの読み取り状態フィルターを示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="4846d-106">Contains values that indicates a read state filter when creating a notification reader.</span></span> <span data-ttu-id="4846d-107">これにより、アプリがすべての通知を受信するか、読み取り専用にするか、または未読のものだけを受信するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="4846d-107">This determines whether the app wants to receive all notifications, only read ones, or only unread ones.</span></span> 

|<span data-ttu-id="4846d-108">名前</span><span class="sxs-lookup"><span data-stu-id="4846d-108">Name</span></span> | <span data-ttu-id="4846d-109">値</span><span class="sxs-lookup"><span data-stu-id="4846d-109">Value</span></span> | <span data-ttu-id="4846d-110">説明</span><span class="sxs-lookup"><span data-stu-id="4846d-110">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="4846d-111">MCDUserNotificationStatusFilterAny</span><span class="sxs-lookup"><span data-stu-id="4846d-111">MCDUserNotificationStatusFilterAny</span></span> | <span data-ttu-id="4846d-112">0</span><span class="sxs-lookup"><span data-stu-id="4846d-112">0</span></span>| <span data-ttu-id="4846d-113">状態の値に関係なく、すべての通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="4846d-113">Include all notifications regardless of status value.</span></span> |
|   <span data-ttu-id="4846d-114">MCDUserNotificationStatusFilterActive</span><span class="sxs-lookup"><span data-stu-id="4846d-114">MCDUserNotificationStatusFilterActive</span></span> |<span data-ttu-id="4846d-115">1</span><span class="sxs-lookup"><span data-stu-id="4846d-115">1</span></span>| <span data-ttu-id="4846d-116">接続されているデバイスのプラットフォーム通知ストアにアクティブで永続化されている通知を含めます。</span><span class="sxs-lookup"><span data-stu-id="4846d-116">Include notifications that are active and persisted in Connected Devices Platform notification store.</span></span> |
|   <span data-ttu-id="4846d-117">MCDUserNotificationStatusFilterDeleted</span><span class="sxs-lookup"><span data-stu-id="4846d-117">MCDUserNotificationStatusFilterDeleted</span></span> | <span data-ttu-id="4846d-118">2</span><span class="sxs-lookup"><span data-stu-id="4846d-118">2</span></span>| <span data-ttu-id="4846d-119">削除された通知のみを含めます。</span><span class="sxs-lookup"><span data-stu-id="4846d-119">Include deleted notifications only.</span></span>|