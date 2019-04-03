---
title: MCDConnectedDevicesAccountAddedStatus
description: 追加アカウントの操作の状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907204"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a>列挙型 `MCDConnectedDevicesAccountAddedStatus`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
追加アカウントの操作の状態を記述する値が含まれています。

## <a name="fields"></a>フィールド

| 名前                              |   値     | 説明 |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesAccountAddedStatusSuccess | 0 | アカウントは、プラットフォームに正常に追加されました。 |
| MCDConnectedDevicesAccountAddedStatusErrorNoNetwork | 1 | ローマにネットワーク アクセスが検出されないために、アカウントの操作が失敗しました。 |
| MCDConnectedDevicesAccountAddedStatusErrorServiceFailed | 2 | ローマで web サービスにお問い合わせできなかったために、アカウントの操作が失敗しました。 |
| MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber | 3 | アカウントの操作では、アプリが AccessTokenRequested イベントをサブスクライブしていないために失敗しました。 |
| MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed | 4 | 要求されたときに、トークンをアプリが失敗したため、アカウントの操作が失敗しました。 |
| MCDConnectedDevicesAccountAddedStatusErrorUnknown | 5 | 不明な理由により、アカウントの操作が失敗しました。 |
