---
title: UserNotificationReaderOptions
description: このクラスは、新しいユーザー通知と既存の通知の更新プログラムを受け取るだけなど、通知リーダーでオプションを提供するアプリを使用できます。
keywords: microsoft、windows、グラフの通知、Windows の操作方法
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909684"
---
# <a name="class-usernotificationreaderoptions"></a>クラス `UserNotificationReaderOptions`

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

このクラスは、新しいユーザー通知と既存の通知の更新プログラムを受け取るだけなど、通知リーダーでオプションを提供するアプリを使用できます。 

## <a name="constructors"></a>コンストラクター

### <a name="usernotificationreaderoptions"></a>UserNotificationReaderOptions
作成し、UserNotificationReaderOptions の新しいインスタンスを初期化します。

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a>UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)
作成し、開始位置が指定されたフィルターと UserNotificationReaderOptions の新しいインスタンスを初期化します。 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a>プロパティ

|名前 | 説明 |
|:-- |:-- |
|位置 |取得または UserNotificationReaderOptions のこのインスタンスの開始位置を設定します。|
|   StatusFilter |取得または作成をご希望のこのユーザー通知のリーダーの状態フィルターを設定します。| 
|   ReadStateFilter |取得または UserNotificationReaderOptions のこのインスタンスに設定されている読み取り状態フィルターを設定します。| 
|   UserActionStateFilter|Getor は、UserNotificationReaderOptions のこのインスタンスに設定されているユーザーの操作状態のフィルターを設定します。| 




