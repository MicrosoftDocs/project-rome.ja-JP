---
title: MCDRemoteSystemWatcherError
description: エラーの説明は、検出プロセス中に、リモート システムの監視オブジェクトで発生した値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 3f65614396377b154b2a37493b8271ac54afb6fd
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907704"
---
# <a name="enum-mcdremotesystemwatchererror"></a>列挙型 `MCDRemoteSystemWatcherError` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemWatcherError)
```  
 エラーの説明は、検出プロセス中に、リモート システムの監視オブジェクトで発生した値が含まれています。

## <a name="fields"></a>フィールド

| 名前                              | 値 | 説明                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemWatcherErrorUnknown | 0 | ウォッチャーには、不明なエラーが発生しました。 |
| MCDRemoteSystemWatcherErrorInternetNotAvailable | 1 | インターネット接続が失われたため、エラーが発生しました。 |
| MCDRemoteSystemWatcherErrorAuthenticationError | 2 | 検出を実行するために使用されている ConnectedDevicesAccount を認証されていないため、エラーが発生しました。 | 
