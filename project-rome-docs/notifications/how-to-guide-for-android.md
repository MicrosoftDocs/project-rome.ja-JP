---
title: Android アプリと Graph 通知の統合
description: アプリ サーバーから発行された通知の受信エンドポイントになるために必要な登録手順を実行する方法。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801204"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a><span data-ttu-id="018eb-103">使い方ガイド: Graph 通知との統合 (Android)</span><span class="sxs-lookup"><span data-stu-id="018eb-103">How-To Guide: Integrating with Graph Notifications (Android)</span></span>

<span data-ttu-id="018eb-104">Graph 通知を使用すると、アプリはユーザーをターゲットにした通知を複数のデバイスにまたがって送信および管理できます。</span><span class="sxs-lookup"><span data-stu-id="018eb-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="018eb-105">Android 上の Project Rome クライアント側 SDK によって、Android アプリは、ログイン中のユーザーをターゲットにしてアプリ サーバーから発行された通知を受信するための登録ができます。</span><span class="sxs-lookup"><span data-stu-id="018eb-105">With the Project Rome client-side SDK on Android, your Android app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="018eb-106">アプリ クライアントは SDK を使用して、新しい着信通知ペイロードを受信したり、既存の通知の状態を管理したり、通知履歴を取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="018eb-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="018eb-107">通知の詳細と、それによって人間が主体の通知配信が実現するしくみについては、[Microsoft Graph 通知の概要](index.md)に関するページを参照してください</span><span class="sxs-lookup"><span data-stu-id="018eb-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="018eb-108">Graph 通知などを含む Project Rome SDK のすべての機能は、Connected Devices Platform と呼ばれる基盤プラットフォーム上に構築されています。</span><span class="sxs-lookup"><span data-stu-id="018eb-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="018eb-109">このガイドの目的は、Connected Devices Platform を初めて使用するために必要な手順、および、Graph 通知に固有の機能を実装するために SDK で API を使用する方法について説明することです。</span><span class="sxs-lookup"><span data-stu-id="018eb-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="018eb-110">通知のシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-android.md)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="018eb-110">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to notification scenarios.</span></span>

<span data-ttu-id="018eb-111">この手順では、[Project Rome Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)のコードを参照します。</span><span class="sxs-lookup"><span data-stu-id="018eb-111">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="018eb-112">Graph 通知チャネルの初期化</span><span class="sxs-lookup"><span data-stu-id="018eb-112">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="018eb-113">Graph 通知、ユーザー アクティビティなど、さまざまな種類のユーザー データを受信および管理するために、アプリで Project Rome SDK を使用してさまざまなチャネルに登録することができます。</span><span class="sxs-lookup"><span data-stu-id="018eb-113">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="018eb-114">これらはすべて **UserDataFeed** に格納され、同期されます。</span><span class="sxs-lookup"><span data-stu-id="018eb-114">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="018eb-115">**UserNotification** は、Graph 通知を介して送信される、ユーザーをターゲットにした通知に対応するクラスおよびデータ型です。</span><span class="sxs-lookup"><span data-stu-id="018eb-115">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="018eb-116">Graph 通知と統合して、アプリ サーバーによって発行された UserNotification の受信を開始するには、まず **UserNotificationChannel** を作成してユーザー データ フィードを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="018eb-116">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="018eb-117">これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="018eb-117">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

<span data-ttu-id="018eb-118">次のメソッドは **UserNotificationChannel** を初期化します。</span><span class="sxs-lookup"><span data-stu-id="018eb-118">The following methods initialize a **UserNotificationChannel**.</span></span>

```Java
private UserNotificationChannel mNotificationChannel;
private UserDataFeed mUserDataFeed;

// ...

/**
 * Initializes the UserNotificationFeed.
 */
public void initializeUserNotificationFeed() {

    // define what scope of data this app needs
    SyncScope[] scopes = { UserNotificationChannel.getSyncScope() };

    // Get a reference to the UserDataFeed. This method is defined below
    mUserDataFeed = getUserDataFeed(scopes, new EventListener<UserDataFeed, Void>() {
        @Override
        public void onEvent(UserDataFeed userDataFeed, Void aVoid) {
            if (userDataFeed.getSyncStatus() == UserDataSyncStatus.SYNCHRONIZED) {
                // log synchronized.
            } else {
                // log synchronization not completed.
            }
        }
    });

    // this method is defined below
    mNotificationChannel = getUserNotificationChannel();
}

// instantiate the UserDataFeed
private UserDataFeed getUserDataFeed(SyncScope[] scopes, EventListener<UserDataFeed, Void> listener) {
    UserAccount[] accounts = AccountProviderBroker.getSignInHelper().getUserAccounts();
    if (accounts.length <= 0) {
        // notify the user that sign-in is required
        return null;
    }

    // use the initialized Platform instance, along with the cross-device app ID.
    UserDataFeed feed = UserDataFeed.getForAccount(accounts[0], PlatformBroker.getPlatform(), Secrets.APP_HOST_NAME);
    feed.addSyncStatusChangedListener(listener);
    feed.addSyncScopes(scopes);
    // sync data with the server
    feed.startSync();
    return feed;
}

// use the UserDataFeed reference to create a UserActivityChannel
@Nullable
private UserNotificationChannel getUserNotificationChannel() {
    UserNotificationChannel channel = null;
    try {
        // create a UserNotificationChannel for the signed in account
        channel = new UserNotificationChannel(mUserDataFeed);
    } catch (Exception e) {
        e.printStackTrace();
        // handle exception
    }
    return channel;
}
```
<span data-ttu-id="018eb-119">この時点で、**UserNotificationChannel** の参照が `mNotificationChannel` にあるはずです。</span><span class="sxs-lookup"><span data-stu-id="018eb-119">At this point, you should have a **UserNotificationChannel** reference in `mNotificationChannel`.</span></span>

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="018eb-120">UserNotificationReader を作成して着信 UserNotification を受信し UserNotification の履歴にアクセスする</span><span class="sxs-lookup"><span data-stu-id="018eb-120">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="018eb-121">前に説明したように、アプリ クライアントに到着する初期の Google Cloud Messaging 通知にはショルダー タップしか含まれておらず、そのショルダー タップ ペイロードを Connected Devices Platform に渡して、Connected Device サーバーとの完全同期を SDK に実行させる必要があります。このサーバーには、アプリ サーバーによって発行されたすべての UserNotification が格納されます。</span><span class="sxs-lookup"><span data-stu-id="018eb-121">As we showed previously, the initial Google Cloud Messaging notification arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the UserNotifications published by your app server.</span></span> <span data-ttu-id="018eb-122">これにより、アプリ サーバーによって発行され、このショルダー タップに対応している完全な通知ペイロードが取得されます (また、発行されたがデバイス接続性またはその他の問題のためこのアプリ クライアントで受信されなかった以前の通知がある場合、それらも同時に取得されます)。</span><span class="sxs-lookup"><span data-stu-id="018eb-122">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="018eb-123">これらのリアルタイム同期が継続的に SDK によって実行されるので、アプリ クライアントはこのログイン中ユーザーの UserNotification データ フィードのローカル キャッシュにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="018eb-123">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s UserNotification data feed.</span></span> <span data-ttu-id="018eb-124">この場合、アプリ クライアントは UserNotificationReader を使用してこのデータ フィードにアクセスし、イベント リスナーを介して最新の通知ペイロードを受信したり、ユーザーの通知履歴のビュー モデルとして使用できる完全な UserNotification コレクションにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="018eb-124">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-usernotifications"></a><span data-ttu-id="018eb-125">UserNotification の受信</span><span class="sxs-lookup"><span data-stu-id="018eb-125">Receiving UserNotifications</span></span>
<span data-ttu-id="018eb-126">実現しようとしているエクスペリエンスのためにその情報を利用することに関心がある場合は、まず UserNotificationReader をインスタンス化し、既にリーダーにある既存の UserNotification をすべて取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="018eb-126">First you need to instantiate a UserNotificationReader, and get all the existing UserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="018eb-127">この特定のデバイス エンドポイントが、ユーザーがアプリをインストールした唯一または最初のエンドポイントではない可能性を考えると、アプリ サーバーはこのログイン中ユーザーに通知を発行済みであると常に想定するのが安全です。</span><span class="sxs-lookup"><span data-stu-id="018eb-127">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> 
```Java
private static UserNotificationReader mReader;
private static final ArrayList<UserNotification> mHistoricalNotifications = new ArrayList<>();
// Instantiate UserNotificationReader
UserNotificationReaderOptions options = new UserNotificationReaderOptions();
mReader = mNotificationChannel.createReaderWithOptions(options);
// Read any previously published UserNotifications that have not expired yet
mReader.readBatchAsync(Long.MAX_VALUE).thenAccept(new AsyncOperation.ResultConsumer<UserNotification[]>() {
    @Override
    public void accept(UserNotification[] userNotifications) throws Throwable {
        synchronized (mHistoricalNotifications) {
            for (UserNotification notification : userNotifications) {
                if (notification.getReadState() == UserNotificationReadState.UNREAD) {
                    mHistoricalNotifications.add(notification);
                }
            }
        }
 
        if (RunnableManager.getHistoryUpdated() != null) {
            activity.runOnUiThread(RunnableManager.getHistoryUpdated());
        }
    }
});

```
<span data-ttu-id="018eb-128">ここで、Connected Devices Platform で同期が完了し、通知する新しい変更がある時点でトリガーされるイベント リスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="018eb-128">Now, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="018eb-129">Graph 通知の場合、新しい変更として可能性があるのは、アプリ サーバーによって発行された UserNotification の新規着信、または、サーバーから発生したか同じユーザーがログインした他の登録済みエンドポイントから発生した UserNotifcation の更新、削除、期限切れです。</span><span class="sxs-lookup"><span data-stu-id="018eb-129">In the case of Graph Notifications, new changes could be new incoming UserNotifications published by your app server, or UserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span> 
> [!TIP] 
> <span data-ttu-id="018eb-130">このイベント リスナーは、メインのビジネス ロジックを処理し、シナリオに基づいて通知ペイロードの内容を "消費" する場所です。</span><span class="sxs-lookup"><span data-stu-id="018eb-130">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="018eb-131">現在 Google Cloud Messaging のデータ メッセージを使用して OS レベルの通知トレイで視覚的な通知を作成している場合、または通知の内容を使用して何らかのアプリ内 UI を更新している場合、ここがそれらの処理を実行する場所です。</span><span class="sxs-lookup"><span data-stu-id="018eb-131">If you currently use Google Cloud Messaging’s data message to construct a visual notification in the OS-level notification tray, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 
```Java
mReader.addDataChangedListener(new EventListener<UserNotificationReader, Void>() {
    @Override
    public void onEvent(UserNotificationReader userNotificationReader, Void aVoid) {
        userNotificationReader.readBatchAsync(Long.MAX_VALUE).thenAccept(new AsyncOperation.ResultConsumer<UserNotification[]>() {
        @Override
        public void accept(UserNotification[] userNotifications) throws Throwable {
            boolean updatedNew = false;
            boolean updatedHistorical = false;
            synchronized (sHistoricalNotifications) {
                for (final UserNotification notification : userNotifications) {
                    if (notification.getStatus() == UserNotificationStatus.ACTIVE && notification.getReadState() == UserNotificationReadState.UNREAD) {
                        switch (notification.getUserActionState()) {
                            case NO_INTERACTION:
                                // Brand new notification
                                // Insert business logic to construct a new visual notification in Android notification tray for the user to see
                                // ...
                            case DISMISSED:
                                // Existing notification that is marked as dismissed
                                // An app client receive this type of changes because another app client logged in by the same user has marked the notification as dismissed and the change is fanned-out to everywhere
                                // This state sync across app clients on different devices enable universal dismiss of notifications and other scenarios across multiple devices owned by the same user
                                // Insert business logic to dismiss the corresponding visual notification inside Android system notification tray, to make sure users don’t have to deal with redundant information across devices, and potentially insert this notification in your app’s notification history view
                                // ...
                            default:
                                // Unexpected
                        }
                    } else {
                        // ...
                    }
                }
            }
        }
    });
}
});

```
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="018eb-132">既存の UserNotification の状態を更新する</span><span class="sxs-lookup"><span data-stu-id="018eb-132">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="018eb-133">前のセクションで説明しましたが、時として、リーダー経由で受信した UserNotification の変更は、既存の UserNotification の状態更新 (それが無視とマークされているか既読とマークされているかは問わない) である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="018eb-133">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="018eb-134">この場合アプリ クライアントは、この特定のデバイス上で対応する視覚的通知を削除することによって全体無視を有効化するなど、実行する処理を選択できます。</span><span class="sxs-lookup"><span data-stu-id="018eb-134">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="018eb-135">少し話を戻すと、多くの場合、この UserNotification の変更更新を最初に別のデバイスから開始したのはアプリ クライアントです。</span><span class="sxs-lookup"><span data-stu-id="018eb-135">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="018eb-136">UserNotification の状態を更新するタイミングは選択できますが、それは通常、対応する視覚的通知がそのデバイス上でユーザーによって処理された時点、または、有効化する何らかのアプリ内エクスペリエンスでその通知がユーザーによってさらに処理された時点です。</span><span class="sxs-lookup"><span data-stu-id="018eb-136">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="018eb-137">フローがどのようになるかの例を次に示します。アプリ サーバーはユーザー A をターゲットに通知を発行します。ユーザー A は、アプリ クライアントがインストールされている PC と電話の両方でこの通知を受信します。</span><span class="sxs-lookup"><span data-stu-id="018eb-137">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="018eb-138">ユーザーは PC で通知をクリックし、対応するタスクを処理するためにアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="018eb-138">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="018eb-139">その後、この PC 上のアプリ クライアントが Connected Devices Platform SDK を呼び出して、対応する UserNotification の状態を更新し、このユーザーのすべてのデバイス間でこの更新を同期します。</span><span class="sxs-lookup"><span data-stu-id="018eb-139">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="018eb-140">他のアプリ クライアントは、この状態更新をリアルタイムで受信すると、対応する視覚的アラート/メッセージ/トースト通知をデバイスの通知センター/通知トレイ/アクション センターから削除します。</span><span class="sxs-lookup"><span data-stu-id="018eb-140">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="018eb-141">これは、ユーザーのデバイス間で通知が全体無視されるしくみです。</span><span class="sxs-lookup"><span data-stu-id="018eb-141">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="018eb-142">UserNotification クラスは現在、2 種類の状態更新を提供します。UserNotificationReadState または UserNotificationUserActionState を変更し、通知が更新されたときに実行する処理について独自のロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="018eb-142">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="018eb-143">たとえば、UserActionState を Activated (アクティブ化) または Dismissed (無視) とマークし、その値を基準にして全体無視を実装できます。</span><span class="sxs-lookup"><span data-stu-id="018eb-143">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="018eb-144">その代わりに、または同時に、ReadState を Read (既読) または Unread (未読) とマークし、それに基づいて、どの通知をアプリ内通知の履歴ビューに表示するかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="018eb-144">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="018eb-145">次のコード スニペットは、通知の UserNotificationUserActionState を Dismissed とマークする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="018eb-145">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
