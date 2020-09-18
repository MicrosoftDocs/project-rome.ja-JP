---
title: MCDRemoteSystemAccountFilter
description: "\"FilterwithAccount\" のようなコンストラクターを使用して、リモートシステムを検出するためにアカウントをフィルター処理する方法について説明します。"
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 3a32c318aba49eff550ccfdf51049fd97a34e2f5
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760726"
---
# <a name="class-mcdremotesystemaccountfilter"></a>講義 `MCDRemoteSystemAccountFilter` 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

でリモートシステムを探索するためのアカウントをフィルター処理します。

## <a name="properties"></a>Properties

### <a name="account"></a>account
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

この MCDRemoteSystemAccountFilter に関連付けられているアカウント。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithaccount"></a>filterWithAccount
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

MCDConnectedDevicesAccount アカウントを使用してクラスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `account` 

使用されている MCDConnectedDevicesAccount アカウント。

#### <a name="returns"></a>戻り値
アカウントを使用してフィルター処理された MCDRemoteSystemAccountFilter オブジェクトを返します。

### <a name="initwithaccount"></a>initWithAccount
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

MCDConnectedDevicesAccount アカウントを使用してクラスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `account` 

使用されている MCDConnectedDevicesAccount アカウント。

#### <a name="returns"></a>戻り値
アカウントでフィルター処理された MCDRemoteSystemAccountFilter オブジェクトを返します。