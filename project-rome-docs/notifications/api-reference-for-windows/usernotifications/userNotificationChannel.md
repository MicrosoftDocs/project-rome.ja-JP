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
# <a name="class-usernotificationchannel"></a><span data-ttu-id="20861-104">クラス `UserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="20861-104">class `UserNotificationChannel`</span></span>

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

<span data-ttu-id="20861-105">このクラスは、受信と、アプリケーションのユーザー通知の管理を処理する通知の変更のリーダーを提供します。</span><span class="sxs-lookup"><span data-stu-id="20861-105">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="methods"></a><span data-ttu-id="20861-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="20861-106">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="20861-107">CreateReader()</span><span class="sxs-lookup"><span data-stu-id="20861-107">CreateReader()</span></span> 
<span data-ttu-id="20861-108">受信し、アプリ サーバーによって発行されたユーザーへの通知を管理するユーザー通知のリーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="20861-108">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a><span data-ttu-id="20861-109">CreateReader(UserNotificationReaderOptions)</span><span class="sxs-lookup"><span data-stu-id="20861-109">CreateReader(UserNotificationReaderOptions)</span></span> 
<span data-ttu-id="20861-110">オプションを持つユーザー通知のリーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="20861-110">Create a user notification reader with options</span></span> 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a><span data-ttu-id="20861-111">CreateReaderWithState(String)</span><span class="sxs-lookup"><span data-stu-id="20861-111">CreateReaderWithState(String)</span></span> 
<span data-ttu-id="20861-112">受信し、アプリ サーバーによって発行されたユーザーへの通知を管理するユーザー通知のリーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="20861-112">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="20861-113">リーダーは、指定された追跡の状態で開始されます。</span><span class="sxs-lookup"><span data-stu-id="20861-113">The reader will start at the provided tracking state.</span></span> 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a><span data-ttu-id="20861-114">GetUserNotificationAsync(String)</span><span class="sxs-lookup"><span data-stu-id="20861-114">GetUserNotificationAsync(String)</span></span>
<span data-ttu-id="20861-115">その id に基づいてユーザー通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="20861-115">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a><span data-ttu-id="20861-116">DeleteUserNotificationAsync(String)</span><span class="sxs-lookup"><span data-stu-id="20861-116">DeleteUserNotificationAsync(String)</span></span>
<span data-ttu-id="20861-117">その id に基づいてユーザー通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="20861-117">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a><span data-ttu-id="20861-118">SyncScope()</span><span class="sxs-lookup"><span data-stu-id="20861-118">SyncScope()</span></span>
<span data-ttu-id="20861-119">このユーザーの通知チャネルの同期スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="20861-119">Get the sync scope of this user notification channel.</span></span>
```C#
public static IUserDataFeedSyncScope SyncScope()
```