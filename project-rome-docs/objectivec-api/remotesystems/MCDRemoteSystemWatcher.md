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
# <a name="class-mcdremotesystemwatcher"></a>講義 `MCDRemoteSystemWatcher`

```
@interface MCDRemoteSystemWatcher : NSObject
```

リモートシステムを検出するために使用されるクラス。 

## <a name="properties"></a>Properties

### <a name="remotesystemadded"></a>remoteSystemAdded
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

新しいリモートシステムが検出されたときのイベントです。

### <a name="remotesystemupdated"></a>remoteSystemUpdated
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

この探索セッションで以前に検出されたリモートシステムが、接続されているクラウドに接続されている proximally、またはその逆の場合に発生するイベントです。 

### <a name="remotesystemremoved"></a>remoteSystemRemoved
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

リモートシステムが削除されたときのイベントです。 

### <a name="enumerationcompleted"></a>enumerationCompleted
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

現在探索可能なデバイスの初期検出が終了したときのイベントです。  既存のリモートシステムのセットが変更されると、検出プロセスが引き続き実行され、追加のイベントが発生します。

### <a name="erroroccurred"></a>エラーが発生しました
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

検出中にエラーが発生した場合のイベントです。 可能であれば、検出プロセスは続行されます。 たとえば、エラーが **MCDRemoteSystemWatcherError**の値と共に発生した場合、エラーは cloud discovery にのみ適用されるため、位 discovery は続行される可能性があります (「 **MCDRemoteSystemDiscoveryType**」を参照してください)。

## <a name="constructors"></a>コンストラクター

### <a name="watcher"></a>監視
```
+ (nullable instancetype)watcher;
```

このクラスの新しいインスタンスを作成して初期化します。

#### <a name="returns"></a>戻り値 
このクラスの新しいインスタンスを返します。

### <a name="watcherwithfilters"></a>watcherWithFilters
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

フィルターを使用して、このクラスの新しいインスタンスを作成して初期化します。

#### <a name="parameters"></a>パラメーター 
* `filters` 

デバイスの検出プロセスで使用するフィルターの配列。

#### <a name="returns"></a>戻り値 
フィルターを使用して MCDRemoteSystemWatcher オブジェクトを返します。

### <a name="initwithfilters"></a>initWithFilters
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

フィルターを使用して、このクラスの新しいインスタンスを作成して初期化します。

#### <a name="parameters"></a>パラメーター 
* `filters` 

デバイスの検出プロセスで使用するフィルターの配列。

#### <a name="returns"></a>戻り値 
フィルターを使用して初期化された MCDRemoteSystemWatcher オブジェクトを返します。

## <a name="methods"></a>メソッド

### <a name="start"></a>start
`- (void)start;`

リモートシステムの検出を開始します。

### <a name="stop"></a>stop
`- (void)stop;` 

アクティブな探索を停止します。
