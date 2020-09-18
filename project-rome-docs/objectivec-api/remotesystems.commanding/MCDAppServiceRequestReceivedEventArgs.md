---
title: MCDAppServiceRequestReceivedEventArgs
description: MCDAppServiceRequestReceivedEventArgs クラスについて説明します。 このクラスには、"要求を受信しました" イベントに関連付けられたデータが含まれています。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 9a4a64ae163a0cc553196914da2f42d8d32e6ade
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760766"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a>講義 `MCDAppServiceRequestReceivedEventArgs` 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
"要求を受信しました" イベントに関連付けられたデータを格納します。

## <a name="properties"></a>Properties

### <a name="request"></a>request
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

リモートデバイスによって送信された要求。