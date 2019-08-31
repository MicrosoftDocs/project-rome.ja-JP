---
title: UserNotificationChannel
description: このクラスは、ユーザー通知のライフサイクルを管理します。
keywords: microsoft、windows、Graph 通知、操作方法ウィンドウ
ms.openlocfilehash: ee30f0eab2bb212dddf1de401a91f0487c512705
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801444"
---
# <a name="class-usernotificationchannel"></a>講義`UserNotificationChannel`

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