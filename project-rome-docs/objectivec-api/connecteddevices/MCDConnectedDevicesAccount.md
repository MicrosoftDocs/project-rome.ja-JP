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
# <a name="class-mcdconnecteddevicesaccount"></a><span data-ttu-id="6875e-105">講義 `MCDConnectedDevicesAccount`</span><span class="sxs-lookup"><span data-stu-id="6875e-105">class `MCDConnectedDevicesAccount`</span></span>

```
@interface MCDConnectedDevicesAccount : NSObject
```  

<span data-ttu-id="6875e-106">このクラスは、アプリによって認識される1つのユーザーアカウントを表します。</span><span class="sxs-lookup"><span data-stu-id="6875e-106">This class represents a single user account known by an app.</span></span>

## <a name="properties"></a><span data-ttu-id="6875e-107">Properties</span><span class="sxs-lookup"><span data-stu-id="6875e-107">Properties</span></span>

### <a name="anonymousaccount"></a><span data-ttu-id="6875e-108">anonymousAccount</span><span class="sxs-lookup"><span data-stu-id="6875e-108">anonymousAccount</span></span>
`+ (nullable instancetype)anonymousAccount;`

<span data-ttu-id="6875e-109">匿名アカウントのシングルトンインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6875e-109">The singleton instance of the Anonymous account.</span></span>

### <a name="accountid"></a><span data-ttu-id="6875e-110">accountId</span><span class="sxs-lookup"><span data-stu-id="6875e-110">accountId</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

<span data-ttu-id="6875e-111">このユーザーアカウントの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="6875e-111">The unique identifier for this user account.</span></span>

### <a name="type"></a><span data-ttu-id="6875e-112">型</span><span class="sxs-lookup"><span data-stu-id="6875e-112">type</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

<span data-ttu-id="6875e-113">アカウントの種類を記述する MCDConnectedDevicesAccountType 値。</span><span class="sxs-lookup"><span data-stu-id="6875e-113">A MCDConnectedDevicesAccountType value describing the type of account.</span></span>

## <a name="constructors"></a><span data-ttu-id="6875e-114">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="6875e-114">Constructors</span></span>

### <a name="accountwithaccountid"></a><span data-ttu-id="6875e-115">accountWithAccountId</span><span class="sxs-lookup"><span data-stu-id="6875e-115">accountWithAccountId</span></span>
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="6875e-116">このユーザーアカウントの一意の識別子を持つ、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6875e-116">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="6875e-117">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6875e-117">Parameters</span></span> 

* `accountId` 

<span data-ttu-id="6875e-118">このユーザーアカウントの一意の識別子文字列。</span><span class="sxs-lookup"><span data-stu-id="6875e-118">A unique identifier string for this user account.</span></span>

`type` 

<span data-ttu-id="6875e-119">アカウントの MCDConnectedDevicesAccountType (アカウントの元の ID プロバイダーによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="6875e-119">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="6875e-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="6875e-120">Returns</span></span>
<span data-ttu-id="6875e-121">アカウント識別子を持つ MCDConnectedDevicesAccount オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="6875e-121">Returns an MCDConnectedDevicesAccount object with the account identifier.</span></span>

### <a name="initwithaccountid"></a><span data-ttu-id="6875e-122">initWithAccountId</span><span class="sxs-lookup"><span data-stu-id="6875e-122">initWithAccountId</span></span>
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="6875e-123">このユーザーアカウントの一意の識別子を持つ、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6875e-123">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="6875e-124">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6875e-124">Parameters</span></span> 
* `type`

<span data-ttu-id="6875e-125">アカウントの MCDConnectedDevicesAccountType (アカウントの元の ID プロバイダーによって異なります)。</span><span class="sxs-lookup"><span data-stu-id="6875e-125">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="6875e-126">戻り値</span><span class="sxs-lookup"><span data-stu-id="6875e-126">Returns</span></span>
<span data-ttu-id="6875e-127">アカウント識別子を使用して初期化された MCDConnectedDevicesAccount オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="6875e-127">Returns an MCDConnectedDevicesAccount object initialized with the account identifier.</span></span>