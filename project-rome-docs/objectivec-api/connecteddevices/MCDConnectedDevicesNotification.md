---
title: MCDConnectedDevicesNotification
description: 通知を処理の結果。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 2a60e2cab26c3d2df39314aa5b61a65de1529356
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800604"
---
# <a name="class-mcdconnecteddevicesnotification"></a>クラス `MCDConnectedDevicesNotification` 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
通知を処理の結果。

## <a name="methods"></a>メソッド

### <a name="tryparse"></a>tryParse

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

APNS からの MCDConnectedDevicesNotification を解析する試行は、マップを書式設定されます。

#### <a name="parameters"></a>パラメーター 
* `dictionary` 

処理のため、接続しているデバイス プラットフォームに APNS 通知を受信するマップです。
