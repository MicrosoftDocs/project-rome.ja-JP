---
title: MCDUserDataSyncStatus
description: 状態を記述する値が含まれています、  **[MCDUserDataFeed](MCDUserDataFeed.md)** の接続されているデバイス プラットフォームのバックエンドと同期します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 805192b0d9169c799f30b7daa0371767145ae86f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908624"
---
# <a name="enum-mcduserdatasyncstatus"></a><span data-ttu-id="cb700-104">列挙型 `MCDUserDataSyncStatus`</span><span class="sxs-lookup"><span data-stu-id="cb700-104">enum `MCDUserDataSyncStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserDataSyncStatus)
```

<span data-ttu-id="cb700-105">状態を記述する値が含まれています、  **[MCDUserDataFeed](MCDUserDataFeed.md)** の接続されているデバイス プラットフォームのバックエンドと同期します。</span><span class="sxs-lookup"><span data-stu-id="cb700-105">Contains values that describe the state of a **[MCDUserDataFeed](MCDUserDataFeed.md)**'s synchronization with the Connected Devices Platform backend.</span></span>

|<span data-ttu-id="cb700-106">名前</span><span class="sxs-lookup"><span data-stu-id="cb700-106">Name</span></span> | <span data-ttu-id="cb700-107">値</span><span class="sxs-lookup"><span data-stu-id="cb700-107">Value</span></span> | <span data-ttu-id="cb700-108">説明</span><span class="sxs-lookup"><span data-stu-id="cb700-108">Description</span></span> |
|:-- |:-- |:-- |
|  <span data-ttu-id="cb700-109">MCDUserDataFeedSyncStatusQueued</span><span class="sxs-lookup"><span data-stu-id="cb700-109">MCDUserDataFeedSyncStatusQueued</span></span> |<span data-ttu-id="cb700-110">0</span><span class="sxs-lookup"><span data-stu-id="cb700-110">0</span></span>| <span data-ttu-id="cb700-111">データがまだ同期されていません。</span><span class="sxs-lookup"><span data-stu-id="cb700-111">The data is not yet synchronized.</span></span> |
| <span data-ttu-id="cb700-112">MCDUserDataFeedSyncStatusSynchronized</span><span class="sxs-lookup"><span data-stu-id="cb700-112">MCDUserDataFeedSyncStatusSynchronized</span></span> |<span data-ttu-id="cb700-113">1</span><span class="sxs-lookup"><span data-stu-id="cb700-113">1</span></span>| <span data-ttu-id="cb700-114">データが同期されています。</span><span class="sxs-lookup"><span data-stu-id="cb700-114">The data has been synchronized.</span></span>|