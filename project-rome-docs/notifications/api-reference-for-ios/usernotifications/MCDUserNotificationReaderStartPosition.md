---
title: MCDUserNotificationReaderStartPosition
description: リーダーの新しい変更が開始される位置 (新しい受信ユーザー通知または新しい受信状態の更新) を決定する値を格納します。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: c1fdf113614d496a2da49072f089f7e6a9f0ca68
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800344"
---
# <a name="enum-mcdusernotificationreaderstartposition"></a><span data-ttu-id="ca5f3-104">enum`MCDUserNotificationReaderStartPosition`</span><span class="sxs-lookup"><span data-stu-id="ca5f3-104">enum `MCDUserNotificationReaderStartPosition`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReaderStartPosition)
```

<span data-ttu-id="ca5f3-105">リーダーの新しい変更が開始される位置 (新しい受信ユーザー通知または新しい受信状態の更新) を決定する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="ca5f3-105">Contains values that determines the position where any new change in the reader starts – new incoming user notification or new incoming state updates.</span></span> 

|<span data-ttu-id="ca5f3-106">名前</span><span class="sxs-lookup"><span data-stu-id="ca5f3-106">Name</span></span> | <span data-ttu-id="ca5f3-107">値</span><span class="sxs-lookup"><span data-stu-id="ca5f3-107">Value</span></span> | <span data-ttu-id="ca5f3-108">説明</span><span class="sxs-lookup"><span data-stu-id="ca5f3-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="ca5f3-109">MCDUserNotificationReaderStartPositionBeginning</span><span class="sxs-lookup"><span data-stu-id="ca5f3-109">MCDUserNotificationReaderStartPositionBeginning</span></span> |<span data-ttu-id="ca5f3-110">0</span><span class="sxs-lookup"><span data-stu-id="ca5f3-110">0</span></span>| <span data-ttu-id="ca5f3-111">通知ストアの先頭の開始位置。</span><span class="sxs-lookup"><span data-stu-id="ca5f3-111">Start position at the beginning of the notification store.</span></span> |
|   <span data-ttu-id="ca5f3-112">MCDUserNotificationReaderStartPositionEnd</span><span class="sxs-lookup"><span data-stu-id="ca5f3-112">MCDUserNotificationReaderStartPositionEnd</span></span> | <span data-ttu-id="ca5f3-113">1</span><span class="sxs-lookup"><span data-stu-id="ca5f3-113">1</span></span>| <span data-ttu-id="ca5f3-114">通知ストアの最後の開始位置。</span><span class="sxs-lookup"><span data-stu-id="ca5f3-114">Start position at the end of the notification store.</span></span> |
