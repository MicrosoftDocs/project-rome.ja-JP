---
title: MCDRemoteSystemConnectionInfo
description: さらに、指定された MCDAppServiceConnection インスタンスに関する情報を提供するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: cdfe9dec49e90013f8c967223803144ad655378e
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801404"
---
# <a name="class-mcdremotesystemconnectioninfo"></a>クラス `MCDRemoteSystemConnectionInfo` 

```
@interface MCDRemoteSystemConnectionInfo : NSObject
```  

に関する情報を提供するクラスを指定した **[MCDAppServiceConnection](MCDAppServiceConnection.md)** インスタンス。

## <a name="properties"></a>プロパティ

### <a name="proximal"></a>位
`@property(nonatomic, readonly, getter=isProximal) BOOL proximal;`

位の接続に関連付けられているかどうかが表示されます (**はい**) かどうか (**いいえ**)。

## <a name="constructors"></a>コンストラクター

### <a name="trycreatefromappserviceconnection"></a>tryCreateFromAppServiceConnection
`+ (nullable instancetype)tryCreateFromAppServiceConnection:(nonnull MCDAppServiceConnection*)appServiceConnection;`

特定のアプリ サービスの接続からは、このクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `appServiceConnection` 

**MCDAppServiceConnection**インスタンス。

#### <a name="returns"></a>戻り値
アプリ サービスの接続に対応するこのクラスのインスタンスを返します。