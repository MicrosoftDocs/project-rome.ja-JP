---
title: UserNotificationReaderOptions
description: このクラスを使用すると、アプリで通知リーダーにオプションを提供できるようになります。たとえば、新しいユーザー通知を受信するだけで、既存の通知を更新することはできません。
keywords: microsoft、windows、Graph 通知、操作方法ウィンドウ
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801384"
---
# <a name="class-usernotificationreaderoptions"></a>講義`UserNotificationReaderOptions`

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

このクラスを使用すると、アプリで通知リーダーにオプションを提供できるようになります。たとえば、新しいユーザー通知を受信するだけで、既存の通知を更新することはできません。 

## <a name="constructors"></a>コンストラクター

### <a name="usernotificationreaderoptions"></a>UserNotificationReaderOptions
UserNotificationReaderOptions の新しいインスタンスを作成して初期化します。

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a>UserNotificationReaderOptions (UserNotificationReaderStartPosition、Usernotificationreaderoptions、UserNotificationReadStateFilter、UserNotificationUserActionStateFilter)
フィルターと開始位置を指定して UserNotificationReaderOptions の新しいインスタンスを作成し、初期化します。 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a>Properties

|名前 | 説明 |
|:-- |:-- |
|開始位置 |UserNotificationReaderOptions のこのインスタンスの開始位置を取得または設定します。|
|   StatusFilter |作成するユーザー通知リーダーのステータスフィルターを取得または設定します。| 
|   ReadStateFilter |UserNotificationReaderOptions のこのインスタンスに設定されている読み取り状態フィルターを取得または設定します。| 
|   UserActionStateFilter|この UserNotificationReaderOptions のインスタンスに設定されているユーザーアクション状態フィルターを getor に設定します。| 




