---
title: MCDConnectedDevicesAccessTokenRequestedEventArgs
description: トークンを要求する必要があるときに発生する MCDConnectedDevicesAccessTokenRequested によって返されます。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: d50b7dc75944e3c3df553c95247b0ec578a477a4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800744"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequestedeventargs"></a>クラス `MCDConnectedDevicesAccessTokenRequestedEventArgs` 

```
@interface MCDConnectedDevicesAccessTokenRequestedEventArgs : NSObject
```  

トークンを要求する必要があるときに発生する MCDConnectedDevicesAccessTokenRequested によって返されます。 

## <a name="properties"></a>プロパティ

### <a name="request"></a>要求
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccessTokenRequest* request;`

この MCDConnectedDevicesAccessTokenRequest に関連付けられた要求。