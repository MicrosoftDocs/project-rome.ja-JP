---
title: MCDRemoteSystemAuthorizationKindFilter
description: MCDRemoteSystemAuthorizationKindFilter クラスについて説明します。 このクラスは、承認の種類に基づいてリモートシステムをフィルター処理するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: a48c9aeacf262146a12da6fd691e853cb7dde199
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760706"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a>講義 `MCDRemoteSystemAuthorizationKindFilter` 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

承認の種類に基づいてリモートシステムをフィルター処理するために使用されるクラス。

## <a name="properties"></a>Properties

### <a name="kind"></a>kind
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

フィルター処理の対象となる承認の種類。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithkind"></a>filterWithKind
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

MCDRemoteSystemAuthorizationKind でフィルター処理された、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `authorizationKind` 

フィルター処理の対象となる承認の種類。

#### <a name="returns"></a>戻り値
指定された承認フィルターを持つ MCDRemoteSystemAuthorizationKindFilter オブジェクトを返します。

### <a name="initwithkind"></a>initWithKind
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

MCDRemoteSystemAuthorizationKind を持つこのクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `authorizationKind` 

フィルター処理の対象となる承認の種類。

#### <a name="returns"></a>戻り値
AuthorizationKind で初期化された MCDRemoteSystemAuthorizationKindFilter オブジェクトを返します。