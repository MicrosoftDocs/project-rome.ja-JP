---
title: MCDConnectedDevicesAccessTokenInvalidatedEventArgs
description: トークンのエラーを報告しました ConnectedDevicesAccount に関連付けられているそのトークンを通知します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 46a21b534e2b3a5fb588e40af2dbc4eb47143873
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907494"
---
# <a name="class-mcdconnecteddevicesaccesstokeninvalidatedeventargs"></a><span data-ttu-id="fb275-104">クラス `MCDConnectedDevicesAccessTokenInvalidatedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="fb275-104">class `MCDConnectedDevicesAccessTokenInvalidatedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenInvalidatedEventArgs : NSObject 
```  
<span data-ttu-id="fb275-105">MCDConnectedDevicesAccount MCDConnectedDevicesAccount に関連付けられているトークンに、包含されるスコープのトークンのエラーが報告されることを通知するためにによって返されます。</span><span class="sxs-lookup"><span data-stu-id="fb275-105">Returned by MCDConnectedDevicesAccount to inform that the token associated with MCDConnectedDevicesAccount reported token error for the contained scopes.</span></span> <span data-ttu-id="fb275-106">トークン プロバイダーは、トークン キャッシュを更新するか、可能性のあるユーザーにそのアカウントのセットアップを修正するにはサインインを要求する UI をポップアップ表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb275-106">Token provider needs to either refresh their token cache or potentially pop up UI to ask user to sign in in order to fix their account setup.</span></span>

## <a name="properties"></a><span data-ttu-id="fb275-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fb275-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="fb275-108">アカウント</span><span class="sxs-lookup"><span data-stu-id="fb275-108">account</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="fb275-109">この MCDConnectedDevicesAccessTokenInvalidatedEventArgs に関連付けられているアカウント。</span><span class="sxs-lookup"><span data-stu-id="fb275-109">The Account associated with this MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span></span>

### <a name="scopes"></a><span data-ttu-id="fb275-110">スコープ</span><span class="sxs-lookup"><span data-stu-id="fb275-110">scopes</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

<span data-ttu-id="fb275-111">トークンを生成されたときに対応する必要がありますスコープのリスト。</span><span class="sxs-lookup"><span data-stu-id="fb275-111">The list of scopes for which the token must cover when generated.</span></span>