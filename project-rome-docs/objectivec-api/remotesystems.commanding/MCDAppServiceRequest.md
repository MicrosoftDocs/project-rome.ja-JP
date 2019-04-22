---
title: MCDAppServiceRequest
description: リモート アプリ/デバイスからこのアプリ サービスの接続を受信したメッセージを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 553403ab57b594294072dc082f5646eb1646e55b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800534"
---
# <a name="class-mcdappservicerequest"></a>クラス `MCDAppServiceRequest`

```
@interface MCDAppServiceRequest : NSObject
```
リモート アプリ/デバイスからこのアプリ サービスの接続を受信したメッセージを表します。

## <a name="properties"></a>プロパティ

### <a name="message"></a>メッセージ 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

リモート アプリ サービスのメッセージ。

## <a name="methods"></a>メソッド

### <a name="sendresponseasync"></a>sendResponseAsync 
```
- (void)sendResponseAsync:(nonnull NSDictionary*)message
               completion:(nonnull void (^)(MCDAppServiceResponseStatus, NSError* _Nullable))completion;
```

要求を送信したリモートの app service への応答メッセージを送信します。

#### <a name="parameters"></a>パラメーター
* `message` 

リモート アプリ サービスのメッセージ。

* `completion`     

送信操作の状態を示す MCDAppServiceResponseStatus 値を持つ非同期の操作を完了します。