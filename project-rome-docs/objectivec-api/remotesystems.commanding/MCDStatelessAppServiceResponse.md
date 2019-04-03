---
title: MCDStatelessAppServiceResponse
description: リモート アプリ サービスから MCDAppServiceConnection.sendStatelessMessageAsync 以前の呼び出しへの応答でクライアント アプリに渡されるメッセージを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 4e650b1b114a3cb05b2d9b03b833b9e1cdd6607c
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907234"
---
# <a name="class-mcdstatelessappserviceresponse"></a>クラス `MCDStatelessAppServiceResponse` 

```
@interface MCDStatelessAppServiceResponse : NSObject
```  

リモート アプリ サービスから MCDAppServiceConnection.sendStatelessMessageAsync 以前の呼び出しへの応答でクライアント アプリに渡されるメッセージを表します。


## <a name="properties"></a>プロパティ

### <a name="message"></a>メッセージ
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

キー/値ペアから成る、リモート アプリ サービスによって送信されるメッセージ。

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDStatelessAppServiceResponseStatus status;`

リモート アプリ サービスからの応答のステータス。

