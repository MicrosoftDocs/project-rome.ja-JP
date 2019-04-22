---
title: MCDConnectedDevicesAccessTokenRequest
description: 包含されるスコープを満たす包含 MCDConnectedDevicesAccount のアクセス トークンを要求します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: b1cd9b747e98d5e9ccf4885b33897e8c240d7673
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800834"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequest"></a>クラス `MCDConnectedDevicesAccessTokenRequest` 

```
@interface MCDConnectedDevicesAccessTokenRequest : NSObject
```  
包含されるスコープを満たす包含 MCDConnectedDevicesAccount のアクセス トークンを要求します。

## <a name="properties"></a>プロパティ

### <a name="account"></a>アカウント
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

この MCDConnectedDevicesAccessTokenInvalidatedEventArgs に関連付けられているアカウント。

### <a name="scopes"></a>スコープ
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

トークンを生成されたときに対応する必要がありますスコープのリスト。

## <a name="methods"></a>メソッド

### <a name="completewithaccesstoken"></a>completeWithAccessToken
`- (void) completeWithAccessToken:(NSString* _Nonnull) token;`

要求されたスコープを持つトークンが正常に生成された場合、は、トークン要求を完了するには、このメソッドを呼び出します。

#### <a name="parameters"></a>パラメーター 
* `token` 

正常に生成されたトークン

### <a name="completewitherrormessage"></a>completeWithErrorMessage
`- (void) completeWithErrorMessage:(NSString* _Nullable) errorMessage;`

要求されたスコープを持つトークンは、何らかの理由で正常に生成されなかった場合は、メッセージ ログ記録に使用するには、このメソッドを呼び出します。

#### <a name="parameters"></a>パラメーター 
* `errorMessage`

トークンが成功した理由を説明するメッセージ。