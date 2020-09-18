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
# <a name="class-usernotificationchannel"></a><span data-ttu-id="802d9-105">講義 `UserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="802d9-105">class `UserNotificationChannel`</span></span>

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

<span data-ttu-id="802d9-106">このクラスは、アプリケーションのユーザー通知の受信と管理を処理する通知変更リーダーを提供します。</span><span class="sxs-lookup"><span data-stu-id="802d9-106">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="methods"></a><span data-ttu-id="802d9-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="802d9-107">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="802d9-108">CreateReader ()</span><span class="sxs-lookup"><span data-stu-id="802d9-108">CreateReader()</span></span> 
<span data-ttu-id="802d9-109">アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="802d9-109">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a><span data-ttu-id="802d9-110">CreateReader (UserNotificationReaderOptions)</span><span class="sxs-lookup"><span data-stu-id="802d9-110">CreateReader(UserNotificationReaderOptions)</span></span> 
<span data-ttu-id="802d9-111">オプションを使用してユーザー通知リーダーを作成する</span><span class="sxs-lookup"><span data-stu-id="802d9-111">Create a user notification reader with options</span></span> 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a><span data-ttu-id="802d9-112">CreateReaderWithState (文字列)</span><span class="sxs-lookup"><span data-stu-id="802d9-112">CreateReaderWithState(String)</span></span> 
<span data-ttu-id="802d9-113">アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="802d9-113">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="802d9-114">リーダーは、指定された追跡状態から開始されます。</span><span class="sxs-lookup"><span data-stu-id="802d9-114">The reader will start at the provided tracking state.</span></span> 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a><span data-ttu-id="802d9-115">GetUserNotificationAsync (文字列)</span><span class="sxs-lookup"><span data-stu-id="802d9-115">GetUserNotificationAsync(String)</span></span>
<span data-ttu-id="802d9-116">Id に基づいてユーザーの通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="802d9-116">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a><span data-ttu-id="802d9-117">DeleteUserNotificationAsync (String)</span><span class="sxs-lookup"><span data-stu-id="802d9-117">DeleteUserNotificationAsync(String)</span></span>
<span data-ttu-id="802d9-118">Id に基づいてユーザーの通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="802d9-118">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a><span data-ttu-id="802d9-119">SyncScope ()</span><span class="sxs-lookup"><span data-stu-id="802d9-119">SyncScope()</span></span>
<span data-ttu-id="802d9-120">このユーザー通知チャネルの同期スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="802d9-120">Get the sync scope of this user notification channel.</span></span>
```C#
public static IUserDataFeedSyncScope SyncScope()
```