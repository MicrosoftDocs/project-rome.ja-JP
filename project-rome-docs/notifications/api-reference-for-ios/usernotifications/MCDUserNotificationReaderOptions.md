---
title: MCDUserNotificationReaderOptions
description: このクラスは、新しいユーザー通知と既存の通知の更新プログラムを受け取るだけなど、通知リーダーでオプションを提供するアプリを使用できます。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907984"
---
# <a name="class-mcdusernotificationreaderoptions"></a>クラス `MCDUserNotificationReaderOptions`

```
@interface MCDUserNotificationReaderOptions : NSObject
```

このクラスは、新しいユーザー通知と既存の通知の更新プログラムを受け取るだけなど、通知リーダーでオプションを提供するアプリを使用できます。 

## <a name="properties"></a>プロパティ

### <a name="startposition"></a>位置
`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` 取得または UserNotificationReaderOptions のこのインスタンスの開始位置を設定します。

### <a name="statusfilter"></a>StatusFilter
`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` 取得または作成をご希望のこのユーザー通知のリーダーの状態フィルターを設定します。

### <a name="readstatefilter"></a>ReadStateFilter
`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` 取得または設定 UserNotificationReaderOptions のこのインスタンスに設定されている読み取り状態フィルター

### <a name="useractionstatefilter"></a>userActionStateFilter
`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` Getor は、UserNotificationReaderOptions のこのインスタンスに設定されているユーザーの操作状態のフィルターを設定します。

## <a name="constructors"></a>コンストラクター

### <a name="options"></a>オプション
`+ (nullable instancetype)options;` 作成し、ユーザーへの通知のオプションの新しいインスタンスを初期化します。