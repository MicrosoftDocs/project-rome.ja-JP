---
title: MCDRemoteSystemWatcher
description: MCDRemoteSystemWatcher クラスとそのプロパティについて説明します。 このクラスは、リモートシステムを検出するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: c000d5392fe6498c248b915ae4e26e49ad1d42db
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760646"
---
# <a name="class-mcdremotesystemwatcher"></a><span data-ttu-id="b5eb7-105">講義 `MCDRemoteSystemWatcher`</span><span class="sxs-lookup"><span data-stu-id="b5eb7-105">class `MCDRemoteSystemWatcher`</span></span>

```
@interface MCDRemoteSystemWatcher : NSObject
```

<span data-ttu-id="b5eb7-106">リモートシステムを検出するために使用されるクラス。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-106">A class used to discover remote systems.</span></span> 

## <a name="properties"></a><span data-ttu-id="b5eb7-107">Properties</span><span class="sxs-lookup"><span data-stu-id="b5eb7-107">Properties</span></span>

### <a name="remotesystemadded"></a><span data-ttu-id="b5eb7-108">remoteSystemAdded</span><span class="sxs-lookup"><span data-stu-id="b5eb7-108">remoteSystemAdded</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

<span data-ttu-id="b5eb7-109">新しいリモートシステムが検出されたときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-109">Event for when a new remote system is discovered.</span></span>

### <a name="remotesystemupdated"></a><span data-ttu-id="b5eb7-110">remoteSystemUpdated</span><span class="sxs-lookup"><span data-stu-id="b5eb7-110">remoteSystemUpdated</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

<span data-ttu-id="b5eb7-111">この探索セッションで以前に検出されたリモートシステムが、接続されているクラウドに接続されている proximally、またはその逆の場合に発生するイベントです。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-111">Event for when a remote system that was previously discovered in this discovery session changes from proximally connected to cloud connected, or the reverse.</span></span> 

### <a name="remotesystemremoved"></a><span data-ttu-id="b5eb7-112">remoteSystemRemoved</span><span class="sxs-lookup"><span data-stu-id="b5eb7-112">remoteSystemRemoved</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

<span data-ttu-id="b5eb7-113">リモートシステムが削除されたときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-113">Event for when a remote system is removed.</span></span> 

### <a name="enumerationcompleted"></a><span data-ttu-id="b5eb7-114">enumerationCompleted</span><span class="sxs-lookup"><span data-stu-id="b5eb7-114">enumerationCompleted</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

<span data-ttu-id="b5eb7-115">現在探索可能なデバイスの初期検出が終了したときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-115">Event for when the initial discovery of currently-discoverable devices has finished.</span></span>  <span data-ttu-id="b5eb7-116">既存のリモートシステムのセットが変更されると、検出プロセスが引き続き実行され、追加のイベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-116">The discovery process will continue to run and will raise additional events if the set of existing remote systems changes.</span></span>

### <a name="erroroccurred"></a><span data-ttu-id="b5eb7-117">エラーが発生しました</span><span class="sxs-lookup"><span data-stu-id="b5eb7-117">errorOccurred</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

<span data-ttu-id="b5eb7-118">検出中にエラーが発生した場合のイベントです。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-118">Event for when an error occurs during discovery.</span></span> <span data-ttu-id="b5eb7-119">可能であれば、検出プロセスは続行されます。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-119">The discovery process will continue if possible.</span></span> <span data-ttu-id="b5eb7-120">たとえば、エラーが **MCDRemoteSystemWatcherError**の値と共に発生した場合、エラーは cloud discovery にのみ適用されるため、位 discovery は続行される可能性があります (「 **MCDRemoteSystemDiscoveryType**」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-120">For example, if the error occurs with a value of **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, proximal discovery may continue because the error applies only to cloud discovery (see **MCDRemoteSystemDiscoveryType**).</span></span>

## <a name="constructors"></a><span data-ttu-id="b5eb7-121">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b5eb7-121">Constructors</span></span>

### <a name="watcher"></a><span data-ttu-id="b5eb7-122">監視</span><span class="sxs-lookup"><span data-stu-id="b5eb7-122">watcher</span></span>
```
+ (nullable instancetype)watcher;
```

<span data-ttu-id="b5eb7-123">このクラスの新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-123">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="b5eb7-124">戻り値</span><span class="sxs-lookup"><span data-stu-id="b5eb7-124">Returns</span></span> 
<span data-ttu-id="b5eb7-125">このクラスの新しいインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-125">Returns a new instance of this class.</span></span>

### <a name="watcherwithfilters"></a><span data-ttu-id="b5eb7-126">watcherWithFilters</span><span class="sxs-lookup"><span data-stu-id="b5eb7-126">watcherWithFilters</span></span>
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="b5eb7-127">フィルターを使用して、このクラスの新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-127">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b5eb7-128">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5eb7-128">Parameters</span></span> 
* `filters` 

<span data-ttu-id="b5eb7-129">デバイスの検出プロセスで使用するフィルターの配列。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-129">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="b5eb7-130">戻り値</span><span class="sxs-lookup"><span data-stu-id="b5eb7-130">Returns</span></span> 
<span data-ttu-id="b5eb7-131">フィルターを使用して MCDRemoteSystemWatcher オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-131">Returns an MCDRemoteSystemWatcher object with filters.</span></span>

### <a name="initwithfilters"></a><span data-ttu-id="b5eb7-132">initWithFilters</span><span class="sxs-lookup"><span data-stu-id="b5eb7-132">initWithFilters</span></span>
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="b5eb7-133">フィルターを使用して、このクラスの新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-133">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b5eb7-134">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b5eb7-134">Parameters</span></span> 
* `filters` 

<span data-ttu-id="b5eb7-135">デバイスの検出プロセスで使用するフィルターの配列。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-135">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="b5eb7-136">戻り値</span><span class="sxs-lookup"><span data-stu-id="b5eb7-136">Returns</span></span> 
<span data-ttu-id="b5eb7-137">フィルターを使用して初期化された MCDRemoteSystemWatcher オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-137">Returns an MCDRemoteSystemWatcher object initialized with filters.</span></span>

## <a name="methods"></a><span data-ttu-id="b5eb7-138">メソッド</span><span class="sxs-lookup"><span data-stu-id="b5eb7-138">Methods</span></span>

### <a name="start"></a><span data-ttu-id="b5eb7-139">start</span><span class="sxs-lookup"><span data-stu-id="b5eb7-139">start</span></span>
`- (void)start;`

<span data-ttu-id="b5eb7-140">リモートシステムの検出を開始します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-140">Begins discovering remote systems.</span></span>

### <a name="stop"></a><span data-ttu-id="b5eb7-141">stop</span><span class="sxs-lookup"><span data-stu-id="b5eb7-141">stop</span></span>
`- (void)stop;` 

<span data-ttu-id="b5eb7-142">アクティブな探索を停止します。</span><span class="sxs-lookup"><span data-stu-id="b5eb7-142">Stops the active discovery.</span></span>
