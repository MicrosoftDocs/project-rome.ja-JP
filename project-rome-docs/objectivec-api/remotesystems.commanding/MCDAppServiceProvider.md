---
title: MCDAppServiceProvider
description: このプロトコルには、ローカル アプリ サービスをリモート デバイスにアクセスできるようにするためのメソッドが含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: f5af56a2c87e3b4335a2a59a0130ef3622af6c26
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908664"
---
# <a name="protocol-mcdappserviceprovider"></a>プロトコル `MCDAppServiceProvider`

```
@protocol MCDAppServiceProvider<NSObject>
```

このプロトコルには、ローカル アプリ サービスをリモート デバイスにアクセスできるようにするためのメソッドが含まれています。 開発者は、アプリ サービスをリモート接続に使用できるようにするには、このプロトコルを実装する必要があります。

## <a name="properties"></a>プロパティ
 
### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, readonly, strong, nonnull) MCDAppServiceInfo* appServiceInfo;`

この app service についての説明。

## <a name="methods"></a>メソッド

### <a name="connectiondidopen"></a>connectionDidOpen
`- (void)connectionDidOpen:(nonnull MCDAppServiceConnectionOpenedInfo*)openedInfo;`

この app service にアプリのリモート サービスの接続を開いたときに、このメソッドが呼び出されます。

#### <a name="parameters"></a>パラメーター 
* `openedInfo`

App service でリモート メッセージの情報を含む MDCAppServiceConnectionOpenedInfo インスタンス。