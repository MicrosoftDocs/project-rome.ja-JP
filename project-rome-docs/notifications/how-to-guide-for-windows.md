---
title: グラフの通知と UWP アプリの統合
description: 通知の受信側のエンドポイントに必要な登録手順を実行する方法は、アプリケーション サーバーから発行します。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909524"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a><span data-ttu-id="771de-103">ハウツー ガイド:MS Graph 通知 (Windows UWP) との統合</span><span class="sxs-lookup"><span data-stu-id="771de-103">How-To Guide: Integrating with MS Graph Notifications (Windows UWP)</span></span>

<span data-ttu-id="771de-104">Windows 上のグラフの通知のクライアント側 sdk では、Windows UWP アプリは、ユーザーを対象とした、アプリ サーバーから公開通知を受信する受信側のエンドポイントに必要な登録手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="771de-104">With the Graph Notifications client-side SDK on Windows, your Windows UWP app can perform the necessary registration steps to become a receiving endpoint that receives notifications published from your app server targeted at a user.</span></span> <span data-ttu-id="771de-105">SDK を使用し、ペイロードがこのクライアントに到着した新しい通知の受信通知の状態の管理、通知履歴の取得など、クライアント側で通知を管理できます。</span><span class="sxs-lookup"><span data-stu-id="771de-105">The SDK is then used to manage the notifications on the client side including receiving new notification payloads arrived on this client, managing the state of notifications, and retrieving notification history.</span></span> <span data-ttu-id="771de-106">MS Graph の通知と人間を中心とした通知の配信を有効にする方法の詳細については、次を参照してください[Microsoft Graph の通知の概要。](index.md)</span><span class="sxs-lookup"><span data-stu-id="771de-106">For more information about MS Graph Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="771de-107">参照してください、 [API リファレンス](api-reference-for-windows/index.md)通知シナリオに関連するリファレンス ドキュメントへのリンクについてのページ。</span><span class="sxs-lookup"><span data-stu-id="771de-107">See the [API reference](api-reference-for-windows/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a><span data-ttu-id="771de-108">グラフの通知を使用するには、接続されているデバイス プラットフォームにアクセスするための暫定的なセットアップ</span><span class="sxs-lookup"><span data-stu-id="771de-108">Preliminary setup for accessing the Connected Devices Platform in order to use Graph Notifications</span></span> 
<span data-ttu-id="771de-109">グラフの通知との統合を行う必要がありますをいくつかの手順します。</span><span class="sxs-lookup"><span data-stu-id="771de-109">There are a few steps you must take to integrate with Graph Notifications</span></span>
* <span data-ttu-id="771de-110">MSA または AAD アプリの登録</span><span class="sxs-lookup"><span data-stu-id="771de-110">MSA or AAD App Registration</span></span>
* <span data-ttu-id="771de-111">クロス プラットフォーム アプリ Id を提供するデベロッパー センター オンボードし、プッシュ通知の資格情報</span><span class="sxs-lookup"><span data-stu-id="771de-111">Dev Center Onboarding to Provide Cross-Platform App Identity and Push Notification Credentials</span></span>
* <span data-ttu-id="771de-112">SDK を追加して、接続されているデバイス プラットフォームの初期化</span><span class="sxs-lookup"><span data-stu-id="771de-112">Adding the SDK and Initializing the Connected Devices Platform</span></span>
* <span data-ttu-id="771de-113">通知サービスに接続されているデバイス プラットフォームを関連付ける</span><span class="sxs-lookup"><span data-stu-id="771de-113">Associate the Notification Service with Connected Devices Platform</span></span>

<span data-ttu-id="771de-114">まず、MSA または AAD アプリの登録を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="771de-114">First, you must complete the MSA and/or AAD App Registration.</span></span> <span data-ttu-id="771de-115">これが既に完了したら場合、次のセクションに進みます。</span><span class="sxs-lookup"><span data-stu-id="771de-115">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
<span data-ttu-id="771de-116">次に、する必要がありますオンボード グラフ通知の使用を含むクロス デバイス エクスペリエンスと統合するために接続されているデバイスのプラットフォームへのアクセスを取得する Microsoft Windows デベロッパー センターでします。</span><span class="sxs-lookup"><span data-stu-id="771de-116">Next, you must onboard with Microsoft Windows Dev Center to get access to the Connected Device Platform in order to integrate with cross-device experiences including use of Graph Notifications.</span></span> <span data-ttu-id="771de-117">これが既に完了したら場合、次のセクションに進みます。</span><span class="sxs-lookup"><span data-stu-id="771de-117">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
<span data-ttu-id="771de-118">次に、プロジェクトのローマ SDK をプロジェクトに追加し、接続されているデバイス プラットフォームを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="771de-118">Next, you must add the Project Rome SDK to your project and initialize the Connected Devices Platform.</span></span> <span data-ttu-id="771de-119">これが既に完了したら場合、次のセクションに進みます。</span><span class="sxs-lookup"><span data-stu-id="771de-119">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
<span data-ttu-id="771de-120">最後に、アプリをプッシュ通知の受信を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="771de-120">Lastly, you must enable your app to receive push notifications.</span></span> <span data-ttu-id="771de-121">これが既に完了したら場合、次のセクションに進みます。</span><span class="sxs-lookup"><span data-stu-id="771de-121">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="771de-122">グラフの通知チャネルを初期化します。</span><span class="sxs-lookup"><span data-stu-id="771de-122">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="771de-123">大まかに言えば、SDK によって、アプリを受信し、さまざまな種類のグラフの通知、ユーザーのアクティビティを含む – ユーザー データを管理するためにさまざまなチャネルにサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="771de-123">At a high level, the SDK allows your app to subscribe to different channels in order to receive and manage different types of User Data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="771de-124">これらはすべてストアドとで同期された**UserDataFeed**します。</span><span class="sxs-lookup"><span data-stu-id="771de-124">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="771de-125">**UserNotification**はグラフの通知を使用して送信するユーザーを対象と通知に対応するクラスとデータ型です。</span><span class="sxs-lookup"><span data-stu-id="771de-125">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="771de-126">グラフの通知とアプリケーション サーバーによって発行された UserNotification の受信開始とを統合する必要がありますユーザー データを作成してフィードを初期化するために、 **UserNotificationChannel**します。</span><span class="sxs-lookup"><span data-stu-id="771de-126">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="771de-127">これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="771de-127">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="771de-128">着信 UserNotifications を受信し、UserNotification 履歴へのアクセスの UserNotificationReader を作成します。</span><span class="sxs-lookup"><span data-stu-id="771de-128">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="771de-129">**UserNotificationChannel**必要がある、参照、 **UserNotificationReader**サーバーから実際の通知の内容をフェッチする SDK を許可するためにします。</span><span class="sxs-lookup"><span data-stu-id="771de-129">Once you have a **UserNotificationChannel** reference, you need a **UserNotificationReader** in order to allow the SDK to fetch the actual notification content from the server.</span></span> <span data-ttu-id="771de-130">この場合により、アプリ クライアントのこのデータ フィード – へのアクセス、UserNotificationReader イベントのリスナーを使用して最新の通知ペイロードを受信するか、ユーザーの通知履歴のビュー モデルとして使用できる完全な UserNotification コレクションにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="771de-130">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  

<span data-ttu-id="771de-131">次のコードは、ユーザーの通知チャネルをインスタンス化し、ユーザー通知のリーダーを作成し、ユーザー通知リーダーが接続されているデバイスのプラットフォームは、各同期が完了しへの新しい変更がトリガーされた取得のイベント ハンドラーを追加する手順を示しています。について通知します。</span><span class="sxs-lookup"><span data-stu-id="771de-131">The code below shows the steps to instantiate a user notification channel, create a user notification reader, and add an event handler on the user notification reader which gets triggered when the COnnected Device Platform completes each sync and has new changes to notify you about.</span></span> 

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

### <a name="receiving-usernotifications"></a><span data-ttu-id="771de-132">受信側 UserNotifications</span><span class="sxs-lookup"><span data-stu-id="771de-132">Receiving UserNotifications</span></span>

<span data-ttu-id="771de-133">前のセクションで、ユーザー通知のリーダーに、イベント リスナーを追加することがわかります。</span><span class="sxs-lookup"><span data-stu-id="771de-133">In the above section we see that an event listner is added to the user notification reader.</span></span> <span data-ttu-id="771de-134">すべての新しい通知と通知の更新プログラムをリーダーから読み取りをするには、このイベント リスナーを実装し、それぞれこれらの新しい変更を処理するために、独自のビジネス ロジックを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="771de-134">You should implement this event listener to read all the new notifications and notification updates from the reader, and implement your own business logic to handle each of these new changes.</span></span> 

> [!TIP] 
> <span data-ttu-id="771de-135">このイベント リスナーとは、主要なビジネス ロジックを処理して、シナリオに基づいた通知ペイロードのコンテンツを「使用」です。</span><span class="sxs-lookup"><span data-stu-id="771de-135">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="771de-136">現在、OS レベルのアクション センターのローカルのトースト通知を構築する WNS の生の通知を使用する場合、またはアプリ内 UI を更新する通知では、コンテンツを使用する場合は、この処理にはそのためには場所です。</span><span class="sxs-lookup"><span data-stu-id="771de-136">If you currently use WNS’s raw notification to construct a local toast notification in the OS-level Action Center, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 

<span data-ttu-id="771de-137">次のコードは、アクティブ、および通知が削除された場合、アプリ内のビューに対応する通知の UI が削除されるすべての着信 UserNotification のローカルのトースト通知を発生させるサンプル アプリを選択する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="771de-137">The code below shows you how the sample app chooses to raise a local toast notification for all the incoming UserNotification that are Active, and remove the corresponding notification UI in the in-app view if a notification is deleted.</span></span> 

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
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="771de-138">既存の UserNotification の状態を更新します。</span><span class="sxs-lookup"><span data-stu-id="771de-138">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="771de-139">前のセクションで説明した場合があります、リーダーから受信した UserNotification 変更がある、既存の UserNotification – で状態の更新済みまたはとしてマークされた既読としてマークされたされているかどうか。</span><span class="sxs-lookup"><span data-stu-id="771de-139">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="771de-140">この場合、アプリ クライアントは、ユニバーサルの有効化など、この特定のデバイスに対応するのビジュアル通知を削除することで無視することはできます。</span><span class="sxs-lookup"><span data-stu-id="771de-140">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="771de-141">バックアップ手順を実行するには、アプリのクライアントは、多くの場合、別のデバイスから始めに – この UserNotification 変更の更新を開始したされます。</span><span class="sxs-lookup"><span data-stu-id="771de-141">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="771de-142">、、UserNotifications の状態を更新する時間を選択できますが、通常、更新、そのデバイス上のユーザーにより、対応する通知が処理されます。 または、通知が有効にすると一部のアプリ内エクスペリエンスでユーザーがさらに処理されるときに.</span><span class="sxs-lookup"><span data-stu-id="771de-142">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="771de-143">次のフローがどのような例に示します。A. ユーザー A が彼の PC とアプリのクライアントがインストールされている電話の両方でこの通知を受け取るユーザーを対象とした通知をアプリケーション サーバーに発行します。</span><span class="sxs-lookup"><span data-stu-id="771de-143">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="771de-144">ユーザーは、PC では、通知をクリックしては追跡、アプリへのハンドルに対応するタスク。</span><span class="sxs-lookup"><span data-stu-id="771de-144">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="771de-145">この PC でアプリのクライアント後、この更新プログラムをこのユーザーのすべてのデバイス間で同期するためには対応する UserNotification の状態を更新するデバイス プラットフォーム SDK の接続に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="771de-145">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="771de-146">これを受信すると、他のアプリ クライアントをリアルタイムで更新プログラムの状態、されますし、対応する視覚的な警告を削除/メッセージ/デバイスの通知センターからの通知のトースト/通知トレイ アクション センター。</span><span class="sxs-lookup"><span data-stu-id="771de-146">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="771de-147">これは、通知の取得、ユーザーのデバイス間で破棄普遍的方法です。</span><span class="sxs-lookup"><span data-stu-id="771de-147">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="771de-148">UserNotification クラスは、2 種類の状態の更新プログラムを現在提供 – UserNotificationReadState、または、UserNotificationUserActionState を変更し、通知が更新されるときの動作で独自のロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="771de-148">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="771de-149">たとえばをアクティブ化済みまたは無視、UserActionState をマークすることができ、ピボット ユニバーサルを実装するには、その値を無視します。</span><span class="sxs-lookup"><span data-stu-id="771de-149">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="771de-150">または、または同時に ReadState を読み取りまたは未読としてマークでき、その指定に基づいて、通知がアプリ内通知の履歴ビューに表示する必要がありますを決定します。</span><span class="sxs-lookup"><span data-stu-id="771de-150">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="771de-151">次のコード スニペットは、通知を破棄としての UserNotificationUserActionState をマークする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="771de-151">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

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
