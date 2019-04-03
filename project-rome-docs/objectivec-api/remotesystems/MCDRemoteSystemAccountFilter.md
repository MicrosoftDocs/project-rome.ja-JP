---
title: MCDRemoteSystemAccountFilter
description: リモート システムを検出するアカウントを返すフィルター。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 34721c2dee89adc380b721a027382f81c2ecb751
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907324"
---
# <a name="class-mcdremotesystemaccountfilter"></a>クラス `MCDRemoteSystemAccountFilter` 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

リモート システムを検出するアカウントを返すフィルター。

## <a name="properties"></a>プロパティ

### <a name="account"></a>アカウント
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
アカウントを使ってフィルター選択 MCDRemoteSystemAccountFilter オブジェクトを返します。

### <a name="initwithaccount"></a>initWithAccount
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

MCDConnectedDevicesAccount アカウントを使用してクラスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `account` 

使用されている MCDConnectedDevicesAccount アカウント。

#### <a name="returns"></a>戻り値
MCDRemoteSystemAccountFilter オブジェクトを返します。 アカウントを使用してフィルター処理されます。