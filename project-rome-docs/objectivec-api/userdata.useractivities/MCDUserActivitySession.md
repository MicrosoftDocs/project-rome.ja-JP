---
title: MCDUserActivitySession
description: このクラスは、ユーザー アクティビティの追跡 ([MCDUserActivity](MCDUserActivity.md)インスタンス)、ユーザーはそのアクティビティに関与して中にします。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 2ae85e637bb059e811a60e5bde5f33ea767c8314
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800664"
---
# <a name="class-mcduseractivitysession"></a>クラス `MCDUserActivitySession`

```
@interface MCDUserActivitySession : NSObject
```

このクラスは、指定したユーザー アクティビティのエンゲージメントを追跡します ([MCDUserActivity](MCDUserActivity.md)インスタンス)。

A [MCDUserActivity](MCDUserActivity.md)はどのくらいの期間、ユーザーが進行中でそのアクティビティを追跡する、MCDUserActivitySession 関連付けられます。 たとえば、映画を見てなど、アクティビティに複数の曜日の過程でオン-と-オフ発生します。 ユーザーは、最初の映画を見て、新しいアクティビティを起動するときに、MCDUserActivitySession を作成する必要があります。 ユーザーが別のアクティビティに切り替えたときに破棄する必要があります。 アプリが別作成、ユーザーの再開時**MCDUserActivitySession** 、元の[MCDUserActivity](MCDUserActivity.md)ユーザーがビデオを視聴している限り、アクティビティを追跡するためにします。


## <a name="properties"></a>プロパティ

### <a name="activityid"></a>ActivityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

関連付けられたこの MCDUserActivitySession MCDUserActivity の一意の ID。

## <a name="methods"></a>メソッド

### <a name="stop"></a>stop
`- (void)stop;`

このアクティビティのセッションを停止します。 これは、ユーザーが不要になったこのセッションに関連付けられたアクティビティに関与している場合に呼び出す必要があります。