---
title: MCDConnectedDevicesAccount
description: MCDConnectedDevicesAccount クラスについて説明します。 このクラスは、アプリによって認識される1つのユーザーアカウントを表します。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: b3004681c2bcbb0ad9d5b1dcb15fe8a711773767
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761046"
---
# <a name="class-mcdconnecteddevicesaccount"></a>講義 `MCDConnectedDevicesAccount`

```
@interface MCDConnectedDevicesAccount : NSObject
```  

このクラスは、アプリによって認識される1つのユーザーアカウントを表します。

## <a name="properties"></a>Properties

### <a name="anonymousaccount"></a>anonymousAccount
`+ (nullable instancetype)anonymousAccount;`

匿名アカウントのシングルトンインスタンス。

### <a name="accountid"></a>accountId
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

このユーザーアカウントの一意の識別子。

### <a name="type"></a>型
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

アカウントの種類を記述する MCDConnectedDevicesAccountType 値。

## <a name="constructors"></a>コンストラクター

### <a name="accountwithaccountid"></a>accountWithAccountId
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

このユーザーアカウントの一意の識別子を持つ、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 

* `accountId` 

このユーザーアカウントの一意の識別子文字列。

`type` 

アカウントの MCDConnectedDevicesAccountType (アカウントの元の ID プロバイダーによって異なります)。

#### <a name="returns"></a>戻り値
アカウント識別子を持つ MCDConnectedDevicesAccount オブジェクトを返します。

### <a name="initwithaccountid"></a>initWithAccountId
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

このユーザーアカウントの一意の識別子を持つ、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `type`

アカウントの MCDConnectedDevicesAccountType (アカウントの元の ID プロバイダーによって異なります)。

#### <a name="returns"></a>戻り値
アカウント識別子を使用して初期化された MCDConnectedDevicesAccount オブジェクトを返します。