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
# <a name="class-mcduseractivitychannel"></a>クラス `MCDUserActivityChannel`

```
@interface MCDUserActivityChannel : NSObject
```

このクラスを追加して、アプリケーションのユーザー アクティビティのクエリを処理します。

## <a name="properties"></a>プロパティ

### <a name="syncscope"></a>syncScope
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

ユーザー アクティビティのユーザー データの同期スコープの値を取得します。

### <a name="appdisplayname"></a>AppDisplayName
`@property(nonatomic, copy, nullable) NSString* appDisplayName;`

すべてのアクティビティ、アプリの表示名。

## <a name="constructors"></a>コンストラクター

### <a name="channelwithuserdatafeed"></a>channelWithUserDataFeed
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

ユーザーのデータ フィードでは、このクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `userDataFeed` このチャネルでのアクティビティに関連付けられているユーザー データ。

#### <a name="returns"></a>戻り値
このクラスの新しいインスタンスを返します。

## <a name="methods"></a>メソッド

### <a name="getorcreateuseractivityasync"></a>getOrCreateUserActivityAsync
`- (void)getOrCreateUserActivityAsync:(nonnull NSString*)activityId
                          completion:(nonnull void (^)(MCDUserActivity* _Nonnull, NSError* _Nullable))completionBlock;`

指定したユーザーのアクティビティを作成します。 または既に存在する場合への参照を取得します。

#### <a name="parameters"></a>パラメーター
* `activityId` このアクティビティの ID。
* `completionBlock` 完了時に実行するコード ブロックです。 これは、取得されたアクティビティへのアクセスを提供します。

### <a name="deleteactivityasync"></a>deleteActivityAsync
`- (void)deleteActivityAsync:(nonnull NSString*)activityId completion:(nonnull void (^)(NSError* _Nullable))completionBlock;`

特定のユーザー アクティビティを削除します。

#### <a name="parameters"></a>パラメーター
* `activityId` 削除するアクティビティの ID。
* `completionBlock` 完了時に実行するコード ブロックです。

### <a name="deleteallactivitiesasync"></a>deleteAllActivitiesAsync
`- (void)deleteAllActivitiesAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

すべてのユーザー アクティビティを削除します。

#### <a name="parameters"></a>パラメーター
* `completionBlock` 完了時に実行するコード ブロックです。

### <a name="getrecentuseractivitiesasync"></a>getRecentUserActivitiesAsync
`- (void)getRecentUserActivitiesAsync:(NSInteger)maxUniqueActivities
                          completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

最近のユーザー アクティビティの履歴を取得します。 

#### <a name="parameters"></a>パラメーター
* `maxUniqueActivities` 取得するユーザー アクティビティの最大数。
* `completionBlock` 完了時に実行するコード ブロックです。 これは、利用状況の履歴へのアクセスを提供します。

### <a name="getsessionhistoryitemsforuseractivityasync"></a>getSessionHistoryItemsForUserActivityAsync
`- (void)getSessionHistoryItemsForUserActivityAsync:(nonnull NSString*)activityId
                                     withStartTime:(nonnull NSDate*)startTime
                                        completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

特定のアクティビティのセッションの履歴エントリを取得します。

#### <a name="parameters"></a>パラメーター
* `activityId` 履歴を取得するアクティビティの ID。
* `startTime` セッションの履歴を考慮する時刻。
* `completionBlock` 完了時に実行するコード ブロックです。 これは、利用状況の履歴へのアクセスを提供します。

### <a name="getrecentsessionhistoryitemsfortimerangeasync"></a>getRecentSessionHistoryItemsForTimeRangeAsync
`- (void)getRecentSessionHistoryItemsForTimeRangeAsync:(nonnull NSDate*)startTime
                                 endTime:(nonnull NSDate*)endTime
                                 maxActivities:(NSInteger)maxActivities
                                 completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull,
                                                       NSError* _Nullable))completionBlock;`

特定のアクティビティのセッションの履歴エントリを取得します。

#### <a name="parameters"></a>パラメーター
* `startTime` セッションの履歴の検討を開始時刻。
* `endTime` セッションの履歴を考えると終了時刻。
* `maxActivities` 取得するユーザー アクティビティの最大数。
* `completion` 完了時に実行するコード ブロックです。
* `completionBlock` 完了時に実行するコード ブロックです。 これは、利用状況の履歴へのアクセスを提供します。