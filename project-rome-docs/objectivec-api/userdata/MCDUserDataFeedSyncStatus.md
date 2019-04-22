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
# <a name="enum-mcduserdatasyncstatus"></a>列挙型 `MCDUserDataSyncStatus`

```
typedef NS_ENUM(NSInteger, MCDUserDataSyncStatus)
```

状態を記述する値が含まれています、  **[MCDUserDataFeed](MCDUserDataFeed.md)** の接続されているデバイス プラットフォームのバックエンドと同期します。

|名前 | 値 | 説明 |
|:-- |:-- |:-- |
|  MCDUserDataFeedSyncStatusQueued |0| データがまだ同期されていません。 |
| MCDUserDataFeedSyncStatusSynchronized |1| データが同期されています。|