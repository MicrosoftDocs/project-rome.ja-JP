---
title: MCDRemoteLauncherOptions
description: リモート起動機能のオプションを表すクラス。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 628bf1659dfb4ce50e20631622d8a78a322bb2f5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907334"
---
# <a name="class-mcdremotelauncheroptions"></a><span data-ttu-id="843e8-104">クラス `MCDRemoteLauncherOptions`</span><span class="sxs-lookup"><span data-stu-id="843e8-104">class `MCDRemoteLauncherOptions`</span></span> 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

<span data-ttu-id="843e8-105">リモート起動機能のオプションを表すクラス。</span><span class="sxs-lookup"><span data-stu-id="843e8-105">A class to represent options for the remote launch feature.</span></span>

## <a name="properties"></a><span data-ttu-id="843e8-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="843e8-106">Properties</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="843e8-107">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="843e8-107">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="843e8-108">Web アプリ URI を起動する場合の起動にフォールバックの URI は失敗します。</span><span class="sxs-lookup"><span data-stu-id="843e8-108">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

### <a name="preferredpackageids"></a><span data-ttu-id="843e8-109">preferredPackageIds</span><span class="sxs-lookup"><span data-stu-id="843e8-109">preferredPackageIds</span></span>
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

<span data-ttu-id="843e8-110">一連の**NSString**この URI を使用して起動できるようにするアプリの Id を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="843e8-110">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="843e8-111">Windows のアプリ ID は、アプリのパッケージ ファミリ名になります。</span><span class="sxs-lookup"><span data-stu-id="843e8-111">For Windows apps, the ID will be the app's package family name.</span></span>

## <a name="constructors"></a><span data-ttu-id="843e8-112">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="843e8-112">Constructors</span></span>

### <a name="optionswithfallbackuri"></a><span data-ttu-id="843e8-113">optionsWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="843e8-113">optionsWithFallbackUri</span></span>
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="843e8-114">作成し、このクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="843e8-114">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="843e8-115">パラメーター</span><span class="sxs-lookup"><span data-stu-id="843e8-115">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="843e8-116">Web アプリ URI を起動する場合の起動にフォールバックの URI は失敗します。</span><span class="sxs-lookup"><span data-stu-id="843e8-116">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="843e8-117">一連の**NSString**この URI を使用して起動できるようにするアプリの Id を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="843e8-117">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="843e8-118">Windows のアプリ ID は、アプリのパッケージ ファミリ名になります。</span><span class="sxs-lookup"><span data-stu-id="843e8-118">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="843e8-119">戻り値</span><span class="sxs-lookup"><span data-stu-id="843e8-119">Returns</span></span>
<span data-ttu-id="843e8-120">返しますが、初期化された[MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="843e8-120">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>

### <a name="initwithfallbackuri"></a><span data-ttu-id="843e8-121">initWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="843e8-121">initWithFallbackUri</span></span>
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="843e8-122">作成し、このクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="843e8-122">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="843e8-123">パラメーター</span><span class="sxs-lookup"><span data-stu-id="843e8-123">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="843e8-124">Web アプリ URI を起動する場合の起動にフォールバックの URI は失敗します。</span><span class="sxs-lookup"><span data-stu-id="843e8-124">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="843e8-125">一連の**NSString**この URI を使用して起動できるようにするアプリの Id を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="843e8-125">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="843e8-126">Windows のアプリ ID は、アプリのパッケージ ファミリ名になります。</span><span class="sxs-lookup"><span data-stu-id="843e8-126">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="843e8-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="843e8-127">Returns</span></span>
<span data-ttu-id="843e8-128">返しますが、初期化された[MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="843e8-128">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>