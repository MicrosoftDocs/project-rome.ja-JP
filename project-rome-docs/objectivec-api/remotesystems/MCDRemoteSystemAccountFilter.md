---
title: MCDRemoteSystemAccountFilter
description: "\"FilterwithAccount\" のようなコンストラクターを使用して、リモートシステムを検出するためにアカウントをフィルター処理する方法について説明します。"
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 3a32c318aba49eff550ccfdf51049fd97a34e2f5
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760726"
---
# <a name="class-mcdremotesystemaccountfilter"></a><span data-ttu-id="41b4b-104">講義 `MCDRemoteSystemAccountFilter`</span><span class="sxs-lookup"><span data-stu-id="41b4b-104">class `MCDRemoteSystemAccountFilter`</span></span> 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="41b4b-105">でリモートシステムを探索するためのアカウントをフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="41b4b-105">Filter for the accounts to discover remote systems with.</span></span>

## <a name="properties"></a><span data-ttu-id="41b4b-106">Properties</span><span class="sxs-lookup"><span data-stu-id="41b4b-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="41b4b-107">account</span><span class="sxs-lookup"><span data-stu-id="41b4b-107">account</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="41b4b-108">この MCDRemoteSystemAccountFilter に関連付けられているアカウント。</span><span class="sxs-lookup"><span data-stu-id="41b4b-108">The Account associated with this MCDRemoteSystemAccountFilter.</span></span>

## <a name="constructors"></a><span data-ttu-id="41b4b-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="41b4b-109">Constructors</span></span>

### <a name="filterwithaccount"></a><span data-ttu-id="41b4b-110">filterWithAccount</span><span class="sxs-lookup"><span data-stu-id="41b4b-110">filterWithAccount</span></span>
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="41b4b-111">MCDConnectedDevicesAccount アカウントを使用してクラスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="41b4b-111">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="41b4b-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41b4b-112">Parameters</span></span> 
* `account` 

<span data-ttu-id="41b4b-113">使用されている MCDConnectedDevicesAccount アカウント。</span><span class="sxs-lookup"><span data-stu-id="41b4b-113">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="41b4b-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="41b4b-114">Returns</span></span>
<span data-ttu-id="41b4b-115">アカウントを使用してフィルター処理された MCDRemoteSystemAccountFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="41b4b-115">Returns a MCDRemoteSystemAccountFilter object filtered with the Account.</span></span>

### <a name="initwithaccount"></a><span data-ttu-id="41b4b-116">initWithAccount</span><span class="sxs-lookup"><span data-stu-id="41b4b-116">initWithAccount</span></span>
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="41b4b-117">MCDConnectedDevicesAccount アカウントを使用してクラスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="41b4b-117">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="41b4b-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41b4b-118">Parameters</span></span> 
* `account` 

<span data-ttu-id="41b4b-119">使用されている MCDConnectedDevicesAccount アカウント。</span><span class="sxs-lookup"><span data-stu-id="41b4b-119">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="41b4b-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="41b4b-120">Returns</span></span>
<span data-ttu-id="41b4b-121">アカウントでフィルター処理された MCDRemoteSystemAccountFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="41b4b-121">Returns an MCDRemoteSystemAccountFilter object initialized filtered with the Account.</span></span>