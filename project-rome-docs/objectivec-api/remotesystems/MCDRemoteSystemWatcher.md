---
title: MCDRemoteSystemWatcher
description: リモート システムを検出するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 8fcb0c01fd8f8c3ef1eb2d959dc9ef8af758562d
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755740"
---
# <a name="class-mcdremotesystemwatcher"></a><span data-ttu-id="00d8d-104">クラス `MCDRemoteSystemWatcher`</span><span class="sxs-lookup"><span data-stu-id="00d8d-104">class `MCDRemoteSystemWatcher`</span></span>

```
@interface MCDRemoteSystemWatcher : NSObject
```

<span data-ttu-id="00d8d-105">リモート システムを検出するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="00d8d-105">A class used to discover remote systems.</span></span> 

## <a name="properties"></a><span data-ttu-id="00d8d-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="00d8d-106">Properties</span></span>

### <a name="remotesystemadded"></a><span data-ttu-id="00d8d-107">remoteSystemAdded</span><span class="sxs-lookup"><span data-stu-id="00d8d-107">remoteSystemAdded</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

<span data-ttu-id="00d8d-108">新しいリモート システムが検出されたときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="00d8d-108">Event for when a new remote system is discovered.</span></span>

### <a name="remotesystemupdated"></a><span data-ttu-id="00d8d-109">remoteSystemUpdated</span><span class="sxs-lookup"><span data-stu-id="00d8d-109">remoteSystemUpdated</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

<span data-ttu-id="00d8d-110">この検出のセッションで以前に検出されたリモート システムが変更されたときから proximally のイベントは、クラウドに接続された、またはその逆に接続されています。</span><span class="sxs-lookup"><span data-stu-id="00d8d-110">Event for when a remote system that was previously discovered in this discovery session changes from proximally connected to cloud connected, or the reverse.</span></span> 

### <a name="remotesystemremoved"></a><span data-ttu-id="00d8d-111">remoteSystemRemoved</span><span class="sxs-lookup"><span data-stu-id="00d8d-111">remoteSystemRemoved</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

<span data-ttu-id="00d8d-112">リモート システムが削除されたときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="00d8d-112">Event for when a remote system is removed.</span></span> 

### <a name="enumerationcompleted"></a><span data-ttu-id="00d8d-113">enumerationCompleted</span><span class="sxs-lookup"><span data-stu-id="00d8d-113">enumerationCompleted</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

<span data-ttu-id="00d8d-114">現在の探索可能なデバイスの初期検出が完了するとイベントです。</span><span class="sxs-lookup"><span data-stu-id="00d8d-114">Event for when the initial discovery of currently-discoverable devices has finished.</span></span>  <span data-ttu-id="00d8d-115">検出プロセスは引き続き実行され、既存のリモート システムのセットが変更された場合は、追加のイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="00d8d-115">The discovery process will continue to run and will raise additional events if the set of existing remote systems changes.</span></span>

### <a name="erroroccurred"></a><span data-ttu-id="00d8d-116">errorOccurred</span><span class="sxs-lookup"><span data-stu-id="00d8d-116">errorOccurred</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

<span data-ttu-id="00d8d-117">探索中にエラーが発生したときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="00d8d-117">Event for when an error occurs during discovery.</span></span> <span data-ttu-id="00d8d-118">可能であれば、検出プロセスが続行されます。</span><span class="sxs-lookup"><span data-stu-id="00d8d-118">The discovery process will continue if possible.</span></span> <span data-ttu-id="00d8d-119">たとえば、値は、エラーが発生した場合**MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**エラーがクラウド検出 (参照にのみ適用されるため位の検出が継続**MCDRemoteSystemDiscoveryType**)。</span><span class="sxs-lookup"><span data-stu-id="00d8d-119">For example, if the error occurs with a value of **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, proximal discovery may continue because the error applies only to cloud discovery (see **MCDRemoteSystemDiscoveryType**).</span></span>

## <a name="constructors"></a><span data-ttu-id="00d8d-120">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="00d8d-120">Constructors</span></span>

### <a name="watcher"></a><span data-ttu-id="00d8d-121">監視</span><span class="sxs-lookup"><span data-stu-id="00d8d-121">watcher</span></span>
```
+ (nullable instancetype)watcher;
```

<span data-ttu-id="00d8d-122">作成し、このクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="00d8d-122">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="00d8d-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="00d8d-123">Returns</span></span> 
<span data-ttu-id="00d8d-124">このクラスの新しいインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="00d8d-124">Returns a new instance of this class.</span></span>

### <a name="watcherwithfilters"></a><span data-ttu-id="00d8d-125">watcherWithFilters</span><span class="sxs-lookup"><span data-stu-id="00d8d-125">watcherWithFilters</span></span>
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="00d8d-126">作成し、フィルターを使用してこのクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="00d8d-126">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="00d8d-127">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00d8d-127">Parameters</span></span> 
* `filters` 

<span data-ttu-id="00d8d-128">デバイスの検出プロセスで使用するフィルターの配列。</span><span class="sxs-lookup"><span data-stu-id="00d8d-128">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="00d8d-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="00d8d-129">Returns</span></span> 
<span data-ttu-id="00d8d-130">フィルターを使用した MCDRemoteSystemWatcher オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="00d8d-130">Returns an MCDRemoteSystemWatcher object with filters.</span></span>

### <a name="initwithfilters"></a><span data-ttu-id="00d8d-131">initWithFilters</span><span class="sxs-lookup"><span data-stu-id="00d8d-131">initWithFilters</span></span>
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="00d8d-132">作成し、フィルターを使用してこのクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="00d8d-132">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="00d8d-133">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00d8d-133">Parameters</span></span> 
* `filters` 

<span data-ttu-id="00d8d-134">デバイスの検出プロセスで使用するフィルターの配列。</span><span class="sxs-lookup"><span data-stu-id="00d8d-134">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="00d8d-135">戻り値</span><span class="sxs-lookup"><span data-stu-id="00d8d-135">Returns</span></span> 
<span data-ttu-id="00d8d-136">フィルターを使用して初期化 MCDRemoteSystemWatcher オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="00d8d-136">Returns an MCDRemoteSystemWatcher object initialized with filters.</span></span>

## <a name="methods"></a><span data-ttu-id="00d8d-137">メソッド</span><span class="sxs-lookup"><span data-stu-id="00d8d-137">Methods</span></span>

### <a name="start"></a><span data-ttu-id="00d8d-138">start</span><span class="sxs-lookup"><span data-stu-id="00d8d-138">start</span></span>
`- (void)start;`

<span data-ttu-id="00d8d-139">リモート システムの検出を開始します。</span><span class="sxs-lookup"><span data-stu-id="00d8d-139">Begins discovering remote systems.</span></span>

### <a name="stop"></a><span data-ttu-id="00d8d-140">stop</span><span class="sxs-lookup"><span data-stu-id="00d8d-140">stop</span></span>
`- (void)stop;` 

<span data-ttu-id="00d8d-141">アクティブな探索を停止します。</span><span class="sxs-lookup"><span data-stu-id="00d8d-141">Stops the active discovery.</span></span>
