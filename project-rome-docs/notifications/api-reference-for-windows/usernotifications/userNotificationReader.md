---
title: UserNotificationReader
description: このクラスは、新しいユーザー通知の受信およびユーザーへの通知は提供します。 更新します。 ユーザーが接続されているデバイスのプラットフォームで永続化の通知のコレクションへのアクセスも提供します。
keywords: microsoft、windows、ユーザー通知では、windows に関する「方法」
ms.openlocfilehash: 3a929939be7e2dd9ecd9db65322efadaea3013d5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907374"
---
# <a name="class-usernotificationreader"></a>クラス `UserNotificationReader`

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

このクラスは、新しいユーザー通知の受信およびユーザーへの通知は提供します。 更新します。 ユーザーが接続されているデバイスのプラットフォームで永続化の通知のコレクションへのアクセスも提供します。  

## <a name="methods"></a>メソッド

### <a name="readbatchasyncint32"></a>ReadBatchAsync(Int32) 
受信し、アプリ サーバーによって発行されたユーザーへの通知を管理するユーザー通知のリーダーを作成します。
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a>イベント


### <a name="datachanged"></a>DataChanged
リーダーがサーバーとの同期が完了すると、新しい変更のときに発生新しい着信 UserNotifications または UserNotification 更新をアプリに通知します。 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
