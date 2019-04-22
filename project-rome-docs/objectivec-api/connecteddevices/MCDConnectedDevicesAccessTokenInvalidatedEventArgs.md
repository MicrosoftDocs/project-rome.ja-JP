---
title: MCDConnectedDevicesAccessTokenInvalidatedEventArgs
description: トークンのエラーを報告しました ConnectedDevicesAccount に関連付けられているそのトークンを通知します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 46a21b534e2b3a5fb588e40af2dbc4eb47143873
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801774"
---
# <a name="class-mcdconnecteddevicesaccesstokeninvalidatedeventargs"></a>クラス `MCDConnectedDevicesAccessTokenInvalidatedEventArgs` 

```
@interface MCDConnectedDevicesAccessTokenInvalidatedEventArgs : NSObject 
```  
MCDConnectedDevicesAccount MCDConnectedDevicesAccount に関連付けられているトークンに、包含されるスコープのトークンのエラーが報告されることを通知するためにによって返されます。 トークン プロバイダーは、トークン キャッシュを更新するか、可能性のあるユーザーにそのアカウントのセットアップを修正するにはサインインを要求する UI をポップアップ表示する必要があります。

## <a name="properties"></a>プロパティ

### <a name="account"></a>アカウント
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

この MCDConnectedDevicesAccessTokenInvalidatedEventArgs に関連付けられているアカウント。

### <a name="scopes"></a>スコープ
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

トークンを生成されたときに対応する必要がありますスコープのリスト。