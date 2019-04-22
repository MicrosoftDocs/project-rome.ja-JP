---
title: MCDConnectedDevicesAccount
description: このクラスは、アプリによって認識されている単一のユーザー アカウントを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: e9b43bb76e46f3a027247b1d4d564c6e1571bae4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800934"
---
# <a name="class-mcdconnecteddevicesaccount"></a>クラス `MCDConnectedDevicesAccount`

```
@interface MCDConnectedDevicesAccount : NSObject
```  

このクラスは、アプリによって認識されている単一のユーザー アカウントを表します。

## <a name="properties"></a>プロパティ

### <a name="anonymousaccount"></a>anonymousAccount
`+ (nullable instancetype)anonymousAccount;`

匿名アカウントのシングルトン インスタンス。

### <a name="accountid"></a>accountId
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

このユーザー アカウントの一意の識別子。

### <a name="type"></a>type
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

アカウントの種類を記述する MCDConnectedDevicesAccountType 値。

## <a name="constructors"></a>コンストラクター

### <a name="accountwithaccountid"></a>accountWithAccountId
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

このユーザー アカウントの一意の識別子では、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 

* `accountId` 

このユーザー アカウントの一意の識別子の文字列。

`type` 

アカウントの MCDConnectedDevicesAccountType (依存、アカウントがどの ID プロバイダーから)。

#### <a name="returns"></a>戻り値
アカウント識別子を含む MCDConnectedDevicesAccount オブジェクトを返します。

### <a name="initwithaccountid"></a>initWithAccountId
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

このユーザー アカウントの一意の識別子では、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `type`

アカウントの MCDConnectedDevicesAccountType (依存、アカウントがどの ID プロバイダーから)。

#### <a name="returns"></a>戻り値
アカウント識別子を使用して初期化 MCDConnectedDevicesAccount オブジェクトを返します。