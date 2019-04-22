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
# <a name="class-mcdconnecteddevicesaccesstokenrequest"></a><span data-ttu-id="38a8d-104">クラス `MCDConnectedDevicesAccessTokenRequest`</span><span class="sxs-lookup"><span data-stu-id="38a8d-104">class `MCDConnectedDevicesAccessTokenRequest`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenRequest : NSObject
```  
<span data-ttu-id="38a8d-105">包含されるスコープを満たす包含 MCDConnectedDevicesAccount のアクセス トークンを要求します。</span><span class="sxs-lookup"><span data-stu-id="38a8d-105">Request for an access token for the contained MCDConnectedDevicesAccount which satisfies the contained scopes.</span></span>

## <a name="properties"></a><span data-ttu-id="38a8d-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="38a8d-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="38a8d-107">アカウント</span><span class="sxs-lookup"><span data-stu-id="38a8d-107">account</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="38a8d-108">この MCDConnectedDevicesAccessTokenInvalidatedEventArgs に関連付けられているアカウント。</span><span class="sxs-lookup"><span data-stu-id="38a8d-108">The Account associated with this MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span></span>

### <a name="scopes"></a><span data-ttu-id="38a8d-109">スコープ</span><span class="sxs-lookup"><span data-stu-id="38a8d-109">scopes</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

<span data-ttu-id="38a8d-110">トークンを生成されたときに対応する必要がありますスコープのリスト。</span><span class="sxs-lookup"><span data-stu-id="38a8d-110">The list of scopes for which the token must cover when generated.</span></span>

## <a name="methods"></a><span data-ttu-id="38a8d-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="38a8d-111">Methods</span></span>

### <a name="completewithaccesstoken"></a><span data-ttu-id="38a8d-112">completeWithAccessToken</span><span class="sxs-lookup"><span data-stu-id="38a8d-112">completeWithAccessToken</span></span>
`- (void) completeWithAccessToken:(NSString* _Nonnull) token;`

<span data-ttu-id="38a8d-113">要求されたスコープを持つトークンが正常に生成された場合、は、トークン要求を完了するには、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="38a8d-113">If a token with the requested scopes was successfully generated, call this method with the token to complete the request.</span></span>

#### <a name="parameters"></a><span data-ttu-id="38a8d-114">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38a8d-114">Parameters</span></span> 
* `token` 

<span data-ttu-id="38a8d-115">正常に生成されたトークン</span><span class="sxs-lookup"><span data-stu-id="38a8d-115">Successfully generated token</span></span>

### <a name="completewitherrormessage"></a><span data-ttu-id="38a8d-116">completeWithErrorMessage</span><span class="sxs-lookup"><span data-stu-id="38a8d-116">completeWithErrorMessage</span></span>
`- (void) completeWithErrorMessage:(NSString* _Nullable) errorMessage;`

<span data-ttu-id="38a8d-117">要求されたスコープを持つトークンは、何らかの理由で正常に生成されなかった場合は、メッセージ ログ記録に使用するには、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="38a8d-117">If a token with the requested scopes was not successfully generated for any reason, call this method with a message to be used for logging.</span></span>

#### <a name="parameters"></a><span data-ttu-id="38a8d-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="38a8d-118">Parameters</span></span> 
* `errorMessage`

<span data-ttu-id="38a8d-119">トークンが成功した理由を説明するメッセージ。</span><span class="sxs-lookup"><span data-stu-id="38a8d-119">A message describing why the token was unsuccessful.</span></span>