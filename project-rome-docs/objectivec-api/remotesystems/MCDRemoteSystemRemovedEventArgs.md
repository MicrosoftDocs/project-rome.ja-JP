---
title: MCDRemoteSystemRemovedEventArgs
description: RemoteSystemWatcher RemoteSystemRemoved イベントのイベント引数。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 652107473e7b716493483057b090f558d82425a2
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907044"
---
# <a name="class-mcdremotesystemremovedeventargs"></a>クラス `MCDRemoteSystemRemovedEventArgs` 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

MCDRemoteSystemWatcher.remoteSystemRemoved イベントのイベント引数。

## <a name="properties"></a>プロパティ

### <a name="remotesystem"></a>RemoteSystem
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

削除された MCDRemoteSystem リモート システム。 このイベントの後このリモート システムで使用する必要があります。