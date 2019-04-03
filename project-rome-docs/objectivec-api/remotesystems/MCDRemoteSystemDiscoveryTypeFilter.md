---
title: MCDRemoteSystemDiscoveryTypeFilter
description: リモート システムの検出の種類に基づいてフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 8054d378f203d5cde29af6b4452cc03e15e24828
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907524"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a>クラス `MCDRemoteSystemDiscoveryTypeFilter` 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

リモート システムの検出の種類に基づいてフィルター処理するために使用するクラスです。

## <a name="properties"></a>プロパティ

### <a name="type"></a>type
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

検出の種類をフィルター処理します。

> 注:Android では、接続されているデバイス プラットフォームでのみ使用できます Bluetooth Android 8.0 (Oreo) を実行しているシステムまたはそれ以降。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>パラメーター 
* `discoveryType` 検出の種類をフィルター処理します。

#### <a name="returns"></a>戻り値
指定した型の値では、このクラスの新しいインスタンス。 値は、一度に複数のフィルターを適用するには、まとめて AND'ed を指定できます。

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>パラメーター 
* `discoveryType` 検出の種類をフィルター処理します。

#### <a name="returns"></a>戻り値
指定した型の値では、このクラスの新しいインスタンス。 値は、一度に複数のフィルターを適用するには、まとめて AND'ed を指定できます。