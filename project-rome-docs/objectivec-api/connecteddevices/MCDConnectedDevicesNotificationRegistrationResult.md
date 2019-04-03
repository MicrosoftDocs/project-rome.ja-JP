---
title: MCDConnectedDevicesNotificationRegistrationResult
description: アカウントの通知情報を登録するための非同期の結果を通信します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 9ee253ff1c07f498b42ccf0cd0edeb9937f31f59
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907744"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationresult"></a><span data-ttu-id="fe96a-104">クラス `MCDConnectedDevicesNotificationRegistrationResult`</span><span class="sxs-lookup"><span data-stu-id="fe96a-104">class `MCDConnectedDevicesNotificationRegistrationResult`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationResult : NSObject
```  
<span data-ttu-id="fe96a-105">MCDConnectedDevicesNotificationRegistrationResult では、アカウントの通知情報を登録するための非同期の結果を通信します。</span><span class="sxs-lookup"><span data-stu-id="fe96a-105">MCDConnectedDevicesNotificationRegistrationResult communicates the async result of registering notification information for an account.</span></span> <span data-ttu-id="fe96a-106">利用できないネットワークなどの特定の一時的な問題が発生した場合、登録を再試行するアプリによってを通じて、この結果、エラー状態を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fe96a-106">The error statuses communicated through this result should be used by the app to retry registration in the event of certain transient conditions like the network being unavailable.</span></span>

## <a name="properties"></a><span data-ttu-id="fe96a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fe96a-107">Properties</span></span>

### <a name="status"></a><span data-ttu-id="fe96a-108">status</span><span class="sxs-lookup"><span data-stu-id="fe96a-108">status</span></span>

`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationStatus status;`

<span data-ttu-id="fe96a-109">登録操作のステータスの列挙型。</span><span class="sxs-lookup"><span data-stu-id="fe96a-109">Status enum of the registration operation.</span></span>