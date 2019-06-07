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
# <a name="class-mcdremotesystemwatcher"></a>クラス `MCDRemoteSystemWatcher`

```
@interface MCDRemoteSystemWatcher : NSObject
```

リモート システムを検出するために使用するクラスです。 

## <a name="properties"></a>プロパティ

### <a name="remotesystemadded"></a>remoteSystemAdded
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

新しいリモート システムが検出されたときのイベントです。

### <a name="remotesystemupdated"></a>remoteSystemUpdated
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

この検出のセッションで以前に検出されたリモート システムが変更されたときから proximally のイベントは、クラウドに接続された、またはその逆に接続されています。 

### <a name="remotesystemremoved"></a>remoteSystemRemoved
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

リモート システムが削除されたときのイベントです。 

### <a name="enumerationcompleted"></a>enumerationCompleted
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

現在の探索可能なデバイスの初期検出が完了するとイベントです。  検出プロセスは引き続き実行され、既存のリモート システムのセットが変更された場合は、追加のイベントを発生させます。

### <a name="erroroccurred"></a>errorOccurred
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

探索中にエラーが発生したときのイベントです。 可能であれば、検出プロセスが続行されます。 たとえば、値は、エラーが発生した場合**MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**エラーがクラウド検出 (参照にのみ適用されるため位の検出が継続**MCDRemoteSystemDiscoveryType**)。

## <a name="constructors"></a>コンストラクター

### <a name="watcher"></a>監視
```
+ (nullable instancetype)watcher;
```

作成し、このクラスの新しいインスタンスを初期化します。

#### <a name="returns"></a>戻り値 
このクラスの新しいインスタンスを返します。

### <a name="watcherwithfilters"></a>watcherWithFilters
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

作成し、フィルターを使用してこのクラスの新しいインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `filters` 

デバイスの検出プロセスで使用するフィルターの配列。

#### <a name="returns"></a>戻り値 
フィルターを使用した MCDRemoteSystemWatcher オブジェクトを返します。

### <a name="initwithfilters"></a>initWithFilters
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

作成し、フィルターを使用してこのクラスの新しいインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `filters` 

デバイスの検出プロセスで使用するフィルターの配列。

#### <a name="returns"></a>戻り値 
フィルターを使用して初期化 MCDRemoteSystemWatcher オブジェクトを返します。

## <a name="methods"></a>メソッド

### <a name="start"></a>start
`- (void)start;`

リモート システムの検出を開始します。

### <a name="stop"></a>stop
`- (void)stop;` 

アクティブな探索を停止します。
