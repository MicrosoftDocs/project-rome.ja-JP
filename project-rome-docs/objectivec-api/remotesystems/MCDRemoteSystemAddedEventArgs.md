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
# <a name="class-mcdremotesystemaddedeventargs"></a><span data-ttu-id="923de-105">講義 `MCDRemoteSystemAddedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="923de-105">class `MCDRemoteSystemAddedEventArgs`</span></span> 

```
@interface MCDRemoteSystemAddedEventArgs : NSObject
```  
<span data-ttu-id="923de-106">RemoteSystemWatcher RemoteSystemAdded イベントのイベント引数。</span><span class="sxs-lookup"><span data-stu-id="923de-106">Event arguments for the RemoteSystemWatcher RemoteSystemAdded event.</span></span>

## <a name="properties"></a><span data-ttu-id="923de-107">Properties</span><span class="sxs-lookup"><span data-stu-id="923de-107">Properties</span></span>

### <a name="remotesystem"></a><span data-ttu-id="923de-108">remoteSystem</span><span class="sxs-lookup"><span data-stu-id="923de-108">remoteSystem</span></span>
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

<span data-ttu-id="923de-109">追加されたリモートシステム。</span><span class="sxs-lookup"><span data-stu-id="923de-109">The remote system that was added.</span></span>