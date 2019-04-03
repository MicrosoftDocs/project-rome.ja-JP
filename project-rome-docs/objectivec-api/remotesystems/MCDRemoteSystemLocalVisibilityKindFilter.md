---
title: MCDRemoteSystemLocalVisibilityKindFilter
description: リモート システムの探索時に、ローカル (呼び出し) アプリケーションの表示優先順位を設定するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: b54614c1ee0a820e605df05768c164d07a5a9464
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909574"
---
# <a name="class-mcdremotesystemlocalvisibilitykindfilter"></a>クラス `MCDRemoteSystemLocalVisibilityKindFilter` 

```
@interface MCDRemoteSystemLocalVisibilityKindFilter : NSObject <MCDRemoteSystemFilter>
```  

リモート システムの探索時に、ローカル (呼び出し) アプリケーションの表示優先順位を設定するために使用するクラスです。

## <a name="properties"></a>プロパティ

### <a name="kind"></a>種類
`@property(nonatomic, readonly) MCDRemoteSystemLocalVisibilityKind kind;`

フィルター処理の可視性の設定。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithkind"></a>filterWithKind
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

作成して、このクラスのインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター
* `localVisibilityKind` 

フィルターにローカル アプリの可視性の設定を示す MCDRemoteSystemLocalVisibilityKind 値。

#### <a name="returns"></a>戻り値
種類でフィルター処理された MCDRemoteSystemLocalVisibilityKind オブジェクトを返します。

### <a name="initwithkind"></a>initWithKind
`- (nullable instancetype)initWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

作成して、このクラスのインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター
* `localVisibilityKind` 

フィルターにローカル アプリの可視性の設定を示す MCDRemoteSystemLocalVisibilityKind 値。

#### <a name="returns"></a>戻り値
種類で初期化 MCDRemoteSystemLocalVisibilityKind オブジェクトを返します。