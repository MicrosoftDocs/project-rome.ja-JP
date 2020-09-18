---
title: MCDRemoteSystemKindFilter
description: MCDRemoteSystemKindFilter クラスについて説明します。 このクラスは、デバイスの種類に基づいてリモートシステムをフィルター処理するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: eb0799fe3c2c9831c7963d2d062f39fbf458689e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760676"
---
# <a name="class-mcdremotesystemkindfilter"></a>講義 `MCDRemoteSystemKindFilter` 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

デバイスの種類に基づいてリモートシステムをフィルター処理するために使用されるクラス。

## <a name="properties"></a>Properties

### <a name="kinds"></a>さまざま
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

フィルター処理の対象となるデバイスの種類を示す文字列の配列。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithkinds"></a>filterWithKinds
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

種類に基づいてフィルター処理された、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `kinds`

 フィルター処理の対象となるデバイスの種類を示す文字列の配列。

#### <a name="returns"></a>戻り値
種類を指定してフィルター処理された MCDRemoteSystemKindFilter オブジェクトを返します。

### <a name="initwithkinds"></a>initWithKinds
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

種類に基づいてフィルター処理された、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `kinds` 

フィルター処理の対象となるデバイスの種類を示す文字列の配列。

#### <a name="returns"></a>戻り値
種類で初期化された MCDRemoteSystemKindFilter オブジェクトを返します。