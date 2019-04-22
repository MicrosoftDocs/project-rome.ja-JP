---
title: MCDUserDataSyncStatus
description: 状態を記述する値が含まれています、  **[MCDUserDataFeed](MCDUserDataFeed.md)** の接続されているデバイス プラットフォームのバックエンドと同期します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 805192b0d9169c799f30b7daa0371767145ae86f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801414"
---
# <a name="enum-mcduserdatasyncstatus"></a><span data-ttu-id="cf7eb-104">列挙型 `MCDUserDataSyncStatus`</span><span class="sxs-lookup"><span data-stu-id="cf7eb-104">enum `MCDUserDataSyncStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserDataSyncStatus)
```

<span data-ttu-id="cf7eb-105">状態を記述する値が含まれています、  **[MCDUserDataFeed](MCDUserDataFeed.md)** の接続されているデバイス プラットフォームのバックエンドと同期します。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-105">Contains values that describe the state of a **[MCDUserDataFeed](MCDUserDataFeed.md)**'s synchronization with the Connected Devices Platform backend.</span></span>

|<span data-ttu-id="cf7eb-106">名前</span><span class="sxs-lookup"><span data-stu-id="cf7eb-106">Name</span></span> | <span data-ttu-id="cf7eb-107">値</span><span class="sxs-lookup"><span data-stu-id="cf7eb-107">Value</span></span> | <span data-ttu-id="cf7eb-108">説明</span><span class="sxs-lookup"><span data-stu-id="cf7eb-108">Description</span></span> |
|:-- |:-- |:-- |
|  <span data-ttu-id="cf7eb-109">MCDUserDataFeedSyncStatusQueued</span><span class="sxs-lookup"><span data-stu-id="cf7eb-109">MCDUserDataFeedSyncStatusQueued</span></span> |<span data-ttu-id="cf7eb-110">0</span><span class="sxs-lookup"><span data-stu-id="cf7eb-110">0</span></span>| <span data-ttu-id="cf7eb-111">データがまだ同期されていません。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-111">The data is not yet synchronized.</span></span> |
| <span data-ttu-id="cf7eb-112">MCDUserDataFeedSyncStatusSynchronized</span><span class="sxs-lookup"><span data-stu-id="cf7eb-112">MCDUserDataFeedSyncStatusSynchronized</span></span> |<span data-ttu-id="cf7eb-113">1</span><span class="sxs-lookup"><span data-stu-id="cf7eb-113">1</span></span>| <span data-ttu-id="cf7eb-114">データが同期されています。</span><span class="sxs-lookup"><span data-stu-id="cf7eb-114">The data has been synchronized.</span></span>|