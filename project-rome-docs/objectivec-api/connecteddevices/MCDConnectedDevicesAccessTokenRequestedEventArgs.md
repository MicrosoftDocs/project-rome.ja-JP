---
title: MCDConnectedDevicesAccessTokenRequestedEventArgs
description: トークンを要求する必要があるときに発生する MCDConnectedDevicesAccessTokenRequested によって返されます。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: d50b7dc75944e3c3df553c95247b0ec578a477a4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908324"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequestedeventargs"></a><span data-ttu-id="8dff7-104">クラス `MCDConnectedDevicesAccessTokenRequestedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="8dff7-104">class `MCDConnectedDevicesAccessTokenRequestedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenRequestedEventArgs : NSObject
```  

<span data-ttu-id="8dff7-105">トークンを要求する必要があるときに発生する MCDConnectedDevicesAccessTokenRequested によって返されます。</span><span class="sxs-lookup"><span data-stu-id="8dff7-105">Returned by MCDConnectedDevicesAccessTokenRequested, fired when there is a need to request a token.</span></span> 

## <a name="properties"></a><span data-ttu-id="8dff7-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8dff7-106">Properties</span></span>

### <a name="request"></a><span data-ttu-id="8dff7-107">要求</span><span class="sxs-lookup"><span data-stu-id="8dff7-107">request</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccessTokenRequest* request;`

<span data-ttu-id="8dff7-108">この MCDConnectedDevicesAccessTokenRequest に関連付けられた要求。</span><span class="sxs-lookup"><span data-stu-id="8dff7-108">The request associated with this MCDConnectedDevicesAccessTokenRequest.</span></span>