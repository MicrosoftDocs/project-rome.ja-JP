---
title: MCDUserNotificationReaderOptions
description: このクラスを使用すると、アプリで通知リーダーにオプションを提供できるようになります。たとえば、新しいユーザー通知を受信するだけで、既存の通知を更新することはできません。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907984"
---
# <a name="class-mcdusernotificationreaderoptions"></a>講義`MCDUserNotificationReaderOptions`

```
@interface MCDUserNotificationReaderOptions : NSObject
```

このクラスを使用すると、アプリで通知リーダーにオプションを提供できるようになります。たとえば、新しいユーザー通知を受信するだけで、既存の通知を更新することはできません。 

## <a name="properties"></a>Properties

### <a name="startposition"></a>開始位置
`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;`UserNotificationReaderOptions のこのインスタンスの開始位置を取得または設定します。

### <a name="statusfilter"></a>statusFilter
`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;`作成するユーザー通知リーダーのステータスフィルターを取得または設定します。

### <a name="readstatefilter"></a>readStateFilter
`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;`UserNotificationReaderOptions のこのインスタンスに設定されている読み取り状態フィルターを取得または設定します。

### <a name="useractionstatefilter"></a>userActionStateFilter
`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;`この UserNotificationReaderOptions のインスタンスに設定されているユーザーアクション状態フィルターを getor に設定します。

## <a name="constructors"></a>コンストラクター

### <a name="options"></a>options
`+ (nullable instancetype)options;`ユーザー通知のオプションの新しいインスタンスを作成して初期化します。