---
title: MCDRemoteSystemStatusTypeFilter
description: リモート システムの可用性の状態の種類に基づいてフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 201570c16a8eb9cf1a31e450b3408c8ab255fe1a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907124"
---
# <a name="class-mcdremotesystemstatustypefilter"></a>クラス `MCDRemoteSystemStatusTypeFilter`

```
@interface MCDRemoteSystemStatusTypeFilter : NSObject <MCDRemoteSystemFilter>
```

リモート システムの可用性の状態の種類に基づいてフィルター処理するために使用するクラスです。

## <a name="properties"></a>プロパティ

### <a name="type"></a>type
`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` このフィルターのインスタンスのリモート システムのステータスの種類です。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a>パラメーター 
* `statusType` フィルター処理するための可用性ステータスの種類を示す値。

#### <a name="returns"></a>戻り値
種類でフィルター処理 MCDRemoteSystemStatusTypeFilter オブジェクトを返します。

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a>パラメーター 
* `statusType` 

フィルター処理するための可用性ステータスの種類を示す値。

#### <a name="returns"></a>戻り値
型を使用して初期化 MCDRemoteSystemStatusTypeFilter オブジェクトを返します。