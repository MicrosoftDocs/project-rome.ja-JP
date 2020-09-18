---
title: MCDUserDataFeedPlatforms
description: MCDUserDataFeedPlatforms クラスについて説明します。 このクラスは、MCDUserDataFeedSyncScope の有効なプラットフォームを提供します。
keywords: microsoft、windows、ユーザーアクティビティ、iOS、iPhone、、接続デバイス、プロジェクトローマ
ms.openlocfilehash: 0f11f695e0c9806dc43ac00e5da92f705758d73d
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760976"
---
# <a name="class-mcduserdatafeedplatforms"></a>講義 `MCDUserDataFeedPlatforms`

```
@interface MCDUserDataFeedPlatforms : NSObject

This class is responsible for providing the valid platform for the MCDUserDataFeedSyncScope.
```

## <a name="properties"></a>Properties

### <a name="all"></a>all
`@property(class, nonatomic, readonly, nonnull) NSString* all;`

すべてのプラットフォームオブジェクト

### <a name="android"></a>Android
`@property(class, nonatomic, readonly, nonnull) NSString* android;`

Android platform オブジェクト

### <a name="ios"></a>iOS
`@property(class, nonatomic, readonly, nonnull) NSString* iOS;`

iOS platform オブジェクト

### <a name="windowsuwp"></a>windowsUWP
`@property(class, nonatomic, readonly, nonnull) NSString* windowsUWP;`

UWP プラットフォームオブジェクト

### <a name="windows32"></a>windows32
`@property(class, nonatomic, readonly, nonnull) NSString* windows32;`

Windows32 platfrom.details.heap.alignedallocate オブジェクト

### <a name="linux"></a>linux
`@property(class, nonatomic, readonly, nonnull) NSString* linux;`

Linux platfrom.details.heap.alignedallocate オブジェクト