---
title: MCDRemoteSystemAuthorizationKindFilter
description: リモート システムの承認の種類に基づいてフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: da68c7a0eacd2018332d5e2fe5c8e3c906f473f8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907644"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a>クラス `MCDRemoteSystemAuthorizationKindFilter` 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

リモート システムの承認の種類に基づいてフィルター処理するために使用するクラスです。

## <a name="properties"></a>プロパティ

### <a name="kind"></a>種類
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

承認の種類をフィルター処理します。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithkind"></a>filterWithKind
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

MCDRemoteSystemAuthorizationKind でフィルター処理するこのクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `authorizationKind` 

承認の種類をフィルター処理します。

#### <a name="returns"></a>戻り値
指定された承認フィルターを使用して MCDRemoteSystemAuthorizationKindFilter オブジェクトを返します。

### <a name="initwithkind"></a>initWithKind
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

MCDRemoteSystemAuthorizationKind でこのクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `authorizationKind` 

承認の種類をフィルター処理します。

#### <a name="returns"></a>戻り値
AuthorizationKind 初期化 MCDRemoteSystemAuthorizationKindFilter オブジェクトを返します。