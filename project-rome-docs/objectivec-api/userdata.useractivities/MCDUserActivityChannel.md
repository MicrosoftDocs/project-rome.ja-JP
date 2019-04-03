---
title: MCDUserActivityChannel
description: このクラスを追加して、アプリケーションのユーザー アクティビティのクエリを処理します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: b047af1da3ba79be88a53cf589c3894892b01ef4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907804"
---
# <a name="class-mcduseractivitychannel"></a><span data-ttu-id="9f4f7-104">クラス `MCDUserActivityChannel`</span><span class="sxs-lookup"><span data-stu-id="9f4f7-104">class `MCDUserActivityChannel`</span></span>

```
@interface MCDUserActivityChannel : NSObject
```

<span data-ttu-id="9f4f7-105">このクラスを追加して、アプリケーションのユーザー アクティビティのクエリを処理します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-105">This class handles the adding and querying of user activities for the application.</span></span>

## <a name="properties"></a><span data-ttu-id="9f4f7-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9f4f7-106">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="9f4f7-107">syncScope</span><span class="sxs-lookup"><span data-stu-id="9f4f7-107">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="9f4f7-108">ユーザー アクティビティのユーザー データの同期スコープの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-108">Gets the user data sync scope value for User Activities.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="9f4f7-109">AppDisplayName</span><span class="sxs-lookup"><span data-stu-id="9f4f7-109">appDisplayName</span></span>
`@property(nonatomic, copy, nullable) NSString* appDisplayName;`

<span data-ttu-id="9f4f7-110">すべてのアクティビティ、アプリの表示名。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-110">The display name of the app for all activities.</span></span>

## <a name="constructors"></a><span data-ttu-id="9f4f7-111">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="9f4f7-111">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="9f4f7-112">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="9f4f7-112">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

<span data-ttu-id="9f4f7-113">ユーザーのデータ フィードでは、このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-113">Creates an instance of this class with the user data feed.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9f4f7-114">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f4f7-114">Parameters</span></span>
* <span data-ttu-id="9f4f7-115">`userDataFeed` このチャネルでのアクティビティに関連付けられているユーザー データ。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-115">`userDataFeed` The user data associated with the activities on this channel.</span></span>

#### <a name="returns"></a><span data-ttu-id="9f4f7-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="9f4f7-116">Returns</span></span>
<span data-ttu-id="9f4f7-117">このクラスの新しいインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-117">Returns a new instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="9f4f7-118">メソッド</span><span class="sxs-lookup"><span data-stu-id="9f4f7-118">Methods</span></span>

### <a name="getorcreateuseractivityasync"></a><span data-ttu-id="9f4f7-119">getOrCreateUserActivityAsync</span><span class="sxs-lookup"><span data-stu-id="9f4f7-119">getOrCreateUserActivityAsync</span></span>
`- (void)getOrCreateUserActivityAsync:(nonnull NSString*)activityId
                          completion:(nonnull void (^)(MCDUserActivity* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="9f4f7-120">指定したユーザーのアクティビティを作成します。 または既に存在する場合への参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-120">Creates the specified user activity, or gets a reference to it if it already exists.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9f4f7-121">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f4f7-121">Parameters</span></span>
* <span data-ttu-id="9f4f7-122">`activityId` このアクティビティの ID。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-122">`activityId` The ID for this activity.</span></span>
* <span data-ttu-id="9f4f7-123">`completionBlock` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-123">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="9f4f7-124">これは、取得されたアクティビティへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-124">This provides access to the retrieved activity.</span></span>

### <a name="deleteactivityasync"></a><span data-ttu-id="9f4f7-125">deleteActivityAsync</span><span class="sxs-lookup"><span data-stu-id="9f4f7-125">deleteActivityAsync</span></span>
`- (void)deleteActivityAsync:(nonnull NSString*)activityId completion:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="9f4f7-126">特定のユーザー アクティビティを削除します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-126">Deletes the given user activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9f4f7-127">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f4f7-127">Parameters</span></span>
* <span data-ttu-id="9f4f7-128">`activityId` 削除するアクティビティの ID。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-128">`activityId` The ID of the activity to delete.</span></span>
* <span data-ttu-id="9f4f7-129">`completionBlock` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-129">`completionBlock` The code block to execute upon completion.</span></span>

### <a name="deleteallactivitiesasync"></a><span data-ttu-id="9f4f7-130">deleteAllActivitiesAsync</span><span class="sxs-lookup"><span data-stu-id="9f4f7-130">deleteAllActivitiesAsync</span></span>
`- (void)deleteAllActivitiesAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="9f4f7-131">すべてのユーザー アクティビティを削除します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-131">Deletes all user activities.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9f4f7-132">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f4f7-132">Parameters</span></span>
* <span data-ttu-id="9f4f7-133">`completionBlock` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-133">`completionBlock` The code block to execute upon completion.</span></span>

### <a name="getrecentuseractivitiesasync"></a><span data-ttu-id="9f4f7-134">getRecentUserActivitiesAsync</span><span class="sxs-lookup"><span data-stu-id="9f4f7-134">getRecentUserActivitiesAsync</span></span>
`- (void)getRecentUserActivitiesAsync:(NSInteger)maxUniqueActivities
                          completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="9f4f7-135">最近のユーザー アクティビティの履歴を取得します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-135">Gets a history of recent user activities.</span></span> 

#### <a name="parameters"></a><span data-ttu-id="9f4f7-136">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f4f7-136">Parameters</span></span>
* <span data-ttu-id="9f4f7-137">`maxUniqueActivities` 取得するユーザー アクティビティの最大数。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-137">`maxUniqueActivities` The maximum number of user activities to retrieve.</span></span>
* <span data-ttu-id="9f4f7-138">`completionBlock` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-138">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="9f4f7-139">これは、利用状況の履歴へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-139">This provides access to the activity history.</span></span>

### <a name="getsessionhistoryitemsforuseractivityasync"></a><span data-ttu-id="9f4f7-140">getSessionHistoryItemsForUserActivityAsync</span><span class="sxs-lookup"><span data-stu-id="9f4f7-140">getSessionHistoryItemsForUserActivityAsync</span></span>
`- (void)getSessionHistoryItemsForUserActivityAsync:(nonnull NSString*)activityId
                                     withStartTime:(nonnull NSDate*)startTime
                                        completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="9f4f7-141">特定のアクティビティのセッションの履歴エントリを取得します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-141">Gets the session history entries for a given activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9f4f7-142">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f4f7-142">Parameters</span></span>
* <span data-ttu-id="9f4f7-143">`activityId` 履歴を取得するアクティビティの ID。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-143">`activityId` The ID of the activity to get history for.</span></span>
* <span data-ttu-id="9f4f7-144">`startTime` セッションの履歴を考慮する時刻。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-144">`startTime` The time at which to consider session history.</span></span>
* <span data-ttu-id="9f4f7-145">`completionBlock` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-145">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="9f4f7-146">これは、利用状況の履歴へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-146">This provides access to the activity history.</span></span>

### <a name="getrecentsessionhistoryitemsfortimerangeasync"></a><span data-ttu-id="9f4f7-147">getRecentSessionHistoryItemsForTimeRangeAsync</span><span class="sxs-lookup"><span data-stu-id="9f4f7-147">getRecentSessionHistoryItemsForTimeRangeAsync</span></span>
`- (void)getRecentSessionHistoryItemsForTimeRangeAsync:(nonnull NSDate*)startTime
                                 endTime:(nonnull NSDate*)endTime
                                 maxActivities:(NSInteger)maxActivities
                                 completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull,
                                                       NSError* _Nullable))completionBlock;`

<span data-ttu-id="9f4f7-148">特定のアクティビティのセッションの履歴エントリを取得します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-148">Gets the session history entries for a given activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9f4f7-149">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9f4f7-149">Parameters</span></span>
* <span data-ttu-id="9f4f7-150">`startTime` セッションの履歴の検討を開始時刻。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-150">`startTime` The time at which to start considering session history.</span></span>
* <span data-ttu-id="9f4f7-151">`endTime` セッションの履歴を考えると終了時刻。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-151">`endTime` The time at which to end considering session history.</span></span>
* <span data-ttu-id="9f4f7-152">`maxActivities` 取得するユーザー アクティビティの最大数。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-152">`maxActivities` The maximum number of user activities to retrieve.</span></span>
* <span data-ttu-id="9f4f7-153">`completion` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-153">`completion` The code block to execute upon completion.</span></span>
* <span data-ttu-id="9f4f7-154">`completionBlock` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-154">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="9f4f7-155">これは、利用状況の履歴へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9f4f7-155">This provides access to the activity history.</span></span>