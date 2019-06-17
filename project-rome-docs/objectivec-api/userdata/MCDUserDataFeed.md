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
# <a name="class-mcduserdatafeed"></a>クラス `MCDUserDataFeed`

```
@interface MCDUserDataFeed : NSObject
```

このクラスは、接続されているデバイス プラットフォームのバックエンドでユーザーに固有のデータを同期する責任を負います。 同期されるデータによって異なりますが **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** のインスタンスが含まれています。

## <a name="properties"></a>プロパティ

### <a name="syncstatus"></a>syncStatus
`@property(nonatomic, readonly) MCDUserDataSyncStatus syncStatus;`

ユーザー データの同期の現在の状態について説明します。

### <a name="syncstatuschanged"></a>syncStatusChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserDataFeed*, MCDUserDataFeedSyncStatusChangedEventArgs*>* syncStatusChanged;`

UserDataFeed の同期の状態が変更されたときのイベントです。

### <a name="daystosync"></a>daysToSync
`@property(nonatomic, readwrite) NSInteger daysToSync;`

日数が 30 未満にする必要がありますが、同期するデータの数。  サーバーによって決まりますが既定値を表します。

## <a name="constructors"></a>コンストラクター

### <a name="getforaccount"></a>getForAccount
`+ (nullable instancetype)getForAccount:(nonnull MCDConnectedDevicesAccount*)userAccount
                                   platform:(nonnull MCDConnectedDevicesPlatform*)platform
                         activitySourceHost:(nonnull NSString*)activitySourceHost;`

作成し、ユーザー アカウント、プラットフォームのインスタンス、およびクロス プラットフォーム アプリの id。 このクラスの新しいインスタンスを初期化します

#### <a name="parameters"></a>パラメーター
* `userAccount` 

このデータの関連付けられているユーザー アカウント。

* `platform` 

**MCDPlatform**がこのアプリの接続されたデバイスの機能用に初期化されたインスタンス。

* `activitySourceHost` 

クロス プラットフォーム アプリの id。 これは、Microsoft 開発者向けダッシュ ボードの登録の過程で取得されます。

#### <a name="returns"></a>戻り値
このクラスのインスタンスを返します。

## <a name="methods"></a>メソッド

> [!WARNING]
> この関数は非推奨とされます、'subscribeToSyncScopesWithResultAsync' 代わりにします。

### <a name="subscribetosyncscopesasync"></a>subscribeToSyncScopesAsync
`- (void)subscribeToSyncScopesAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(BOOL, NSError* _Nullable)) callback  __attribute__((deprecated("Use subscribeToSyncScopesWithResultAsync instead")));`

追加**MCDUserDataFeedSyncScope**この MCDUserDataFeed するインスタンス。  に従ってこの MCDUserDataFeed が同期されている、 **MCDUserDataFeedSyncScope**インスタンスを指定します。

#### <a name="parameters"></a>パラメーター

* `syncScopes` 配列の**MCDSyncScope**インスタンス。

* `callback`

コールバックの結果は、サブスクリプションが成功したかどうかを示します。

### <a name="subscribetosyncscopeswithresultasync"></a>subscribeToSyncScopesWithResultAsync
`- (void)subscribeToSyncScopesWithResultAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(MCDUserDataFeedSubscribeResult* _Nullable, NSError* _Nullable)) callback;`

追加**MCDUserDataFeedSyncScope**この MCDUserDataFeed するインスタンス。  に従ってこの MCDUserDataFeed が同期されている、 **MCDUserDataFeedSyncScope**インスタンスを指定します。

#### <a name="parameters"></a>パラメーター

* `syncScopes` 配列の**MCDSyncScope**インスタンス。

* `callback`

コールバックの結果は、サブスクリプションが成功したかどうかを示します。

### <a name="startsync"></a>startSync
`- (void)startSync;`

接続されているデバイス プラットフォームでは、同期プロセスを開始します。 この操作中に、 **syncStatus**プロパティが更新され、変更イベントが発生します。