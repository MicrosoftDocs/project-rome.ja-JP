---
title: MCDRemoteSystemRemovedEventArgs
description: RemoteSystemWatcher RemoteSystemRemoved イベントのイベント引数。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 652107473e7b716493483057b090f558d82425a2
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801734"
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