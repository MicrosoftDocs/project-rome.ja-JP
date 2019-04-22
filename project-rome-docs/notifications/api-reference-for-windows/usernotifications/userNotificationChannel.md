---
title: UserNotificationChannel
description: このクラスは、ユーザー通知のライフ サイクルを管理します。
keywords: microsoft、windows、グラフの通知、Windows の操作方法
ms.openlocfilehash: ee30f0eab2bb212dddf1de401a91f0487c512705
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801444"
---
# <a name="class-usernotificationchannel"></a>クラス `UserNotificationChannel`

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

このクラスは、受信と、アプリケーションのユーザー通知の管理を処理する通知の変更のリーダーを提供します。 

## <a name="methods"></a>メソッド

### <a name="createreader"></a>CreateReader() 
受信し、アプリ サーバーによって発行されたユーザーへの通知を管理するユーザー通知のリーダーを作成します。
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a>CreateReader(UserNotificationReaderOptions) 
オプションを持つユーザー通知のリーダーを作成します。 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a>CreateReaderWithState(String) 
受信し、アプリ サーバーによって発行されたユーザーへの通知を管理するユーザー通知のリーダーを作成します。 リーダーは、指定された追跡の状態で開始されます。 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a>GetUserNotificationAsync(String)
その id に基づいてユーザー通知を受け取ります。 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a>DeleteUserNotificationAsync(String)
その id に基づいてユーザー通知を受け取ります。 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a>SyncScope()
このユーザーの通知チャネルの同期スコープを取得します。
```C#
public static IUserDataFeedSyncScope SyncScope()
```