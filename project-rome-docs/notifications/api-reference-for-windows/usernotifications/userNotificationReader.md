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
# <a name="class-usernotificationreader"></a><span data-ttu-id="b1bdb-105">クラス `UserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="b1bdb-105">class `UserNotificationReader`</span></span>

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

<span data-ttu-id="b1bdb-106">このクラスは、新しいユーザー通知の受信およびユーザーへの通知は提供します。 更新します。</span><span class="sxs-lookup"><span data-stu-id="b1bdb-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="b1bdb-107">ユーザーが接続されているデバイスのプラットフォームで永続化の通知のコレクションへのアクセスも提供します。</span><span class="sxs-lookup"><span data-stu-id="b1bdb-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="methods"></a><span data-ttu-id="b1bdb-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="b1bdb-108">Methods</span></span>

### <a name="readbatchasyncint32"></a><span data-ttu-id="b1bdb-109">ReadBatchAsync(Int32)</span><span class="sxs-lookup"><span data-stu-id="b1bdb-109">ReadBatchAsync(Int32)</span></span> 
<span data-ttu-id="b1bdb-110">受信し、アプリ サーバーによって発行されたユーザーへの通知を管理するユーザー通知のリーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b1bdb-110">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a><span data-ttu-id="b1bdb-111">イベント</span><span class="sxs-lookup"><span data-stu-id="b1bdb-111">Events</span></span>


### <a name="datachanged"></a><span data-ttu-id="b1bdb-112">DataChanged</span><span class="sxs-lookup"><span data-stu-id="b1bdb-112">DataChanged</span></span>
<span data-ttu-id="b1bdb-113">リーダーがサーバーとの同期が完了すると、新しい変更のときに発生新しい着信 UserNotifications または UserNotification 更新をアプリに通知します。</span><span class="sxs-lookup"><span data-stu-id="b1bdb-113">Raised when the reader completes sync with the server and has new change - new incoming UserNotifications or UserNotification updates to notify the app.</span></span> 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
