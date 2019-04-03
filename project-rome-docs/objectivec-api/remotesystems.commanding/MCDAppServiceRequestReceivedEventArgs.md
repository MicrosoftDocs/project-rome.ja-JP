---
title: MCDAppServiceRequestReceivedEventArgs
description: 「要求を受信」のイベントに関連付けられたデータが含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5fa7a3b2742d5ecacd7c6a90e39e86f4c46f2218
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908564"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a>クラス `MCDAppServiceRequestReceivedEventArgs` 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
「要求を受信」のイベントに関連付けられたデータが含まれています。

## <a name="properties"></a>プロパティ

### <a name="request"></a>要求
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

リモート デバイスによって送信される要求。