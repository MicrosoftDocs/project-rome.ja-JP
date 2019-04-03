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
# <a name="class-mcdremotesystemremovedeventargs"></a><span data-ttu-id="a71fa-104">クラス `MCDRemoteSystemRemovedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="a71fa-104">class `MCDRemoteSystemRemovedEventArgs`</span></span> 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

<span data-ttu-id="a71fa-105">MCDRemoteSystemWatcher.remoteSystemRemoved イベントのイベント引数。</span><span class="sxs-lookup"><span data-stu-id="a71fa-105">Event arguments for the MCDRemoteSystemWatcher.remoteSystemRemoved event.</span></span>

## <a name="properties"></a><span data-ttu-id="a71fa-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a71fa-106">Properties</span></span>

### <a name="remotesystem"></a><span data-ttu-id="a71fa-107">RemoteSystem</span><span class="sxs-lookup"><span data-stu-id="a71fa-107">remoteSystem</span></span>
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

<span data-ttu-id="a71fa-108">削除された MCDRemoteSystem リモート システム。</span><span class="sxs-lookup"><span data-stu-id="a71fa-108">The MCDRemoteSystem remote system that was removed.</span></span> <span data-ttu-id="a71fa-109">このイベントの後このリモート システムで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a71fa-109">This remote system should not be used after this event.</span></span>