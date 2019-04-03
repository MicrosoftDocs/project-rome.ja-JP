---
title: MCDConnectedDevicesAccountManager
description: SDK アカウントに関連するすべての機能の 1 つのエントリ ポイントを提供します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: c265a0c7114704ea6f9ae9818eb9abdb39b5437f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908394"
---
# <a name="class-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="34e03-104">クラス `MCDConnectedDevicesAccountManager`</span><span class="sxs-lookup"><span data-stu-id="34e03-104">class `MCDConnectedDevicesAccountManager`</span></span> 

```
@interface MCDConnectedDevicesAccountManager : NSObject
```  
<span data-ttu-id="34e03-105">SDK アカウントに関連するすべての機能の 1 つのエントリ ポイントを提供します。</span><span class="sxs-lookup"><span data-stu-id="34e03-105">Provides a single entrypoint for all account-related features in the SDK.</span></span>

## <a name="properties"></a><span data-ttu-id="34e03-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="34e03-106">Properties</span></span>

### <a name="accesstokenrequested"></a><span data-ttu-id="34e03-107">accessTokenRequested</span><span class="sxs-lookup"><span data-stu-id="34e03-107">accessTokenRequested</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenRequestedEventArgs*>* accessTokenRequested;`

<span data-ttu-id="34e03-108">このイベントは、トークンを要求する必要があるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="34e03-108">This event is fired when there is a need to request a token.</span></span> <span data-ttu-id="34e03-109">このイベントは、サブスクライブしていると、すべての要求が送信される前に応答する準備が必要があります。</span><span class="sxs-lookup"><span data-stu-id="34e03-109">This event should be subscribed and ready to respond before any request is sent out.</span></span>

### <a name="accesstokeninvalidated"></a><span data-ttu-id="34e03-110">accessTokenInvalidated</span><span class="sxs-lookup"><span data-stu-id="34e03-110">accessTokenInvalidated</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenInvalidatedEventArgs*>* accessTokenInvalidated;`

<span data-ttu-id="34e03-111">このイベントは、トークンのコンシューマーは、トークンのエラーを報告したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="34e03-111">This event is fired when a token consumer reports a token error.</span></span> <span data-ttu-id="34e03-112">トークン プロバイダーは、そのトークンのキャッシュを更新またはそのアカウントのセットアップを修正する新しいユーザー ログインを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34e03-112">The token provider needs to either refresh their token cache or request a new user login to fix their account setup.</span></span>

### <a name="allaccounts"></a><span data-ttu-id="34e03-113">allAccounts</span><span class="sxs-lookup"><span data-stu-id="34e03-113">allAccounts</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<MCDConnectedDevicesAccount*>* allAccounts;`

<span data-ttu-id="34e03-114">このマネージャーが現在追跡されているすべての MCDConnectedDevicesAccount します。</span><span class="sxs-lookup"><span data-stu-id="34e03-114">All MCDConnectedDevicesAccount which are currently tracked by this manager.</span></span>

## <a name="methods"></a><span data-ttu-id="34e03-115">メソッド</span><span class="sxs-lookup"><span data-stu-id="34e03-115">Methods</span></span>

### <a name="addaccountasync"></a><span data-ttu-id="34e03-116">addAccountAsync</span><span class="sxs-lookup"><span data-stu-id="34e03-116">addAccountAsync</span></span>
`- (void) addAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesAddAccountResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="34e03-117">アカウントにアカウント管理者を追加、完了時にコールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="34e03-117">Add an account to account manager, callback will be invoked when it completes.</span></span>

#### <a name="parameters"></a><span data-ttu-id="34e03-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34e03-118">Parameters</span></span> 
* `callback`

<span data-ttu-id="34e03-119">コールバックの結果は、アカウントの追加が成功したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="34e03-119">The callback result indicates if Account addition is successful or not.</span></span> 

### <a name="removeaccountasync"></a><span data-ttu-id="34e03-120">removeAccountAsync</span><span class="sxs-lookup"><span data-stu-id="34e03-120">removeAccountAsync</span></span>
`- (void) removeAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesRemoveAccountResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="34e03-121">アカウント マネージャーからアカウントを削除、完了時にコールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="34e03-121">Remove an account from account manager, callback will be invoked when it completes.</span></span>

#### <a name="parameters"></a><span data-ttu-id="34e03-122">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34e03-122">Parameters</span></span> 
* `callback` 

 <span data-ttu-id="34e03-123">コールバックの結果は、アカウントの削除が成功したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="34e03-123">The callback result indicates if Account removal is successful or not.</span></span> 