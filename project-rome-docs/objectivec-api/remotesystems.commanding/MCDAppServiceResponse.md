---
title: MCDAppServiceResponse
description: 接続されたリモート アプリ サービスから受信した応答を表すクラス。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 74cff4a84bdc4bf073dd57319c987e274ea8ceaf
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909204"
---
# <a name="class-mcdappserviceresponse"></a>クラス `MCDAppServiceResponse`

```
@interface MCDAppServiceResponse : NSObject
```

接続されたリモート アプリ サービスから受信した応答を表すクラス。

## <a name="properties"></a>プロパティ

### <a name="message"></a>メッセージ 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

リモート アプリ サービスから受信したメッセージ。

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDAppServiceResponseStatus status;`

受信した応答の状態です。