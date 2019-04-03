---
title: MCDRemoteSystemAppRegistrationPublishResult
description: クラスは、アカウントの発行のリモート システム アプリ情報の非同期結果を通信します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5e28e2533d14839384bcd2cfac2db3fc368a6207
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909924"
---
# <a name="class-mcdremotesystemappregistrationpublishresult"></a><span data-ttu-id="86fb6-104">クラス `MCDRemoteSystemAppRegistrationPublishResult`</span><span class="sxs-lookup"><span data-stu-id="86fb6-104">class `MCDRemoteSystemAppRegistrationPublishResult`</span></span> 

```
@interface MCDRemoteSystemAppRegistrationPublishResult : NSObject
```  

<span data-ttu-id="86fb6-105">このクラスは、アカウントの発行のリモート システム アプリ情報の非同期結果を通信します。</span><span class="sxs-lookup"><span data-stu-id="86fb6-105">This class communicates the async result of publishing remote system app information for an account.</span></span> <span data-ttu-id="86fb6-106">利用できないネットワークなどの特定の一時的な問題が発生した場合の発行を再試行するアプリによってを通じて、この結果、エラー状態を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86fb6-106">The error statuses communicated through this result should be used by the app to retry publishing in the event of certain transient conditions like the network being unavailable.</span></span>

## <a name="properties"></a><span data-ttu-id="86fb6-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="86fb6-107">Properties</span></span>

### <a name="status"></a><span data-ttu-id="86fb6-108">status</span><span class="sxs-lookup"><span data-stu-id="86fb6-108">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAppRegistrationPublishStatus status;`

<span data-ttu-id="86fb6-109">発行操作のステータスの列挙型。</span><span class="sxs-lookup"><span data-stu-id="86fb6-109">Status enum of the publish operation.</span></span>