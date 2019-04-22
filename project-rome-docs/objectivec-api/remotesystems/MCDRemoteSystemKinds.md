---
title: MCDRemoteSystemKinds
description: リモート システムのデバイスの種類を表す文字列フィールドが含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 701bc4662fc8d46009889645bab6e4ee83fdb959
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801274"
---
# <a name="class-mcdremotesystemkinds"></a>クラス `MCDRemoteSystemKinds` 

```
@interface MCDRemoteSystemKinds : NSObject
```

リモート システムのデバイスの種類を表す文字列フィールドが含まれています。

## <a name="properties"></a>プロパティ

### <a name="desktop"></a>デスクトップ
`@property(class, readonly, readonly, nonnull) NSString* desktop;`

デスクトップ デバイスの種類の正規名。

### <a name="holographic"></a>Holographic
`@property(class, readonly, readonly, nonnull) NSString* holographic;`

Holographic デバイスの種類の正規名。

### <a name="hub"></a>ハブ
`@property(class, readonly, readonly, nonnull) NSString* hub;`

ハブのデバイスの種類の正規名。

### <a name="phone"></a>[電話]
`@property(class, readonly, readonly, nonnull) NSString* phone;`

Phone デバイスの種類の正規名。

### <a name="xbox"></a>Xbox
`@property(class, readonly, readonly, nonnull) NSString* xbox;`

Xbox デバイスの種類の正規名。

### <a name="laptop"></a>ノート PC
`@property(class, readonly, readonly, nonnull) NSString* laptop;`

ラップトップ コンピューター デバイスの種類の正規名。

> **注:** Surface Book を含め、すべての Microsoft Surface デバイスでは、タブレット デバイスと見なされます。

### <a name="iot"></a>iot
`@property(class, readonly, readonly, nonnull) NSString* iot;`

IoT デバイスの種類の正規名。

### <a name="tablet"></a>タブレット
`@property(class, readonly, readonly, nonnull) NSString* tablet;`

タブレット デバイスの種類の正規名。
