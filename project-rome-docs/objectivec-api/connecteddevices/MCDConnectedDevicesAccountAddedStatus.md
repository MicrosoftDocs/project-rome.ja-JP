---
title: MCDConnectedDevicesAccountAddedStatus
description: MCDConnectedDevicesAccountAddedStatus 列挙型について説明します。 この列挙には、アカウントの追加操作の状態を表す値が含まれます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: f7ea80735a8df2138f2557ff2e7ab4db0b4a9800
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761036"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a>enum `MCDConnectedDevicesAccountAddedStatus`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
アカウントの追加操作の状態を示す値を格納します。

## <a name="fields"></a>フィールド

| 名前                              |   [値]     | 説明 |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesAccountAddedStatusSuccess | 0 | アカウントがプラットフォームに正常に追加されました。 |
| MCDConnectedDevicesAccountAddedStatusErrorNoNetwork | 1 | ローマがネットワークアクセスを検出しなかったため、アカウント操作に失敗しました。 |
| MCDConnectedDevicesAccountAddedStatusErrorServiceFailed | 2 | ローマが web サービスに接続できなかったため、アカウント操作に失敗しました。 |
| MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber | 3 | アプリが AccessTokenRequested イベントをサブスクライブしていなかったため、アカウント操作に失敗しました。 |
| MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed | 4 | アプリが要求されたときにトークンを返すことができなかったため、アカウント操作に失敗しました。 |
| MCDConnectedDevicesAccountAddedStatusErrorUnknown | 5 | 不明な理由により、アカウント操作に失敗しました。 |
