---
title: UserNotificationChannel
description: UserNotificationChannel クラスについて説明します。 このクラスは、ユーザー通知のライフサイクルを管理します。
keywords: microsoft、windows、Graph 通知、操作方法ウィンドウ
ms.openlocfilehash: f5347878da2d82035db1dbb63cca015180f66a34
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760936"
---
# <a name="class-usernotificationchannel"></a>講義 `UserNotificationChannel`

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

このクラスは、アプリケーションのユーザー通知の受信と管理を処理する通知変更リーダーを提供します。 

## <a name="methods"></a>メソッド

### <a name="createreader"></a>CreateReader () 
アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a>CreateReader (UserNotificationReaderOptions) 
オプションを使用してユーザー通知リーダーを作成する 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a>CreateReaderWithState (文字列) 
アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。 リーダーは、指定された追跡状態から開始されます。 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a>GetUserNotificationAsync (文字列)
Id に基づいてユーザーの通知を受け取ります。 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a>DeleteUserNotificationAsync (String)
Id に基づいてユーザーの通知を受け取ります。 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a>SyncScope ()
このユーザー通知チャネルの同期スコープを取得します。
```C#
public static IUserDataFeedSyncScope SyncScope()
```