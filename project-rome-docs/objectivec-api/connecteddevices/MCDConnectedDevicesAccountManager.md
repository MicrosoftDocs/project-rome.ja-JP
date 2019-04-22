---
title: MCDConnectedDevicesAccountManager
description: SDK アカウントに関連するすべての機能の 1 つのエントリ ポイントを提供します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: c265a0c7114704ea6f9ae9818eb9abdb39b5437f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801644"
---
# <a name="class-mcdconnecteddevicesaccountmanager"></a>クラス `MCDConnectedDevicesAccountManager` 

```
@interface MCDConnectedDevicesAccountManager : NSObject
```  
SDK アカウントに関連するすべての機能の 1 つのエントリ ポイントを提供します。

## <a name="properties"></a>プロパティ

### <a name="accesstokenrequested"></a>accessTokenRequested
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenRequestedEventArgs*>* accessTokenRequested;`

このイベントは、トークンを要求する必要があるときに発生します。 このイベントは、サブスクライブしていると、すべての要求が送信される前に応答する準備が必要があります。

### <a name="accesstokeninvalidated"></a>accessTokenInvalidated
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenInvalidatedEventArgs*>* accessTokenInvalidated;`

このイベントは、トークンのコンシューマーは、トークンのエラーを報告したときに発生します。 トークン プロバイダーは、そのトークンのキャッシュを更新またはそのアカウントのセットアップを修正する新しいユーザー ログインを要求する必要があります。

### <a name="allaccounts"></a>allAccounts
`@property (nonatomic, readonly, nonnull) NSArray<MCDConnectedDevicesAccount*>* allAccounts;`

このマネージャーが現在追跡されているすべての MCDConnectedDevicesAccount します。

## <a name="methods"></a>メソッド

### <a name="addaccountasync"></a>addAccountAsync
`- (void) addAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesAddAccountResult* _Nonnull, NSError* _Nullable))callback;`

アカウントにアカウント管理者を追加、完了時にコールバックが呼び出されます。

#### <a name="parameters"></a>パラメーター 
* `callback`

コールバックの結果は、アカウントの追加が成功したかどうかを示します。 

### <a name="removeaccountasync"></a>removeAccountAsync
`- (void) removeAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesRemoveAccountResult* _Nonnull, NSError* _Nullable))callback;`

アカウント マネージャーからアカウントを削除、完了時にコールバックが呼び出されます。

#### <a name="parameters"></a>パラメーター 
* `callback` 

 コールバックの結果は、アカウントの削除が成功したかどうかを示します。 