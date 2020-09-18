---
title: MCDUserActivityAttribution
description: MCDUserActivityAttribution クラスについて説明します。 このクラスは、ユーザーアクティビティのグラフィカル要素を管理します。
keywords: microsoft、windows、ユーザーアクティビティ、iOS、iPhone、、接続デバイス、プロジェクトローマ
ms.openlocfilehash: e4cf9f078215e987c2f0e8068c4afdf640409acc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760196"
---
# <a name="class-mcduseractivityattribution"></a>講義 `MCDUserActivityAttribution`

```
@interface MCDUserActivityAttribution : NSObject
```

このクラスは、ユーザーアクティビティのグラフィカル要素を管理します。

## <a name="properties"></a>Properties

### <a name="iconuri"></a>iconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

アイコンイメージの URI。

### <a name="alternatetext"></a>alternateText
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

アイコンイメージを説明するテキスト。スクリーンリーダーで使用します。

### <a name="addimagequery"></a>addImageQuery
`@property(nonatomic, assign) BOOL addImageQuery;`

イメージを取得するときに、 **IconUri** から提供されたイメージ URI に Windows がクエリ文字列を追加できるようにするかどうかを決定します。 クエリ文字列には、ユーザーのディスプレイの DPI、ハイコントラストの設定、およびユーザーの言語に基づいて最適なイメージを選択するのに役立つ情報が含まれています。 このクエリ文字列は、スケール、コントラスト設定、および言語を指定します。たとえば、 **IconUri** 値 "www.website.com/images/hello.png" は、"www.website.com/images/hello.png? ms-scale = 100&ms-contrast = standard&ms-lang = en-us" になります。

## <a name="constructors"></a>コンストラクター

### <a name="useractivityattributionwithiconuri"></a>userActivityAttributionWithIconUri
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

アイコン URI を使用して、このクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `iconUri` 

作成されたインスタンスに属するアイコン URI の文字列値。

#### <a name="returns"></a>戻り値
アイコン uri で初期化された MCDUserActivityAttribution オブジェクトを返します。

### <a name="attributionwithiconuri"></a>attributionWithIconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

アイコン uri に対する属性を使用して、このクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `iconUri` 

作成されたインスタンスに属するアイコン URI の文字列値。

#### <a name="returns"></a>戻り値
アイコンの uri を持つ MCDUserActivityAttribution オブジェクト属性を返します。