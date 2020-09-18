---
title: MCDRemoteSystemAddedEventArgs
description: MCDRemoteSystemAddedEventArgs クラスについて説明します。 このクラスは、RemoteSystemWatcher RemoteSystemAdded イベントのイベント引数用です。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 3b9058cba0f4469fbbf60e89586c08b27f34eb4b
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760716"
---
# <a name="class-mcdremotesystemaddedeventargs"></a>講義 `MCDRemoteSystemAddedEventArgs` 

```
@interface MCDRemoteSystemAddedEventArgs : NSObject
```  
RemoteSystemWatcher RemoteSystemAdded イベントのイベント引数。

## <a name="properties"></a>Properties

### <a name="remotesystem"></a>remoteSystem
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

追加されたリモートシステム。