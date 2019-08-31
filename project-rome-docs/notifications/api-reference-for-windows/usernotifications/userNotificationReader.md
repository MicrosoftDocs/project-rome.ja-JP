---
title: UserNotificationReader
description: このクラスは、新しい受信ユーザー通知とユーザー通知の更新を提供します。 また、接続されているデバイスプラットフォームに保持されているユーザー通知のコレクションにアクセスすることもできます。
keywords: microsoft、windows、ユーザー通知、操作方法ウィンドウ
ms.openlocfilehash: 3a929939be7e2dd9ecd9db65322efadaea3013d5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801424"
---
# <a name="class-usernotificationreader"></a>講義`UserNotificationReader`

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

このクラスは、新しい受信ユーザー通知とユーザー通知の更新を提供します。 また、接続されているデバイスプラットフォームに保持されているユーザー通知のコレクションにアクセスすることもできます。  

## <a name="methods"></a>メソッド

### <a name="readbatchasyncint32"></a>ReadBatchAsync (Int32) 
アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a>イベント


### <a name="datachanged"></a>DataChanged
リーダーがサーバーとの同期を完了し、新しい変更-新しい受信 Usernotifications または Usernotifications の更新プログラムによってアプリに通知されるときに発生します。 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
