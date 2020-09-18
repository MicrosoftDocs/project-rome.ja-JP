---
title: MCDRemoteSystemStatus
description: MCDRemoteSystemStatus 列挙型について説明します。 この列挙には、リモートシステムの可用性を表す値が含まれます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 71e4216c949506f45f26a7c035ff043a55168b23
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760656"
---
# <a name="enum-mcdremotesystemstatus"></a>enum `MCDRemoteSystemStatus` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
リモートシステムの可用性を示す値を格納します。 IOS アプリでは、 **MCDRemoteSystemStatusUnknown** の値が常に検出されます。その他の値は、Windows システムでのみ使用できます。

## <a name="fields"></a>フィールド

| 名前                              | [値] | 説明                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemStatusUnavailable | 0 | リモートシステムは使用不可として報告されます。 |
| MCDRemoteSystemStatusDiscoveringAvailablilty | 1 | リモートシステムの状態が特定されている (検出プロセス中に発生する)。 |
| MCDRemoteSystemStatusAvailable | 2 | リモートシステムが使用可能として報告されます。 |
| MCDRemoteSystemStatusUnknown | 3 | 状態が不明です。 |
