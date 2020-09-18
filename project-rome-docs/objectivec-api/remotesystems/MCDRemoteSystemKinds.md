---
title: MCDRemoteSystemKinds
description: MCDRemoteSystemKinds クラスについて説明します。 このクラスには、リモートシステムデバイスの種類を表す文字列フィールドが含まれています。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 978188b1a17c1acdd257fdc97c64fd17b3a1f618
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760666"
---
# <a name="class-mcdremotesystemkinds"></a>講義 `MCDRemoteSystemKinds` 

```
@interface MCDRemoteSystemKinds : NSObject
```

リモートシステムデバイスの種類を表す文字列フィールドが含まれています。

## <a name="properties"></a>Properties

### <a name="desktop"></a>デスクトップ
`@property(class, readonly, readonly, nonnull) NSString* desktop;`

デスクトップデバイスの種類の正規名。

### <a name="holographic"></a>holographic
`@property(class, readonly, readonly, nonnull) NSString* holographic;`

Holographic デバイスタイプの正規名。

### <a name="hub"></a>ハブ
`@property(class, readonly, readonly, nonnull) NSString* hub;`

ハブデバイスタイプの正規名。

### <a name="phone"></a>phone
`@property(class, readonly, readonly, nonnull) NSString* phone;`

Phone デバイスタイプの正規名。

### <a name="xbox"></a>本体
`@property(class, readonly, readonly, nonnull) NSString* xbox;`

Xbox デバイスタイプの正規名。

### <a name="laptop"></a>本体
`@property(class, readonly, readonly, nonnull) NSString* laptop;`

ラップトップデバイスの標準の名前。

> **注:** Surface Book を含むすべての Microsoft Surface デバイスは、タブレットデバイスと見なされます。

### <a name="iot"></a>iot
`@property(class, readonly, readonly, nonnull) NSString* iot;`

IoT デバイスの標準の名前。

### <a name="tablet"></a>タブレット
`@property(class, readonly, readonly, nonnull) NSString* tablet;`

タブレットデバイスの標準の名前。
