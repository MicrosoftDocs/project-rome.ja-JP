---
title: MCDAppServiceConnectionOpenedInfo
description: このクラスは、リモート デバイスが、ローカルの app service への接続を開いたときに発生しますが、MCDAppServiceProvider.connectionDidOpen イベントのデータを提供します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: b700c95d7ab093b47a94c856c25b946fc5df12d7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907554"
---
# <a name="class-mcdappserviceconnectionopenedinfo"></a><span data-ttu-id="e478c-104">クラス `MCDAppServiceConnectionOpenedInfo`</span><span class="sxs-lookup"><span data-stu-id="e478c-104">class `MCDAppServiceConnectionOpenedInfo`</span></span> 

```
@interface MCDAppServiceConnectionOpenedInfo : NSObject
```  

<span data-ttu-id="e478c-105">このクラスは、リモート デバイスが、ローカルの app service への接続を開いたときに発生しますが、MCDAppServiceProvider.connectionDidOpen イベントのデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="e478c-105">This class provides data for the MCDAppServiceProvider.connectionDidOpen event, which is raised when a remote device opens a connection to a local app service.</span></span>

## <a name="properties"></a><span data-ttu-id="e478c-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e478c-106">Properties</span></span>

### <a name="appserviceconnection"></a><span data-ttu-id="e478c-107">appServiceConnection</span><span class="sxs-lookup"><span data-stu-id="e478c-107">appServiceConnection</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceConnection* appServiceConnection;`

<span data-ttu-id="e478c-108">ローカル アプリ サービスとリモート デバイス間の接続を表す MCDAppServiceConnection インスタンス。</span><span class="sxs-lookup"><span data-stu-id="e478c-108">An MCDAppServiceConnection instance representing the connection between the local app service and the remote device.</span></span>

### <a name="remotesystemapp"></a><span data-ttu-id="e478c-109">RemoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="e478c-109">remoteSystemApp</span></span>
`@property(nonatomic, readonly, nullable) MCDRemoteSystemApp* remoteSystemApp;`

<span data-ttu-id="e478c-110">ローカルの app service への接続を開始した MCDRemoteSystemApp リモート アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="e478c-110">The MCDRemoteSystemApp remote application that initiated a connection to the local app service.</span></span>