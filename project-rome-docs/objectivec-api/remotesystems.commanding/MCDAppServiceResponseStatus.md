---
title: MCDAppServiceResponseStatus
description: リモート アプリ サービスから応答メッセージの状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 395c2669af7178ef90ff7fd2dc8bafe9b1044028
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908944"
---
# <a name="enum-mcdappserviceresponsestatus"></a>列挙型 `MCDAppServiceResponseStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceResponseStatus)
```

リモート アプリ サービスから応答メッセージの状態を記述する値が含まれています。

|名前         | 値  | 説明    |                           
|--------|-------------|-----|
|MCDAppServiceResponseStatusSuccess |0| App service は正常に受信し、メッセージを処理します。|
|MCDAppServiceResponseStatusFailure |1| App service は、受信とメッセージを処理できませんでした。|
|MCDAppServiceResponseStatusResourceLimitsExceeded |2| App service では、十分なリソースが使用可能なために終了しました。|
|MCDAppServiceResponseStatusUnknown |3| 不明なエラーが発生しました。|
|MCDAppServiceResponseStatusRemoteSystemUnavailable |4| メッセージの送信、デバイスは、ご利用いただけません。|
|MCDAppServiceResponseStatusMessageTooLarge |5| App service が大きすぎるため、メッセージを処理できませんでした。|
|MCDAppServiceResponseStatusAppServiceConnectionClosed|6| 応答が送信される前に、アプリ サービスの接続が閉じられました。|