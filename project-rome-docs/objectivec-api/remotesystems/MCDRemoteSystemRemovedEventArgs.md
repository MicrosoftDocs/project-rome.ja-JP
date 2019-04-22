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
# <a name="class-mcdremotesystemremovedeventargs"></a><span data-ttu-id="99a91-104">クラス `MCDRemoteSystemRemovedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="99a91-104">class `MCDRemoteSystemRemovedEventArgs`</span></span> 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

<span data-ttu-id="99a91-105">MCDRemoteSystemWatcher.remoteSystemRemoved イベントのイベント引数。</span><span class="sxs-lookup"><span data-stu-id="99a91-105">Event arguments for the MCDRemoteSystemWatcher.remoteSystemRemoved event.</span></span>

## <a name="properties"></a><span data-ttu-id="99a91-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="99a91-106">Properties</span></span>

### <a name="remotesystem"></a><span data-ttu-id="99a91-107">RemoteSystem</span><span class="sxs-lookup"><span data-stu-id="99a91-107">remoteSystem</span></span>
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

<span data-ttu-id="99a91-108">削除された MCDRemoteSystem リモート システム。</span><span class="sxs-lookup"><span data-stu-id="99a91-108">The MCDRemoteSystem remote system that was removed.</span></span> <span data-ttu-id="99a91-109">このイベントの後このリモート システムで使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99a91-109">This remote system should not be used after this event.</span></span>