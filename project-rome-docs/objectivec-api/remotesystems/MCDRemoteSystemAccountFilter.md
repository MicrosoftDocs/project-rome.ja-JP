---
title: MCDRemoteSystemAccountFilter
description: リモート システムを検出するアカウントを返すフィルター。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 34721c2dee89adc380b721a027382f81c2ecb751
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907324"
---
# <a name="class-mcdremotesystemaccountfilter"></a><span data-ttu-id="9a678-104">クラス `MCDRemoteSystemAccountFilter`</span><span class="sxs-lookup"><span data-stu-id="9a678-104">class `MCDRemoteSystemAccountFilter`</span></span> 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="9a678-105">リモート システムを検出するアカウントを返すフィルター。</span><span class="sxs-lookup"><span data-stu-id="9a678-105">Filter for the accounts to discover remote systems with.</span></span>

## <a name="properties"></a><span data-ttu-id="9a678-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9a678-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="9a678-107">アカウント</span><span class="sxs-lookup"><span data-stu-id="9a678-107">account</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="9a678-108">この MCDRemoteSystemAccountFilter に関連付けられているアカウント。</span><span class="sxs-lookup"><span data-stu-id="9a678-108">The Account associated with this MCDRemoteSystemAccountFilter.</span></span>

## <a name="constructors"></a><span data-ttu-id="9a678-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="9a678-109">Constructors</span></span>

### <a name="filterwithaccount"></a><span data-ttu-id="9a678-110">filterWithAccount</span><span class="sxs-lookup"><span data-stu-id="9a678-110">filterWithAccount</span></span>
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="9a678-111">MCDConnectedDevicesAccount アカウントを使用してクラスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9a678-111">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9a678-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a678-112">Parameters</span></span> 
* `account` 

<span data-ttu-id="9a678-113">使用されている MCDConnectedDevicesAccount アカウント。</span><span class="sxs-lookup"><span data-stu-id="9a678-113">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="9a678-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="9a678-114">Returns</span></span>
<span data-ttu-id="9a678-115">アカウントを使ってフィルター選択 MCDRemoteSystemAccountFilter オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="9a678-115">Returns a MCDRemoteSystemAccountFilter object filtered with the Account.</span></span>

### <a name="initwithaccount"></a><span data-ttu-id="9a678-116">initWithAccount</span><span class="sxs-lookup"><span data-stu-id="9a678-116">initWithAccount</span></span>
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="9a678-117">MCDConnectedDevicesAccount アカウントを使用してクラスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9a678-117">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9a678-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a678-118">Parameters</span></span> 
* `account` 

<span data-ttu-id="9a678-119">使用されている MCDConnectedDevicesAccount アカウント。</span><span class="sxs-lookup"><span data-stu-id="9a678-119">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="9a678-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="9a678-120">Returns</span></span>
<span data-ttu-id="9a678-121">MCDRemoteSystemAccountFilter オブジェクトを返します。 アカウントを使用してフィルター処理されます。</span><span class="sxs-lookup"><span data-stu-id="9a678-121">Returns an MCDRemoteSystemAccountFilter object initialized filtered with the Account.</span></span>