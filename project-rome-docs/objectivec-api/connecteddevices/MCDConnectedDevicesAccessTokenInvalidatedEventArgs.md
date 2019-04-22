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
# <a name="class-mcdconnecteddevicesaccesstokeninvalidatedeventargs"></a><span data-ttu-id="b535f-104">クラス `MCDConnectedDevicesAccessTokenInvalidatedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="b535f-104">class `MCDConnectedDevicesAccessTokenInvalidatedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenInvalidatedEventArgs : NSObject 
```  
<span data-ttu-id="b535f-105">MCDConnectedDevicesAccount MCDConnectedDevicesAccount に関連付けられているトークンに、包含されるスコープのトークンのエラーが報告されることを通知するためにによって返されます。</span><span class="sxs-lookup"><span data-stu-id="b535f-105">Returned by MCDConnectedDevicesAccount to inform that the token associated with MCDConnectedDevicesAccount reported token error for the contained scopes.</span></span> <span data-ttu-id="b535f-106">トークン プロバイダーは、トークン キャッシュを更新するか、可能性のあるユーザーにそのアカウントのセットアップを修正するにはサインインを要求する UI をポップアップ表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b535f-106">Token provider needs to either refresh their token cache or potentially pop up UI to ask user to sign in in order to fix their account setup.</span></span>

## <a name="properties"></a><span data-ttu-id="b535f-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b535f-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="b535f-108">アカウント</span><span class="sxs-lookup"><span data-stu-id="b535f-108">account</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="b535f-109">この MCDConnectedDevicesAccessTokenInvalidatedEventArgs に関連付けられているアカウント。</span><span class="sxs-lookup"><span data-stu-id="b535f-109">The Account associated with this MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span></span>

### <a name="scopes"></a><span data-ttu-id="b535f-110">スコープ</span><span class="sxs-lookup"><span data-stu-id="b535f-110">scopes</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

<span data-ttu-id="b535f-111">トークンを生成されたときに対応する必要がありますスコープのリスト。</span><span class="sxs-lookup"><span data-stu-id="b535f-111">The list of scopes for which the token must cover when generated.</span></span>