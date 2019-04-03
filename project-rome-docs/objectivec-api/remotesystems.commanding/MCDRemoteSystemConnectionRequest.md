---
title: MCDRemoteSystemConnectionRequest
description: 特定のリモート デバイスやアプリケーションとの通信の試行を表すクラス。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 54ed7deb1fa2b1c87a3195e61c2ce031d6e0cea9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907134"
---
# <a name="class-mcdremotesystemconnectionrequest"></a><span data-ttu-id="9933f-104">クラス `MCDRemoteSystemConnectionRequest`</span><span class="sxs-lookup"><span data-stu-id="9933f-104">class `MCDRemoteSystemConnectionRequest`</span></span> 

```
@interface MCDRemoteSystemConnectionRequest : NSObject
```  

<span data-ttu-id="9933f-105">特定のリモート デバイスやアプリケーションとの通信の試行を表すクラス。</span><span class="sxs-lookup"><span data-stu-id="9933f-105">A class that represents an attempt to communicate with a specific remote device or application.</span></span>

## <a name="constructors"></a><span data-ttu-id="9933f-106">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="9933f-106">Constructors</span></span>

### <a name="requestwithremotesystem"></a><span data-ttu-id="9933f-107">requestWithRemoteSystem</span><span class="sxs-lookup"><span data-stu-id="9933f-107">requestWithRemoteSystem</span></span>
`+ (instancetype)requestWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

<span data-ttu-id="9933f-108">初期化します、 [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)で、 [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="9933f-108">Initializes the [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) with a [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance.</span></span> <span data-ttu-id="9933f-109">このコンス トラクターは推奨されませんがターゲットにアプリを指定しないと、システムに送信された要求をサービスに選択されている、予期しないアプリのため可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9933f-109">This constructor is not recommended, as it does not specify an app to target and therefore may result in an unexpected app being selected to service requests sent to the system.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9933f-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9933f-110">Parameters</span></span>
* `remoteSystem` 

<span data-ttu-id="9933f-111">この接続要求の対象とするリモート システム。</span><span class="sxs-lookup"><span data-stu-id="9933f-111">The remote system to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="9933f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="9933f-112">Returns</span></span>
<span data-ttu-id="9933f-113">返しますが、初期化された[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="9933f-113">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="requestwithremotesystemapp"></a><span data-ttu-id="9933f-114">requestWithRemoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="9933f-114">requestWithRemoteSystemApp</span></span>
`+ (instancetype)requestWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

<span data-ttu-id="9933f-115">作成し、このクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9933f-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9933f-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9933f-116">Parameters</span></span>
* `remoteSystemApp` 

<span data-ttu-id="9933f-117">この接続要求の対象とするリモート アプリ。</span><span class="sxs-lookup"><span data-stu-id="9933f-117">The remote app to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="9933f-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="9933f-118">Returns</span></span>
<span data-ttu-id="9933f-119">返しますが、初期化された[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="9933f-119">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="initwithremotesystem"></a><span data-ttu-id="9933f-120">initWithRemoteSystem</span><span class="sxs-lookup"><span data-stu-id="9933f-120">initWithRemoteSystem</span></span>
`- (nullable instancetype)initWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

<span data-ttu-id="9933f-121">初期化します、 [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)で、 [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="9933f-121">Initializes the [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) with a [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance.</span></span> <span data-ttu-id="9933f-122">このコンス トラクターは推奨されませんがターゲットにアプリを指定しないと、システムに送信された要求をサービスに選択されている、予期しないアプリのため可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9933f-122">This constructor is not recommended, as it does not specify an app to target and therefore may result in an unexpected app being selected to service requests sent to the system.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9933f-123">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9933f-123">Parameters</span></span>
* <span data-ttu-id="9933f-124">`remoteSystem` この接続要求の対象とするリモート システム。</span><span class="sxs-lookup"><span data-stu-id="9933f-124">`remoteSystem` The remote system to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="9933f-125">戻り値</span><span class="sxs-lookup"><span data-stu-id="9933f-125">Returns</span></span>
<span data-ttu-id="9933f-126">返しますが、初期化された[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="9933f-126">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="initwithremotesystemapp"></a><span data-ttu-id="9933f-127">initWithRemoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="9933f-127">initWithRemoteSystemApp</span></span>
`- (nullable instancetype)initWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

<span data-ttu-id="9933f-128">作成し、このクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9933f-128">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9933f-129">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9933f-129">Parameters</span></span>
* `remoteSystemApp` 

<span data-ttu-id="9933f-130">この接続要求の対象とするリモート アプリ。</span><span class="sxs-lookup"><span data-stu-id="9933f-130">The remote app to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="9933f-131">戻り値</span><span class="sxs-lookup"><span data-stu-id="9933f-131">Returns</span></span>
<span data-ttu-id="9933f-132">返しますが、初期化された[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="9933f-132">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>