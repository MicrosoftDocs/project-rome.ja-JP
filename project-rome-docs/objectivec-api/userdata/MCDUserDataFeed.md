---
title: MCDUserDataFeed
description: このクラスは、接続されているデバイス プラットフォームのバックエンドでユーザーに固有のデータを同期する責任を負います。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: cd90c266c3c0293996a4f23059719224579404ff
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132238"
---
# <a name="class-mcduserdatafeed"></a><span data-ttu-id="55c57-104">クラス `MCDUserDataFeed`</span><span class="sxs-lookup"><span data-stu-id="55c57-104">class `MCDUserDataFeed`</span></span>

```
@interface MCDUserDataFeed : NSObject
```

<span data-ttu-id="55c57-105">このクラスは、接続されているデバイス プラットフォームのバックエンドでユーザーに固有のデータを同期する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="55c57-105">This class is responsible for synchronizing user-specific data with the Connected Devices Platform backend.</span></span> <span data-ttu-id="55c57-106">同期されるデータによって異なりますが **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="55c57-106">The data that is synchronized depends on which **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** instances are contained.</span></span>

## <a name="properties"></a><span data-ttu-id="55c57-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="55c57-107">Properties</span></span>

### <a name="syncstatus"></a><span data-ttu-id="55c57-108">syncStatus</span><span class="sxs-lookup"><span data-stu-id="55c57-108">syncStatus</span></span>
`@property(nonatomic, readonly) MCDUserDataSyncStatus syncStatus;`

<span data-ttu-id="55c57-109">ユーザー データの同期の現在の状態について説明します。</span><span class="sxs-lookup"><span data-stu-id="55c57-109">Describes the current status of user data synchronization.</span></span>

### <a name="syncstatuschanged"></a><span data-ttu-id="55c57-110">syncStatusChanged</span><span class="sxs-lookup"><span data-stu-id="55c57-110">syncStatusChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserDataFeed*, MCDUserDataFeedSyncStatusChangedEventArgs*>* syncStatusChanged;`

<span data-ttu-id="55c57-111">UserDataFeed の同期の状態が変更されたときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="55c57-111">Event for when the sync status of the UserDataFeed changes.</span></span>

### <a name="daystosync"></a><span data-ttu-id="55c57-112">daysToSync</span><span class="sxs-lookup"><span data-stu-id="55c57-112">daysToSync</span></span>
`@property(nonatomic, readwrite) NSInteger daysToSync;`

<span data-ttu-id="55c57-113">日数が 30 未満にする必要がありますが、同期するデータの数。</span><span class="sxs-lookup"><span data-stu-id="55c57-113">The number of days of data to sync, which should be fewer than 30.</span></span>  <span data-ttu-id="55c57-114">サーバーによって決まりますが既定値を表します。</span><span class="sxs-lookup"><span data-stu-id="55c57-114">It represents the default value, which will be determined by the server.</span></span>

## <a name="constructors"></a><span data-ttu-id="55c57-115">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="55c57-115">Constructors</span></span>

### <a name="getforaccount"></a><span data-ttu-id="55c57-116">getForAccount</span><span class="sxs-lookup"><span data-stu-id="55c57-116">getForAccount</span></span>
`+ (nullable instancetype)getForAccount:(nonnull MCDConnectedDevicesAccount*)userAccount
                                   platform:(nonnull MCDConnectedDevicesPlatform*)platform
                         activitySourceHost:(nonnull NSString*)activitySourceHost;`

<span data-ttu-id="55c57-117">作成し、ユーザー アカウント、プラットフォームのインスタンス、およびクロス プラットフォーム アプリの id。 このクラスの新しいインスタンスを初期化します</span><span class="sxs-lookup"><span data-stu-id="55c57-117">Creates and initializes a new instance of this class with a user account, platform instance, and the cross-platform app ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="55c57-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55c57-118">Parameters</span></span>
* `userAccount` 

<span data-ttu-id="55c57-119">このデータの関連付けられているユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="55c57-119">The user account that this data will be associated with.</span></span>

* `platform` 

<span data-ttu-id="55c57-120">**MCDPlatform**がこのアプリの接続されたデバイスの機能用に初期化されたインスタンス。</span><span class="sxs-lookup"><span data-stu-id="55c57-120">The **MCDPlatform** instance that has been initialized for this app's Connected Devices functionality.</span></span>

* `activitySourceHost` 

<span data-ttu-id="55c57-121">クロス プラットフォーム アプリの id。</span><span class="sxs-lookup"><span data-stu-id="55c57-121">The cross-platform app ID.</span></span> <span data-ttu-id="55c57-122">これは、Microsoft 開発者向けダッシュ ボードの登録の過程で取得されます。</span><span class="sxs-lookup"><span data-stu-id="55c57-122">This is retrieved through the Microsoft Developer Dashboard registration.</span></span>

#### <a name="returns"></a><span data-ttu-id="55c57-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="55c57-123">Returns</span></span>
<span data-ttu-id="55c57-124">このクラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="55c57-124">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="55c57-125">メソッド</span><span class="sxs-lookup"><span data-stu-id="55c57-125">Methods</span></span>

> [!WARNING]
> <span data-ttu-id="55c57-126">この関数は非推奨とされます、'subscribeToSyncScopesWithResultAsync' 代わりにします。</span><span class="sxs-lookup"><span data-stu-id="55c57-126">This function is deprecated, 'subscribeToSyncScopesWithResultAsync' instead.</span></span>

### <a name="subscribetosyncscopesasync"></a><span data-ttu-id="55c57-127">subscribeToSyncScopesAsync</span><span class="sxs-lookup"><span data-stu-id="55c57-127">subscribeToSyncScopesAsync</span></span>
`- (void)subscribeToSyncScopesAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(BOOL, NSError* _Nullable)) callback  __attribute__((deprecated("Use subscribeToSyncScopesWithResultAsync instead")));`

<span data-ttu-id="55c57-128">追加**MCDUserDataFeedSyncScope**この MCDUserDataFeed するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="55c57-128">Adds **MCDUserDataFeedSyncScope** instances to this MCDUserDataFeed.</span></span>  <span data-ttu-id="55c57-129">に従ってこの MCDUserDataFeed が同期されている、 **MCDUserDataFeedSyncScope**インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="55c57-129">This MCDUserDataFeed is synchronized according to the **MCDUserDataFeedSyncScope** instances specified.</span></span>

#### <a name="parameters"></a><span data-ttu-id="55c57-130">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55c57-130">Parameters</span></span>

* <span data-ttu-id="55c57-131">`syncScopes` 配列の**MCDSyncScope**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="55c57-131">`syncScopes` An array of **MCDSyncScope** instances.</span></span>

* `callback`

<span data-ttu-id="55c57-132">コールバックの結果は、サブスクリプションが成功したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="55c57-132">The callback result indicates if subscription is successful, or not.</span></span>

### <a name="subscribetosyncscopeswithresultasync"></a><span data-ttu-id="55c57-133">subscribeToSyncScopesWithResultAsync</span><span class="sxs-lookup"><span data-stu-id="55c57-133">subscribeToSyncScopesWithResultAsync</span></span>
`- (void)subscribeToSyncScopesWithResultAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(MCDUserDataFeedSubscribeResult* _Nullable, NSError* _Nullable)) callback;`

<span data-ttu-id="55c57-134">追加**MCDUserDataFeedSyncScope**この MCDUserDataFeed するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="55c57-134">Adds **MCDUserDataFeedSyncScope** instances to this MCDUserDataFeed.</span></span>  <span data-ttu-id="55c57-135">に従ってこの MCDUserDataFeed が同期されている、 **MCDUserDataFeedSyncScope**インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="55c57-135">This MCDUserDataFeed is synchronized according to the **MCDUserDataFeedSyncScope** instances specified.</span></span>

#### <a name="parameters"></a><span data-ttu-id="55c57-136">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55c57-136">Parameters</span></span>

* <span data-ttu-id="55c57-137">`syncScopes` 配列の**MCDSyncScope**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="55c57-137">`syncScopes` An array of **MCDSyncScope** instances.</span></span>

* `callback`

<span data-ttu-id="55c57-138">コールバックの結果は、サブスクリプションが成功したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="55c57-138">The callback result indicates if subscription is successful, or not.</span></span>

### <a name="startsync"></a><span data-ttu-id="55c57-139">startSync</span><span class="sxs-lookup"><span data-stu-id="55c57-139">startSync</span></span>
`- (void)startSync;`

<span data-ttu-id="55c57-140">接続されているデバイス プラットフォームでは、同期プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="55c57-140">Starts the synchronization process with the Connected Devices Platform.</span></span> <span data-ttu-id="55c57-141">この操作中に、 **syncStatus**プロパティが更新され、変更イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="55c57-141">During this operation, the **syncStatus** property will be updated and change events will be raised.</span></span>