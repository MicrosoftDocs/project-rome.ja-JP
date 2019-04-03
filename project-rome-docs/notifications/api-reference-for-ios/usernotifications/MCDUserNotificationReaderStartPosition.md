---
title: MCDUserNotificationReaderStartPosition
description: 新しいユーザーの通知の受信または新規の受信状態の更新で – リーダーの新しい変更が開始する位置を決定する値が含まれています。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: c1fdf113614d496a2da49072f089f7e6a9f0ca68
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908984"
---
# <a name="enum-mcdusernotificationreaderstartposition"></a><span data-ttu-id="d65df-104">列挙型 `MCDUserNotificationReaderStartPosition`</span><span class="sxs-lookup"><span data-stu-id="d65df-104">enum `MCDUserNotificationReaderStartPosition`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReaderStartPosition)
```

<span data-ttu-id="d65df-105">新しいユーザーの通知の受信または新規の受信状態の更新で – リーダーの新しい変更が開始する位置を決定する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d65df-105">Contains values that determines the position where any new change in the reader starts – new incoming user notification or new incoming state updates.</span></span> 

|<span data-ttu-id="d65df-106">名前</span><span class="sxs-lookup"><span data-stu-id="d65df-106">Name</span></span> | <span data-ttu-id="d65df-107">値</span><span class="sxs-lookup"><span data-stu-id="d65df-107">Value</span></span> | <span data-ttu-id="d65df-108">説明</span><span class="sxs-lookup"><span data-stu-id="d65df-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="d65df-109">MCDUserNotificationReaderStartPositionBeginning</span><span class="sxs-lookup"><span data-stu-id="d65df-109">MCDUserNotificationReaderStartPositionBeginning</span></span> |<span data-ttu-id="d65df-110">0</span><span class="sxs-lookup"><span data-stu-id="d65df-110">0</span></span>| <span data-ttu-id="d65df-111">通知のストアの開始位置を開始します。</span><span class="sxs-lookup"><span data-stu-id="d65df-111">Start position at the beginning of the notification store.</span></span> |
|   <span data-ttu-id="d65df-112">MCDUserNotificationReaderStartPositionEnd</span><span class="sxs-lookup"><span data-stu-id="d65df-112">MCDUserNotificationReaderStartPositionEnd</span></span> | <span data-ttu-id="d65df-113">1</span><span class="sxs-lookup"><span data-stu-id="d65df-113">1</span></span>| <span data-ttu-id="d65df-114">通知のストアの終了位置を開始します。</span><span class="sxs-lookup"><span data-stu-id="d65df-114">Start position at the end of the notification store.</span></span> |