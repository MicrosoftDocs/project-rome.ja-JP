---
title: MCDAppServiceConnectionOpenedInfo
description: このクラスは、リモート デバイスが、ローカルの app service への接続を開いたときに発生しますが、MCDAppServiceProvider.connectionDidOpen イベントのデータを提供します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: b700c95d7ab093b47a94c856c25b946fc5df12d7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801074"
---
# <a name="class-mcdappserviceconnectionopenedinfo"></a><span data-ttu-id="41e47-104">クラス `MCDAppServiceConnectionOpenedInfo`</span><span class="sxs-lookup"><span data-stu-id="41e47-104">class `MCDAppServiceConnectionOpenedInfo`</span></span> 

```
@interface MCDAppServiceConnectionOpenedInfo : NSObject
```  

<span data-ttu-id="41e47-105">このクラスは、リモート デバイスが、ローカルの app service への接続を開いたときに発生しますが、MCDAppServiceProvider.connectionDidOpen イベントのデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="41e47-105">This class provides data for the MCDAppServiceProvider.connectionDidOpen event, which is raised when a remote device opens a connection to a local app service.</span></span>

## <a name="properties"></a><span data-ttu-id="41e47-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="41e47-106">Properties</span></span>

### <a name="appserviceconnection"></a><span data-ttu-id="41e47-107">appServiceConnection</span><span class="sxs-lookup"><span data-stu-id="41e47-107">appServiceConnection</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceConnection* appServiceConnection;`

<span data-ttu-id="41e47-108">ローカル アプリ サービスとリモート デバイス間の接続を表す MCDAppServiceConnection インスタンス。</span><span class="sxs-lookup"><span data-stu-id="41e47-108">An MCDAppServiceConnection instance representing the connection between the local app service and the remote device.</span></span>

### <a name="remotesystemapp"></a><span data-ttu-id="41e47-109">RemoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="41e47-109">remoteSystemApp</span></span>
`@property(nonatomic, readonly, nullable) MCDRemoteSystemApp* remoteSystemApp;`

<span data-ttu-id="41e47-110">ローカルの app service への接続を開始した MCDRemoteSystemApp リモート アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="41e47-110">The MCDRemoteSystemApp remote application that initiated a connection to the local app service.</span></span>