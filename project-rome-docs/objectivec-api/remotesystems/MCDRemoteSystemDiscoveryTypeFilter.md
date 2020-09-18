---
title: MCDRemoteSystemDiscoveryTypeFilter
description: MCDRemoteSystemDiscoveryTypeFilter クラスについて説明します。 このクラスは、検出の種類に基づいてリモートシステムをフィルター処理するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: a38036811fda38df944e67e431f864c33d1c335d
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760696"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a>講義 `MCDRemoteSystemDiscoveryTypeFilter` 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

探索の種類に基づいてリモートシステムをフィルター処理するために使用されるクラス。

## <a name="properties"></a>Properties

### <a name="type"></a>type
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

フィルター処理の対象となる検出の種類。

> 注: Android では、接続されているデバイスプラットフォームは、Android 8.0 (Oreo) 以降を実行しているシステムでのみ Bluetooth を使用できます。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>パラメーター 
* `discoveryType` フィルター処理の対象となる検出の種類。

#### <a name="returns"></a>戻り値
指定された型の値を持つ、このクラスの新しいインスタンス。 一度に複数のフィルターを適用するために、値を組み合わせて使用できます。

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>パラメーター 
* `discoveryType` フィルター処理の対象となる検出の種類。

#### <a name="returns"></a>戻り値
指定された型の値を持つ、このクラスの新しいインスタンス。 一度に複数のフィルターを適用するために、値を組み合わせて使用できます。