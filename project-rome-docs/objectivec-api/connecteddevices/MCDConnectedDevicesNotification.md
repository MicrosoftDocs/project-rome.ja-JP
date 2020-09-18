---
title: MCDConnectedDevicesNotification
description: MCDConnectedDevicesNotification クラスについて説明します。 このクラスは、通知を処理した結果です。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: c05ac896113b8196d1dd3854a14ef5730552435f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761016"
---
# <a name="class-mcdconnecteddevicesnotification"></a>講義 `MCDConnectedDevicesNotification` 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
通知を処理した結果。

## <a name="methods"></a>メソッド

### <a name="tryparse"></a><C3>

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

APNS 形式のマップから MCDConnectedDevicesNotification の解析を試みます。

#### <a name="parameters"></a>パラメーター 
* `dictionary` 

処理のために APNS 通知から接続されたデバイスプラットフォームに受信したマップ。
