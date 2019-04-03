---
title: MCDAppServiceConnectionOpenedInfo
description: このクラスは、リモート デバイスが、ローカルの app service への接続を開いたときに発生しますが、MCDAppServiceProvider.connectionDidOpen イベントのデータを提供します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: b700c95d7ab093b47a94c856c25b946fc5df12d7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907554"
---
# <a name="class-mcdappserviceconnectionopenedinfo"></a>クラス `MCDAppServiceConnectionOpenedInfo` 

```
@interface MCDAppServiceConnectionOpenedInfo : NSObject
```  

このクラスは、リモート デバイスが、ローカルの app service への接続を開いたときに発生しますが、MCDAppServiceProvider.connectionDidOpen イベントのデータを提供します。

## <a name="properties"></a>プロパティ

### <a name="appserviceconnection"></a>appServiceConnection
`@property(nonatomic, readonly, nonnull) MCDAppServiceConnection* appServiceConnection;`

ローカル アプリ サービスとリモート デバイス間の接続を表す MCDAppServiceConnection インスタンス。

### <a name="remotesystemapp"></a>RemoteSystemApp
`@property(nonatomic, readonly, nullable) MCDRemoteSystemApp* remoteSystemApp;`

ローカルの app service への接続を開始した MCDRemoteSystemApp リモート アプリケーションです。