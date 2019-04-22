---
title: MCDUserActivityAttribution
description: このクラスは、ユーザーの利用状況のグラフィカル要素を管理します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 94ae2f5afef24a1f4e320014ac930d67b657b0d7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801544"
---
# <a name="class-mcduseractivityattribution"></a>クラス `MCDUserActivityAttribution`

```
@interface MCDUserActivityAttribution : NSObject
```

このクラスは、ユーザーの利用状況のグラフィカル要素を管理します。

## <a name="properties"></a>プロパティ

### <a name="iconuri"></a>iconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

アイコン イメージの URI。

### <a name="alternatetext"></a>AlternateText
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

(スクリーン リーダーで使用する) のアイコンの画像を説明するテキスト。

### <a name="addimagequery"></a>addImageQuery
`@property(nonatomic, assign) BOOL addImageQuery;`

Windows イメージから指定された URI にクエリ文字列を追加するを許可するかどうかを判断します**IconUri**イメージを取得するときにします。 クエリ文字列には、ユーザーの表示、ハイ コントラスト設定、およびユーザーの言語の DPI に基づく最適なイメージを選択するのに役立つ情報が含まれています。 このクエリ文字列は、スケール、コントラスト設定、および言語を指定します。たとえば、 **IconUri** "www.website.com/images/hello.png"の値になります"www.website.com/images/hello.png?ms-scale=100 & ms コントラスト = 標準 & ms lang = en-米国"。

## <a name="constructors"></a>コンストラクター

### <a name="useractivityattributionwithiconuri"></a>userActivityAttributionWithIconUri
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

アイコンの URI をこのクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `iconUri` 

作成されたインスタンスに属している、アイコンの URI の文字列値。

#### <a name="returns"></a>戻り値
アイコンの uri を使用して初期化 MCDUserActivityAttribution オブジェクトを返します。

### <a name="attributionwithiconuri"></a>attributionWithIconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

アイコンの uri への帰属をこのクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `iconUri` 

作成されたインスタンスに属している、アイコンの URI の文字列値。

#### <a name="returns"></a>戻り値
MCDUserActivityAttribution オブジェクト属性とアイコンの uri を返します。