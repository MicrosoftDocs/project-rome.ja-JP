---
title: MCDRemoteSystemConnectionRequest
description: 特定のリモート デバイスやアプリケーションとの通信の試行を表すクラス。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 54ed7deb1fa2b1c87a3195e61c2ce031d6e0cea9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907134"
---
# <a name="class-mcdremotesystemconnectionrequest"></a>クラス `MCDRemoteSystemConnectionRequest` 

```
@interface MCDRemoteSystemConnectionRequest : NSObject
```  

特定のリモート デバイスやアプリケーションとの通信の試行を表すクラス。

## <a name="constructors"></a>コンストラクター

### <a name="requestwithremotesystem"></a>requestWithRemoteSystem
`+ (instancetype)requestWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

初期化します、 [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)で、 [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md)インスタンス。 このコンス トラクターは推奨されませんがターゲットにアプリを指定しないと、システムに送信された要求をサービスに選択されている、予期しないアプリのため可能性があります。

#### <a name="parameters"></a>パラメーター
* `remoteSystem` 

この接続要求の対象とするリモート システム。

#### <a name="returns"></a>戻り値
返しますが、初期化された[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)成功した場合、それ以外の場合の nil します。

### <a name="requestwithremotesystemapp"></a>requestWithRemoteSystemApp
`+ (instancetype)requestWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

作成し、このクラスの新しいインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター
* `remoteSystemApp` 

この接続要求の対象とするリモート アプリ。

#### <a name="returns"></a>戻り値
返しますが、初期化された[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)成功した場合、それ以外の場合の nil します。

### <a name="initwithremotesystem"></a>initWithRemoteSystem
`- (nullable instancetype)initWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

初期化します、 [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)で、 [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md)インスタンス。 このコンス トラクターは推奨されませんがターゲットにアプリを指定しないと、システムに送信された要求をサービスに選択されている、予期しないアプリのため可能性があります。

#### <a name="parameters"></a>パラメーター
* `remoteSystem` この接続要求の対象とするリモート システム。

#### <a name="returns"></a>戻り値
返しますが、初期化された[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)成功した場合、それ以外の場合の nil します。

### <a name="initwithremotesystemapp"></a>initWithRemoteSystemApp
`- (nullable instancetype)initWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

作成し、このクラスの新しいインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター
* `remoteSystemApp` 

この接続要求の対象とするリモート アプリ。

#### <a name="returns"></a>戻り値
返しますが、初期化された[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)成功した場合、それ以外の場合の nil します。