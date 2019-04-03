---
title: MCDConnectedDevicesAccount
description: このクラスは、アプリによって認識されている単一のユーザー アカウントを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: e9b43bb76e46f3a027247b1d4d564c6e1571bae4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909154"
---
# <a name="class-mcdconnecteddevicesaccount"></a><span data-ttu-id="aa816-104">クラス `MCDConnectedDevicesAccount`</span><span class="sxs-lookup"><span data-stu-id="aa816-104">class `MCDConnectedDevicesAccount`</span></span>

```
@interface MCDConnectedDevicesAccount : NSObject
```  

<span data-ttu-id="aa816-105">このクラスは、アプリによって認識されている単一のユーザー アカウントを表します。</span><span class="sxs-lookup"><span data-stu-id="aa816-105">This class represents a single user account known by an app.</span></span>

## <a name="properties"></a><span data-ttu-id="aa816-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="aa816-106">Properties</span></span>

### <a name="anonymousaccount"></a><span data-ttu-id="aa816-107">anonymousAccount</span><span class="sxs-lookup"><span data-stu-id="aa816-107">anonymousAccount</span></span>
`+ (nullable instancetype)anonymousAccount;`

<span data-ttu-id="aa816-108">匿名アカウントのシングルトン インスタンス。</span><span class="sxs-lookup"><span data-stu-id="aa816-108">The singleton instance of the Anonymous account.</span></span>

### <a name="accountid"></a><span data-ttu-id="aa816-109">accountId</span><span class="sxs-lookup"><span data-stu-id="aa816-109">accountId</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

<span data-ttu-id="aa816-110">このユーザー アカウントの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="aa816-110">The unique identifier for this user account.</span></span>

### <a name="type"></a><span data-ttu-id="aa816-111">type</span><span class="sxs-lookup"><span data-stu-id="aa816-111">type</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

<span data-ttu-id="aa816-112">アカウントの種類を記述する MCDConnectedDevicesAccountType 値。</span><span class="sxs-lookup"><span data-stu-id="aa816-112">A MCDConnectedDevicesAccountType value describing the type of account.</span></span>

## <a name="constructors"></a><span data-ttu-id="aa816-113">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="aa816-113">Constructors</span></span>

### <a name="accountwithaccountid"></a><span data-ttu-id="aa816-114">accountWithAccountId</span><span class="sxs-lookup"><span data-stu-id="aa816-114">accountWithAccountId</span></span>
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="aa816-115">このユーザー アカウントの一意の識別子では、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="aa816-115">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="aa816-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa816-116">Parameters</span></span> 

* `accountId` 

<span data-ttu-id="aa816-117">このユーザー アカウントの一意の識別子の文字列。</span><span class="sxs-lookup"><span data-stu-id="aa816-117">A unique identifier string for this user account.</span></span>

`type` 

<span data-ttu-id="aa816-118">アカウントの MCDConnectedDevicesAccountType (依存、アカウントがどの ID プロバイダーから)。</span><span class="sxs-lookup"><span data-stu-id="aa816-118">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="aa816-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa816-119">Returns</span></span>
<span data-ttu-id="aa816-120">アカウント識別子を含む MCDConnectedDevicesAccount オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="aa816-120">Returns an MCDConnectedDevicesAccount object with the account identifier.</span></span>

### <a name="initwithaccountid"></a><span data-ttu-id="aa816-121">initWithAccountId</span><span class="sxs-lookup"><span data-stu-id="aa816-121">initWithAccountId</span></span>
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="aa816-122">このユーザー アカウントの一意の識別子では、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="aa816-122">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="aa816-123">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa816-123">Parameters</span></span> 
* `type`

<span data-ttu-id="aa816-124">アカウントの MCDConnectedDevicesAccountType (依存、アカウントがどの ID プロバイダーから)。</span><span class="sxs-lookup"><span data-stu-id="aa816-124">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="aa816-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa816-125">Returns</span></span>
<span data-ttu-id="aa816-126">アカウント識別子を使用して初期化 MCDConnectedDevicesAccount オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="aa816-126">Returns an MCDConnectedDevicesAccount object initialized with the account identifier.</span></span>