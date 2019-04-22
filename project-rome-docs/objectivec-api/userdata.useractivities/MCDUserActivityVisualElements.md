---
title: MCDUserActivityVisualElements
description: このクラスには、説明、アイコンを MCDUserActivity を"details"タイルを表示するなど、visual 情報が含まれています。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: c969b8a52bc6d2a22fd0a00808f9bb374c63cd8a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801064"
---
# <a name="class-mcduseractivityvisualelements"></a>クラス `MCDUserActivityVisualElements`

```
@interface MCDUserActivityVisualElements : NSObject 
```

このクラスには、説明、アイコンを MCDUserActivity を"details"タイルを表示するなど、visual 情報が含まれています。

## <a name="properties"></a>プロパティ

### <a name="displaytext"></a>displayText
`@property(nonatomic, copy, nonnull) NSString* displayText;`

アクティビティの詳細」のタイルの表示テキスト。

### <a name="descriptiontext"></a>descriptionText
`@property(nonatomic, copy, nullable) NSString* descriptionText;`

アクティビティの詳細」のタイルの説明テキスト。

### <a name="backgroundcolor"></a>BackgroundColor
`@property(nonatomic, copy, nullable) SKColor* backgroundColor;`

アクティビティのタイルの背景色。

### <a name="attribution"></a>属性
`@property(nonatomic, retain, nullable) MCDUserActivityAttribution* attribution;`

アクティビティに関するグラフィック情報。

### <a name="adaptivecardjson"></a>adaptiveCardJson
`@property(nonatomic, copy, nullable) NSString* adaptiveCardJson;`

アクティビティの詳細」のタイルのコンテンツのテキスト。

### <a name="attributiondisplaytext"></a>attributionDisplayText
`@property(nonatomic, copy, nullable) NSString* attributionDisplayText;`

アクティビティのカードの上部にあるバナーに表示されるテキスト。