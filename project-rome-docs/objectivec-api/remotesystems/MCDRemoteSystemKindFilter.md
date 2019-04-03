---
title: MCDRemoteSystemKindFilter
description: リモート システムのデバイスの種類に基づいてフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 162e8f881b532fae50f6d301149b50c5ddf344b5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907264"
---
# <a name="class-mcdremotesystemkindfilter"></a>クラス `MCDRemoteSystemKindFilter` 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

リモート システムのデバイスの種類に基づいてフィルター処理するために使用するクラスです。

## <a name="properties"></a>プロパティ

### <a name="kinds"></a>種類
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

フィルター処理するためのデバイスの種類を示す文字列の配列。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithkinds"></a>filterWithKinds
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

種類でフィルター処理するこのクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `kinds`

 フィルター処理するためのデバイスの種類を示す文字列の配列。

#### <a name="returns"></a>戻り値
種類でフィルター処理された MCDRemoteSystemKindFilter オブジェクトを返します。

### <a name="initwithkinds"></a>initWithKinds
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

種類でフィルター処理するこのクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `kinds` 

フィルター処理するためのデバイスの種類を示す文字列の配列。

#### <a name="returns"></a>戻り値
種類で初期化 MCDRemoteSystemKindFilter オブジェクトを返します。