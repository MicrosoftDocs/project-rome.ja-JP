---
title: MCDUserDataFeed
description: このクラスは、接続されているデバイス プラットフォームのバックエンドでユーザーに固有のデータを同期する責任を負います。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 66898563bdad8adb2f1ebfe75f010cd5ef1d9ca2
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908994"
---
# <a name="class-mcduserdatafeed"></a><span data-ttu-id="edeea-104">クラス `MCDUserDataFeed`</span><span class="sxs-lookup"><span data-stu-id="edeea-104">class `MCDUserDataFeed`</span></span>

```
@interface MCDUserDataFeed : NSObject
```

<span data-ttu-id="edeea-105">このクラスは、接続されているデバイス プラットフォームのバックエンドでユーザーに固有のデータを同期する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="edeea-105">This class is responsible for synchronizing user-specific data with the Connected Devices Platform backend.</span></span> <span data-ttu-id="edeea-106">同期されるデータによって異なりますが**[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** のインスタンスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="edeea-106">The data that is synchronized depends on which **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** instances are contained.</span></span>

## <a name="properties"></a><span data-ttu-id="edeea-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="edeea-107">Properties</span></span>

### <a name="syncstatus"></a><span data-ttu-id="edeea-108">syncStatus</span><span class="sxs-lookup"><span data-stu-id="edeea-108">syncStatus</span></span>
`@property(nonatomic, readonly) MCDUserDataSyncStatus syncStatus;`

<span data-ttu-id="edeea-109">ユーザー データの同期の現在の状態について説明します。</span><span class="sxs-lookup"><span data-stu-id="edeea-109">Describes the current status of user data synchronization.</span></span>

### <a name="syncstatuschanged"></a><span data-ttu-id="edeea-110">syncStatusChanged</span><span class="sxs-lookup"><span data-stu-id="edeea-110">syncStatusChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserDataFeed*, MCDUserDataFeedSyncStatusChangedEventArgs*>* syncStatusChanged;`

<span data-ttu-id="edeea-111">UserDataFeed の同期の状態が変更されたときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="edeea-111">Event for when the sync status of the UserDataFeed changes.</span></span>

### <a name="daystosync"></a><span data-ttu-id="edeea-112">daysToSync</span><span class="sxs-lookup"><span data-stu-id="edeea-112">daysToSync</span></span>
`@property(nonatomic, readwrite) NSInteger daysToSync;`

<span data-ttu-id="edeea-113">日数が 30 未満にする必要がありますが、同期するデータの数。</span><span class="sxs-lookup"><span data-stu-id="edeea-113">The number of days of data to sync, which should be fewer than 30.</span></span>  <span data-ttu-id="edeea-114">サーバーによって決まりますが既定値を表します。</span><span class="sxs-lookup"><span data-stu-id="edeea-114">It represents the default value, which will be determined by the server.</span></span>

## <a name="constructors"></a><span data-ttu-id="edeea-115">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="edeea-115">Constructors</span></span>

### <a name="getforaccount"></a><span data-ttu-id="edeea-116">getForAccount</span><span class="sxs-lookup"><span data-stu-id="edeea-116">getForAccount</span></span>
`+ (nullable instancetype)getForAccount:(nonnull MCDConnectedDevicesAccount*)userAccount
                                   platform:(nonnull MCDConnectedDevicesPlatform*)platform
                         activitySourceHost:(nonnull NSString*)activitySourceHost;`

<span data-ttu-id="edeea-117">作成し、ユーザー アカウント、プラットフォームのインスタンス、およびクロス プラットフォーム アプリの id。 このクラスの新しいインスタンスを初期化します</span><span class="sxs-lookup"><span data-stu-id="edeea-117">Creates and initializes a new instance of this class with a user account, platform instance, and the cross-platform app ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="edeea-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="edeea-118">Parameters</span></span>
* `userAccount` 

<span data-ttu-id="edeea-119">このデータの関連付けられているユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="edeea-119">The user account that this data will be associated with.</span></span>

* `platform` 

<span data-ttu-id="edeea-120">**MCDPlatform**がこのアプリの接続されたデバイスの機能用に初期化されたインスタンス。</span><span class="sxs-lookup"><span data-stu-id="edeea-120">The **MCDPlatform** instance that has been initialized for this app's Connected Devices functionality.</span></span>

* `activitySourceHost` 

<span data-ttu-id="edeea-121">クロス プラットフォーム アプリの id。</span><span class="sxs-lookup"><span data-stu-id="edeea-121">The cross-platform app ID.</span></span> <span data-ttu-id="edeea-122">これは、Microsoft 開発者向けダッシュ ボードの登録の過程で取得されます。</span><span class="sxs-lookup"><span data-stu-id="edeea-122">This is retrieved through the Microsoft Developer Dashboard registration.</span></span>

#### <a name="returns"></a><span data-ttu-id="edeea-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="edeea-123">Returns</span></span>
<span data-ttu-id="edeea-124">このクラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="edeea-124">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="edeea-125">メソッド</span><span class="sxs-lookup"><span data-stu-id="edeea-125">Methods</span></span>

### <a name="subscribetosyncscopesasync"></a><span data-ttu-id="edeea-126">subscribeToSyncScopesAsync</span><span class="sxs-lookup"><span data-stu-id="edeea-126">subscribeToSyncScopesAsync</span></span>
`- (void)subscribeToSyncScopesAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(BOOL, NSError* _Nullable)) callback;`

<span data-ttu-id="edeea-127">追加**MCDUserDataFeedSyncScope**この MCDUserDataFeed するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="edeea-127">Adds **MCDUserDataFeedSyncScope** instances to this MCDUserDataFeed.</span></span>  <span data-ttu-id="edeea-128">に従ってこの MCDUserDataFeed が同期されている、 **MCDUserDataFeedSyncScope**インスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="edeea-128">This MCDUserDataFeed is synchronized according to the **MCDUserDataFeedSyncScope** instances specified.</span></span>

#### <a name="parameters"></a><span data-ttu-id="edeea-129">パラメーター</span><span class="sxs-lookup"><span data-stu-id="edeea-129">Parameters</span></span>

* <span data-ttu-id="edeea-130">`syncScopes` 配列の**MCDSyncScope**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="edeea-130">`syncScopes` An array of **MCDSyncScope** instances.</span></span>

* `callback`

<span data-ttu-id="edeea-131">コールバックの結果は、サブスクリプションが成功したかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="edeea-131">The callback result indicates if subscription is successful, or not.</span></span> 

### <a name="startsync"></a><span data-ttu-id="edeea-132">startSync</span><span class="sxs-lookup"><span data-stu-id="edeea-132">startSync</span></span>
`- (void)startSync;`

<span data-ttu-id="edeea-133">接続されているデバイス プラットフォームでは、同期プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="edeea-133">Starts the synchronization process with the Connected Devices Platform.</span></span> <span data-ttu-id="edeea-134">この操作中に、 **syncStatus**プロパティが更新され、変更イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="edeea-134">During this operation, the **syncStatus** property will be updated and change events will be raised.</span></span>