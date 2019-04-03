---
title: グラフの通知と Android アプリの統合
description: 通知の受信側のエンドポイントに必要な登録手順を実行する方法は、アプリケーション サーバーから発行します。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907914"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a><span data-ttu-id="0e61f-103">ハウツー ガイド:グラフの通知 (Android) との統合</span><span class="sxs-lookup"><span data-stu-id="0e61f-103">How-To Guide: Integrating with Graph Notifications (Android)</span></span>

<span data-ttu-id="0e61f-104">グラフの通知の送信し、複数のデバイスでユーザーを対象とした通知を管理するアプリを有効にします。</span><span class="sxs-lookup"><span data-stu-id="0e61f-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="0e61f-105">Android プロジェクト ローマ クライアント側 sdk では、ログインしているユーザーを対象とした、アプリ サーバーから公開通知を受信する Android アプリを登録できます。</span><span class="sxs-lookup"><span data-stu-id="0e61f-105">With the Project Rome client-side SDK on Android, your Android app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="0e61f-106">SDK では、アプリ クライアントで新しい受信の通知ペイロードが表示される、既存の通知および通知履歴の取得の状態を管理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0e61f-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="0e61f-107">通知と人間を中心とした通知の配信を有効にする方法の詳細については、次を参照してください[Microsoft Graph の通知の概要。](index.md)</span><span class="sxs-lookup"><span data-stu-id="0e61f-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="0e61f-108">Project ローマ SDK、includng グラフ通知などのすべての機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームの上に構築されます。</span><span class="sxs-lookup"><span data-stu-id="0e61f-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="0e61f-109">このガイドは、接続されているデバイス プラットフォームの使用を開始して、グラフの通知を実装する SDK の Api を使用する方法を説明するために必要な手順について説明しています-特定の機能です。</span><span class="sxs-lookup"><span data-stu-id="0e61f-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="0e61f-110">参照してください、 [API リファレンス](api-reference-for-android.md)通知シナリオに関連するリファレンス ドキュメントへのリンクについてのページ。</span><span class="sxs-lookup"><span data-stu-id="0e61f-110">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to notification scenarios.</span></span>

<span data-ttu-id="0e61f-111">この手順はからコードを参照、[プロジェクト ローマ Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-111">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="0e61f-112">グラフの通知チャネルを初期化します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-112">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="0e61f-113">プロジェクトのローマ SDK は、受信し、さまざまな種類のグラフの通知、ユーザーのアクティビティを含む – ユーザー データを管理するためにさまざまなチャネルをサブスクライブするアプリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0e61f-113">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="0e61f-114">これらはすべてストアドとで同期された**UserDataFeed**します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-114">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="0e61f-115">**UserNotification**はグラフの通知を使用して送信するユーザーを対象と通知に対応するクラスとデータ型です。</span><span class="sxs-lookup"><span data-stu-id="0e61f-115">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="0e61f-116">グラフの通知とアプリケーション サーバーによって発行された UserNotification の受信開始とを統合する必要がありますユーザー データを作成してフィードを初期化するために、 **UserNotificationChannel**します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-116">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="0e61f-117">これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e61f-117">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

<span data-ttu-id="0e61f-118">次のメソッドの初期化、 **UserNotificationChannel**します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-118">The following methods initialize a **UserNotificationChannel**.</span></span>

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
<span data-ttu-id="0e61f-119">この時点では、必要な**UserNotificationChannel**で参照`mNotificationChannel`します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-119">At this point, you should have a **UserNotificationChannel** reference in `mNotificationChannel`.</span></span>

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="0e61f-120">着信 UserNotifications を受信し、UserNotification 履歴へのアクセスの UserNotificationReader を作成します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-120">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="0e61f-121">到着最初、Google Cloud Messaging に通知を見せ以前は、アプリのクライアントのみが含まれる肩のタップと接続されているデバイス プラットフォームに完全な同期を実行する SDK をトリガーするためにそのショルダー タップ ペイロードを渡す必要がある、アプリケーション サーバーによって発行されたすべての UserNotifications を含むデバイス サーバーに接続されています。</span><span class="sxs-lookup"><span data-stu-id="0e61f-121">As we showed previously, the initial Google Cloud Messaging notification arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the UserNotifications published by your app server.</span></span> <span data-ttu-id="0e61f-122">このショルダー タップに対応するアプリケーション サーバーによって発行されたすべての通知ペイロード ダウンがプルされます (は、場合も、以前の通知発行しますが、このアプリのクライアント デバイスの接続またはその他の問題が原因で受信しない場合プルダウンも)。</span><span class="sxs-lookup"><span data-stu-id="0e61f-122">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="0e61f-123">リアルタイム同期が SDK によって実行される継続的にこれらをアプリのクライアントがこのログインしているユーザーの UserNotification データ フィードのローカル キャッシュにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0e61f-123">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s UserNotification data feed.</span></span> <span data-ttu-id="0e61f-124">この場合により、アプリ クライアントのこのデータ フィード – へのアクセス、UserNotificationReader イベントのリスナーを使用して最新の通知ペイロードを受信するか、ユーザーの通知履歴のビュー モデルとして使用できる完全な UserNotification コレクションにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="0e61f-124">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-usernotifications"></a><span data-ttu-id="0e61f-125">受信側 UserNotifications</span><span class="sxs-lookup"><span data-stu-id="0e61f-125">Receiving UserNotifications</span></span>
<span data-ttu-id="0e61f-126">まずの UserNotificationReader をインスタンス化しを有効にしようとして、エクスペリエンスの情報の使用に関心がある場合、リーダーで既に既存のすべての UserNotifications を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e61f-126">First you need to instantiate a UserNotificationReader, and get all the existing UserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="0e61f-127">常に、アプリ サーバーは既に公開通知ユーザー、ログインしているこの特定のデバイス エンドポイントにしかできない可能性がありますまたは最初のエンドポイントをユーザーにアプリがインストールされていることを想定することも安全です。</span><span class="sxs-lookup"><span data-stu-id="0e61f-127">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> 
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
<span data-ttu-id="0e61f-128">接続されているデバイスのプラットフォームが同期が完了し、新しい変更がユーザーに通知するトリガーを取得するイベント リスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-128">Now, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="0e61f-129">グラフの通知の場合、新しい変更が、新しい可能性があります、アプリのサーバー、または UserNotifcation 更新プログラムの削除によって受信 UserNotifications が発行され、有効期限の設定または他のサーバーから発生した同じユーザーがログインしてエンドポイントを登録します。でします。</span><span class="sxs-lookup"><span data-stu-id="0e61f-129">In the case of Graph Notifications, new changes could be new incoming UserNotifications published by your app server, or UserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span> 
> [!TIP] 
> <span data-ttu-id="0e61f-130">このイベント リスナーとは、主要なビジネス ロジックを処理して、シナリオに基づいた通知ペイロードのコンテンツを「使用」です。</span><span class="sxs-lookup"><span data-stu-id="0e61f-130">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="0e61f-131">現在、OS レベル通知トレイで視覚的に通知を作成するデータの Google Cloud Messaging のメッセージを使用する場合、またはアプリ内 UI を更新する通知では、コンテンツを使用する場合は、この処理にはそのためには場所です。</span><span class="sxs-lookup"><span data-stu-id="0e61f-131">If you currently use Google Cloud Messaging’s data message to construct a visual notification in the OS-level notification tray, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 
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
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="0e61f-132">既存の UserNotification の状態を更新します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-132">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="0e61f-133">前のセクションで説明した場合があります、リーダーから受信した UserNotification 変更がある、既存の UserNotification – で状態の更新済みまたはとしてマークされた既読としてマークされたされているかどうか。</span><span class="sxs-lookup"><span data-stu-id="0e61f-133">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="0e61f-134">この場合、アプリ クライアントは、ユニバーサルの有効化など、この特定のデバイスに対応するのビジュアル通知を削除することで無視することはできます。</span><span class="sxs-lookup"><span data-stu-id="0e61f-134">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="0e61f-135">バックアップ手順を実行するには、アプリのクライアントは、多くの場合、別のデバイスから始めに – この UserNotification 変更の更新を開始したされます。</span><span class="sxs-lookup"><span data-stu-id="0e61f-135">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="0e61f-136">、、UserNotifications の状態を更新する時間を選択できますが、通常、更新、そのデバイス上のユーザーにより、対応する通知が処理されます。 または、通知が有効にすると一部のアプリ内エクスペリエンスでユーザーがさらに処理されるときに.</span><span class="sxs-lookup"><span data-stu-id="0e61f-136">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="0e61f-137">次のフローがどのような例に示します。A. ユーザー A が彼の PC とアプリのクライアントがインストールされている電話の両方でこの通知を受け取るユーザーを対象とした通知をアプリケーション サーバーに発行します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-137">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="0e61f-138">ユーザーは、PC では、通知をクリックしては追跡、アプリへのハンドルに対応するタスク。</span><span class="sxs-lookup"><span data-stu-id="0e61f-138">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="0e61f-139">この PC でアプリのクライアント後、この更新プログラムをこのユーザーのすべてのデバイス間で同期するためには対応する UserNotification の状態を更新するデバイス プラットフォーム SDK の接続に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-139">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="0e61f-140">これを受信すると、他のアプリ クライアントをリアルタイムで更新プログラムの状態、されますし、対応する視覚的な警告を削除/メッセージ/デバイスの通知センターからの通知のトースト/通知トレイ アクション センター。</span><span class="sxs-lookup"><span data-stu-id="0e61f-140">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="0e61f-141">これは、通知の取得、ユーザーのデバイス間で破棄普遍的方法です。</span><span class="sxs-lookup"><span data-stu-id="0e61f-141">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="0e61f-142">UserNotification クラスは、2 種類の状態の更新プログラムを現在提供 – UserNotificationReadState、または、UserNotificationUserActionState を変更し、通知が更新されるときの動作で独自のロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="0e61f-142">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="0e61f-143">たとえばをアクティブ化済みまたは無視、UserActionState をマークすることができ、ピボット ユニバーサルを実装するには、その値を無視します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-143">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="0e61f-144">または、または同時に ReadState を読み取りまたは未読としてマークでき、その指定に基づいて、通知がアプリ内通知の履歴ビューに表示する必要がありますを決定します。</span><span class="sxs-lookup"><span data-stu-id="0e61f-144">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="0e61f-145">次のコード スニペットは、通知を破棄としての UserNotificationUserActionState をマークする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="0e61f-145">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
