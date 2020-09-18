---
title: MCDUserNotificationReadState
description: MCDUserNotificationReadState 列挙型について説明します。 この列挙には、通知の読み取り状態を記述する値が含まれます。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: ce082e85b446977a85c2f93bfafdcd6889c06d92
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760856"
---
# <a name="enum-mcdusernotificationreadstate"></a><span data-ttu-id="f1a52-105">enum `MCDUserNotificationReadState`</span><span class="sxs-lookup"><span data-stu-id="f1a52-105">enum `MCDUserNotificationReadState`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadState)
```

<span data-ttu-id="f1a52-106">通知の読み取り状態を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="f1a52-106">Contains values that describe the read state of a notification.</span></span>

|<span data-ttu-id="f1a52-107">名前</span><span class="sxs-lookup"><span data-stu-id="f1a52-107">Name</span></span> | <span data-ttu-id="f1a52-108">[値]</span><span class="sxs-lookup"><span data-stu-id="f1a52-108">Value</span></span> | <span data-ttu-id="f1a52-109">説明</span><span class="sxs-lookup"><span data-stu-id="f1a52-109">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="f1a52-110">MCDUserNotificationReadStateUnread</span><span class="sxs-lookup"><span data-stu-id="f1a52-110">MCDUserNotificationReadStateUnread</span></span> |<span data-ttu-id="f1a52-111">0</span><span class="sxs-lookup"><span data-stu-id="f1a52-111">0</span></span>| <span data-ttu-id="f1a52-112">通知が読み取られていません。</span><span class="sxs-lookup"><span data-stu-id="f1a52-112">The notification has not been read.</span></span> |
|   <span data-ttu-id="f1a52-113">MCDUserNotificationReadStateRead</span><span class="sxs-lookup"><span data-stu-id="f1a52-113">MCDUserNotificationReadStateRead</span></span> | <span data-ttu-id="f1a52-114">1</span><span class="sxs-lookup"><span data-stu-id="f1a52-114">1</span></span>| <span data-ttu-id="f1a52-115">通知が読み取られました。</span><span class="sxs-lookup"><span data-stu-id="f1a52-115">The notification has been read.</span></span>|