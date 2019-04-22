---
title: MCDRemoteSystemStatus
description: リモート システムの可用性を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 4a69961b12def736733e1b6a78d376d57b2fa33f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801374"
---
# <a name="enum-mcdremotesystemstatus"></a>列挙型 `MCDRemoteSystemStatus` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
リモート システムの可用性を記述する値が含まれています。 IOS アプリの値に**MCDRemoteSystemStatusUnknown**は常に発生する; 他の値は Windows システムで利用できるのみです。

## <a name="fields"></a>フィールド

| 名前                              | 値 | 説明                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemStatusUnavailable | 0 | リモート システムが利用不可と報告されます。 |
| MCDRemoteSystemStatusDiscoveringAvailablilty | 1 | リモート システムのステータスを特定する複素数 (検出プロセス中に発生します)。 |
| MCDRemoteSystemStatusAvailable | 2 | リモート システムが利用可能として報告されます。 |
| MCDRemoteSystemStatusUnknown | 3 | 状態が不明です。 |
