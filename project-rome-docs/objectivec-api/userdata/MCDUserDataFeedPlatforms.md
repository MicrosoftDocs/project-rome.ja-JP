---
title: MCDUserDataFeedPlatforms
description: MCDUserDataFeedSyncScope の有効なプラットフォームを提供します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 7474c5896fec97a94799423ba0748bd2814d2c7a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907194"
---
# <a name="class-mcduserdatafeedplatforms"></a>クラス `MCDUserDataFeedPlatforms`

```
@interface MCDUserDataFeedPlatforms : NSObject

This class is responsible for providing the valid platform for the MCDUserDataFeedSyncScope.
```

## <a name="properties"></a>プロパティ

### <a name="all"></a>all
`@property(class, nonatomic, readonly, nonnull) NSString* all;`

プラットフォームのすべてのオブジェクト

### <a name="android"></a>Android
`@property(class, nonatomic, readonly, nonnull) NSString* android;`

Android プラットフォームのオブジェクト

### <a name="ios"></a>iOS
`@property(class, nonatomic, readonly, nonnull) NSString* iOS;`

iOS プラットフォーム オブジェクト

### <a name="windowsuwp"></a>windowsUWP
`@property(class, nonatomic, readonly, nonnull) NSString* windowsUWP;`

UWP プラットフォーム オブジェクト

### <a name="windows32"></a>windows32
`@property(class, nonatomic, readonly, nonnull) NSString* windows32;`

Windows32 プラットフォーム オブジェクト

### <a name="linux"></a>Linux
`@property(class, nonatomic, readonly, nonnull) NSString* linux;`

Linux プラットフォーム オブジェクト