---
title: MCDRemoteLauncherOptions
description: MCDRemoteLauncherOptions クラスについて説明します。 このクラスは、リモート起動機能のオプションを表します。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 2e698ad71282e44d1447e19085598139b67f9270
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760736"
---
# <a name="class-mcdremotelauncheroptions"></a><span data-ttu-id="ad5af-105">講義 `MCDRemoteLauncherOptions`</span><span class="sxs-lookup"><span data-stu-id="ad5af-105">class `MCDRemoteLauncherOptions`</span></span> 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

<span data-ttu-id="ad5af-106">リモート起動機能のオプションを表すクラス。</span><span class="sxs-lookup"><span data-stu-id="ad5af-106">A class to represent options for the remote launch feature.</span></span>

## <a name="properties"></a><span data-ttu-id="ad5af-107">Properties</span><span class="sxs-lookup"><span data-stu-id="ad5af-107">Properties</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="ad5af-108">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="ad5af-108">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="ad5af-109">アプリの起動 URI が失敗した場合に web で起動するフォールバック URI。</span><span class="sxs-lookup"><span data-stu-id="ad5af-109">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

### <a name="preferredpackageids"></a><span data-ttu-id="ad5af-110">Preferredのパッケージ</span><span class="sxs-lookup"><span data-stu-id="ad5af-110">preferredPackageIds</span></span>
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

<span data-ttu-id="ad5af-111">この URI で起動できるアプリの Id を表す **nsstring** オブジェクトのリスト。</span><span class="sxs-lookup"><span data-stu-id="ad5af-111">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="ad5af-112">Windows アプリの場合、ID はアプリのパッケージファミリ名になります。</span><span class="sxs-lookup"><span data-stu-id="ad5af-112">For Windows apps, the ID will be the app's package family name.</span></span>

## <a name="constructors"></a><span data-ttu-id="ad5af-113">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ad5af-113">Constructors</span></span>

### <a name="optionswithfallbackuri"></a><span data-ttu-id="ad5af-114">オプション Withfallbackuri</span><span class="sxs-lookup"><span data-stu-id="ad5af-114">optionsWithFallbackUri</span></span>
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="ad5af-115">このクラスの新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="ad5af-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ad5af-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad5af-116">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="ad5af-117">アプリの起動 URI が失敗した場合に web で起動するフォールバック URI。</span><span class="sxs-lookup"><span data-stu-id="ad5af-117">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="ad5af-118">この URI で起動できるアプリの Id を表す **nsstring** オブジェクトのリスト。</span><span class="sxs-lookup"><span data-stu-id="ad5af-118">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="ad5af-119">Windows アプリの場合、ID はアプリのパッケージファミリ名になります。</span><span class="sxs-lookup"><span data-stu-id="ad5af-119">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="ad5af-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad5af-120">Returns</span></span>
<span data-ttu-id="ad5af-121">成功した場合は初期化された [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) を返し、それ以外の場合は nil を返します。</span><span class="sxs-lookup"><span data-stu-id="ad5af-121">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>

### <a name="initwithfallbackuri"></a><span data-ttu-id="ad5af-122">initWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="ad5af-122">initWithFallbackUri</span></span>
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="ad5af-123">このクラスの新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="ad5af-123">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ad5af-124">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad5af-124">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="ad5af-125">アプリの起動 URI が失敗した場合に web で起動するフォールバック URI。</span><span class="sxs-lookup"><span data-stu-id="ad5af-125">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="ad5af-126">この URI で起動できるアプリの Id を表す **nsstring** オブジェクトのリスト。</span><span class="sxs-lookup"><span data-stu-id="ad5af-126">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="ad5af-127">Windows アプリの場合、ID はアプリのパッケージファミリ名になります。</span><span class="sxs-lookup"><span data-stu-id="ad5af-127">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="ad5af-128">戻り値</span><span class="sxs-lookup"><span data-stu-id="ad5af-128">Returns</span></span>
<span data-ttu-id="ad5af-129">成功した場合は初期化された [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) を返し、それ以外の場合は nil を返します。</span><span class="sxs-lookup"><span data-stu-id="ad5af-129">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>