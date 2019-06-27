---
title: UWP アプリと Graph 通知の統合
description: アプリ サーバーから発行された通知の受信エンドポイントになるために必要な登録手順を実行する方法。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801304"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a><span data-ttu-id="16813-103">使い方ガイド: MS Graph 通知との統合 (Windows UWP)</span><span class="sxs-lookup"><span data-stu-id="16813-103">How-To Guide: Integrating with MS Graph Notifications (Windows UWP)</span></span>

<span data-ttu-id="16813-104">Windows の Graph 通知クライアント側 SDK を使用すると、Windows UWP アプリは、必要な登録手順を実行して、ユーザーをターゲットにしてアプリ サーバーから発行された通知を受信する受信エンドポイントになることができます。</span><span class="sxs-lookup"><span data-stu-id="16813-104">With the Graph Notifications client-side SDK on Windows, your Windows UWP app can perform the necessary registration steps to become a receiving endpoint that receives notifications published from your app server targeted at a user.</span></span> <span data-ttu-id="16813-105">その後は、このクライアントに到着した新しい通知ペイロードの受信、通知の状態の管理、通知履歴の取得など、クライアント側で通知を管理するためにこの SDK を使用します。</span><span class="sxs-lookup"><span data-stu-id="16813-105">The SDK is then used to manage the notifications on the client side including receiving new notification payloads arrived on this client, managing the state of notifications, and retrieving notification history.</span></span> <span data-ttu-id="16813-106">MS Graph 通知の詳細と、それによって人間が主体の通知配信が実現するしくみについては、[Microsoft Graph 通知の概要](index.md)に関するページを参照してください</span><span class="sxs-lookup"><span data-stu-id="16813-106">For more information about MS Graph Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="16813-107">通知のシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-windows/index.md)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="16813-107">See the [API reference](api-reference-for-windows/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a><span data-ttu-id="16813-108">Connected Devices Platform にアクセスして Graph 通知を使用するための準備段階のセットアップ</span><span class="sxs-lookup"><span data-stu-id="16813-108">Preliminary setup for accessing the Connected Devices Platform in order to use Graph Notifications</span></span> 
<span data-ttu-id="16813-109">Graph 通知と統合するために、いくつかの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16813-109">There are a few steps you must take to integrate with Graph Notifications</span></span>
* <span data-ttu-id="16813-110">MSA または AAD アプリ登録</span><span class="sxs-lookup"><span data-stu-id="16813-110">MSA or AAD App Registration</span></span>
* <span data-ttu-id="16813-111">クロスプラットフォームのアプリ ID とプッシュ通知資格情報を提供するためのデベロッパー センターでのオンボーディング</span><span class="sxs-lookup"><span data-stu-id="16813-111">Dev Center Onboarding to Provide Cross-Platform App Identity and Push Notification Credentials</span></span>
* <span data-ttu-id="16813-112">SDK の追加と Connected Devices Platform の初期化</span><span class="sxs-lookup"><span data-stu-id="16813-112">Adding the SDK and Initializing the Connected Devices Platform</span></span>
* <span data-ttu-id="16813-113">通知サービスと Connected Devices Platform の関連付け</span><span class="sxs-lookup"><span data-stu-id="16813-113">Associate the Notification Service with Connected Devices Platform</span></span>

<span data-ttu-id="16813-114">まず、MSA/AAD アプリ登録を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16813-114">First, you must complete the MSA and/or AAD App Registration.</span></span> <span data-ttu-id="16813-115">これが既に完了している場合、次のセクションに進みます。</span><span class="sxs-lookup"><span data-stu-id="16813-115">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
<span data-ttu-id="16813-116">次に、Graph 通知の使用などのクロスデバイス エクスペリエンスと統合するために、Microsoft Windows デベロッパー センターでオンボーディングを行い、Connected Device Platform にアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="16813-116">Next, you must onboard with Microsoft Windows Dev Center to get access to the Connected Device Platform in order to integrate with cross-device experiences including use of Graph Notifications.</span></span> <span data-ttu-id="16813-117">これが既に完了している場合、次のセクションに進みます。</span><span class="sxs-lookup"><span data-stu-id="16813-117">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
<span data-ttu-id="16813-118">次に、Project Rome SDK をプロジェクトに追加して、Connected Devices Platform を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16813-118">Next, you must add the Project Rome SDK to your project and initialize the Connected Devices Platform.</span></span> <span data-ttu-id="16813-119">これが既に完了している場合、次のセクションに進みます。</span><span class="sxs-lookup"><span data-stu-id="16813-119">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
<span data-ttu-id="16813-120">最後に、アプリでのプッシュ通知の受信を有効化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16813-120">Lastly, you must enable your app to receive push notifications.</span></span> <span data-ttu-id="16813-121">これが既に完了している場合、次のセクションに進みます。</span><span class="sxs-lookup"><span data-stu-id="16813-121">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="16813-122">Graph 通知チャネルの初期化</span><span class="sxs-lookup"><span data-stu-id="16813-122">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="16813-123">大まかに言えば、Graph 通知、ユーザー アクティビティなど、さまざまな種類のユーザー データを受信および管理するために、アプリで SDK を使用してさまざまなチャネルに登録することができます。</span><span class="sxs-lookup"><span data-stu-id="16813-123">At a high level, the SDK allows your app to subscribe to different channels in order to receive and manage different types of User Data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="16813-124">これらはすべて **UserDataFeed** に格納され、同期されます。</span><span class="sxs-lookup"><span data-stu-id="16813-124">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="16813-125">**UserNotification** は、Graph 通知を介して送信される、ユーザーをターゲットにした通知に対応するクラスおよびデータ型です。</span><span class="sxs-lookup"><span data-stu-id="16813-125">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="16813-126">Graph 通知と統合して、アプリ サーバーによって発行された UserNotification の受信を開始するには、まず **UserNotificationChannel** を作成してユーザー データ フィードを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16813-126">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="16813-127">これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="16813-127">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="16813-128">UserNotificationReader を作成して着信 UserNotification を受信し UserNotification の履歴にアクセスする</span><span class="sxs-lookup"><span data-stu-id="16813-128">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="16813-129">**UserNotificationChannel** の参照を取得したら、SDK で実際の通知内容をサーバーから取得できるようにするために **UserNotificationReader** が必要です。</span><span class="sxs-lookup"><span data-stu-id="16813-129">Once you have a **UserNotificationChannel** reference, you need a **UserNotificationReader** in order to allow the SDK to fetch the actual notification content from the server.</span></span> <span data-ttu-id="16813-130">この場合、アプリ クライアントは UserNotificationReader を使用してこのデータ フィードにアクセスし、イベント リスナーを介して最新の通知ペイロードを受信したり、ユーザーの通知履歴のビュー モデルとして使用できる完全な UserNotification コレクションにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="16813-130">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  

<span data-ttu-id="16813-131">次のコードは、ユーザー通知チャネルをインスタンス化し、ユーザー通知リーダーを作成し、イベント ハンドラーをユーザー通知リーダーに追加する手順を示しています。このイベント ハンドラーは、Connected Device Platform が毎回の同期を完了し、通知が必要な新しい変更があるときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="16813-131">The code below shows the steps to instantiate a user notification channel, create a user notification reader, and add an event handler on the user notification reader which gets triggered when the COnnected Device Platform completes each sync and has new changes to notify you about.</span></span> 

```C#

public async Task SetupChannel()
{
    var account = m_accoutProvider.SignedInAccount;

    if (m_feed == null)
    {
        await Task.Run(() =>
        {
            lock (this)
            {
                if (m_feed == null)
                {
                    m_platform = new ConnectedDevicesPlatform(m_accoutProvider, this);

                    Logger.Instance.LogMessage($"Create feed for {account.Id} {account.Type}");
                    m_feed = new UserDataFeed(account, m_platform, "graphnotifications.sample.windows.com");
                    m_feed.SyncStatusChanged += Feed_SyncStatusChanged;
                    m_feed.AddSyncScopes(new List<IUserDataFeedSyncScope>
                    {
                        UserNotificationChannel.SyncScope
                    });

                    m_channel = new UserNotificationChannel(m_feed);
                    m_reader = m_channel.CreateReader();
                    m_reader.DataChanged += Reader_DataChanged;
                }
            }
        });
    }
}

```

### <a name="receiving-usernotifications"></a><span data-ttu-id="16813-132">UserNotification の受信</span><span class="sxs-lookup"><span data-stu-id="16813-132">Receiving UserNotifications</span></span>

<span data-ttu-id="16813-133">前のセクションで、イベント リスナーをユーザー通知リーダーに追加しています。</span><span class="sxs-lookup"><span data-stu-id="16813-133">In the above section we see that an event listner is added to the user notification reader.</span></span> <span data-ttu-id="16813-134">すべての新しい通知と通知の更新をリーダーから読み取るために、このイベント リスナーを実装する必要があります。また、これらの新しい変更を個々に処理する独自のビジネス ロジックを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="16813-134">You should implement this event listener to read all the new notifications and notification updates from the reader, and implement your own business logic to handle each of these new changes.</span></span> 

> [!TIP] 
> <span data-ttu-id="16813-135">このイベント リスナーは、メインのビジネス ロジックを処理し、シナリオに基づいて通知ペイロードの内容を "消費" する場所です。</span><span class="sxs-lookup"><span data-stu-id="16813-135">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="16813-136">現在 WNS の直接通知を使用して OS レベルのアクション センターでローカル トースト通知を作成している場合、または通知の内容を使用して何らかのアプリ内 UI を更新している場合、ここがそれらの処理を実行する場所です。</span><span class="sxs-lookup"><span data-stu-id="16813-136">If you currently use WNS’s raw notification to construct a local toast notification in the OS-level Action Center, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 

<span data-ttu-id="16813-137">次のコードは、サンプル アプリにおいて、アクティブであるすべての着信 UserNotification に対してローカル トースト通知を発生させる方法、また、通知が削除された場合に、それに対応する通知 UI をアプリ内ビューから削除する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="16813-137">The code below shows you how the sample app chooses to raise a local toast notification for all the incoming UserNotification that are Active, and remove the corresponding notification UI in the in-app view if a notification is deleted.</span></span> 

```C#

private void Reader_DataChanged(UserNotificationReader sender, object args)
{
    ReadNotifications(sender, true);
}

private async void ReadNotifications(UserNotificationReader reader, bool showToast)
{
    var notifications = await reader.ReadBatchAsync(UInt32.MaxValue);

    foreach (var notification in notifications)
    {

        if (notification.Status == UserNotificationStatus.Active)
        {
            m_newNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            if (notification.UserActionState == UserNotificationUserActionState.NoInteraction)
            {
                // new notification, show this to user using the Windows local toast notification APIs
                m_newNotifications.Add(notification);
                if (!string.IsNullOrEmpty(notification.Content) && showToast)
                {
                    ShowToastNotification(BuildToastNotification(notification.Id, notification.Content));
                }
            }

            m_historicalNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            m_historicalNotifications.Insert(0, notification);
        }
        else
        {
            // Existing notification is marked as deleted, remove from display
            m_newNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            m_historicalNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            RemoveToastNotification(notification.Id);
        }
    }
}

```
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="16813-138">既存の UserNotification の状態を更新する</span><span class="sxs-lookup"><span data-stu-id="16813-138">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="16813-139">前のセクションで説明しましたが、時として、リーダー経由で受信した UserNotification の変更は、既存の UserNotification の状態更新 (それが無視とマークされているか既読とマークされているかは問わない) である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16813-139">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="16813-140">この場合アプリ クライアントは、この特定のデバイス上で対応する視覚的通知を削除することによって全体無視を有効化するなど、実行する処理を選択できます。</span><span class="sxs-lookup"><span data-stu-id="16813-140">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="16813-141">少し話を戻すと、多くの場合、この UserNotification の変更更新を最初に別のデバイスから開始したのはアプリ クライアントです。</span><span class="sxs-lookup"><span data-stu-id="16813-141">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="16813-142">UserNotification の状態を更新するタイミングは選択できますが、それは通常、対応する視覚的通知がそのデバイス上でユーザーによって処理された時点、または、有効化する何らかのアプリ内エクスペリエンスでその通知がユーザーによってさらに処理された時点です。</span><span class="sxs-lookup"><span data-stu-id="16813-142">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="16813-143">フローがどのようになるかの例を次に示します。アプリ サーバーはユーザー A をターゲットに通知を発行します。ユーザー A は、アプリ クライアントがインストールされている PC と電話の両方でこの通知を受信します。</span><span class="sxs-lookup"><span data-stu-id="16813-143">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="16813-144">ユーザーは PC で通知をクリックし、対応するタスクを処理するためにアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="16813-144">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="16813-145">その後、この PC 上のアプリ クライアントが Connected Devices Platform SDK を呼び出して、対応する UserNotification の状態を更新し、このユーザーのすべてのデバイス間でこの更新を同期します。</span><span class="sxs-lookup"><span data-stu-id="16813-145">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="16813-146">他のアプリ クライアントは、この状態更新をリアルタイムで受信すると、対応する視覚的アラート/メッセージ/トースト通知をデバイスの通知センター/通知トレイ/アクション センターから削除します。</span><span class="sxs-lookup"><span data-stu-id="16813-146">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="16813-147">これは、ユーザーのデバイス間で通知が全体無視されるしくみです。</span><span class="sxs-lookup"><span data-stu-id="16813-147">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="16813-148">UserNotification クラスは現在、2 種類の状態更新を提供します。UserNotificationReadState または UserNotificationUserActionState を変更し、通知が更新されたときに実行する処理について独自のロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="16813-148">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="16813-149">たとえば、UserActionState を Activated (アクティブ化) または Dismissed (無視) とマークし、その値を基準にして全体無視を実装できます。</span><span class="sxs-lookup"><span data-stu-id="16813-149">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="16813-150">その代わりに、または同時に、ReadState を Read (既読) または Unread (未読) とマークし、それに基づいて、どの通知をアプリ内通知の履歴ビューに表示するかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="16813-150">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="16813-151">次のコード スニペットは、通知の UserNotificationUserActionState を Dismissed とマークする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="16813-151">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

```C#
public async void Dismiss(string id)
{
    var notification = m_newNotifications.Find((n) => { return (n.Id == id); });
    if (notification != null)
    {
        notification.UserActionState = UserNotificationUserActionState.Dismissed;
        await notification.SaveAsync();
    }
}

```
