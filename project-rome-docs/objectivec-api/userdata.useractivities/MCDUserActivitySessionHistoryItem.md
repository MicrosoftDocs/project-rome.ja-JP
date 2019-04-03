---
title: MCDUserActivitySessionHistoryItem
description: このクラスは、特定の活動に従事するユーザーが開始および終了の時間を提供します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 3a480d9d0d028973554c13ee162b359502c8a772
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907404"
---
# <a name="class-mcduseractivitysessionhistoryitem"></a>クラス `MCDUserActivitySessionHistoryItem`

```
@interface MCDUserActivitySessionHistoryItem : NSObject
```

このクラスは、特定の活動に従事するユーザーが開始および終了の時間を提供します。


## <a name="properties"></a>プロパティ

### <a name="useractivity"></a>UserActivity
`@property(nonatomic, readonly, nonnull) MCDUserActivity* userActivity;`

ユーザー アクティビティの履歴がこのクラスのインスタンスを表します。

### <a name="starttime"></a>startTime
`@property(nonatomic, readonly, nonnull) NSDate* startTime;`

ユーザーの関連付けられているアクティビティで魅力的な開始時刻。

### <a name="endtime"></a>終了時刻
`@property(nonatomic, readonly, nullable) NSDate* endTime;`

ユーザーが関連付けられているアクティビティで停止したときに時間です。

### <a name="remotesystemid"></a>remoteSystemId
`@property(nonatomic, readonly, nullable) NSString* remoteSystemId;`

ユーザー デバイスのリモート システム id を示す文字列でこの活動を行っています。