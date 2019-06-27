---
title: iOS アプリと Graph 通知の統合
description: アプリ サーバーから発行された通知の受信エンドポイントになるために必要な登録手順を実行する方法。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801314"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a><span data-ttu-id="006e6-103">使い方ガイド: Graph 通知との統合 (iOS)</span><span class="sxs-lookup"><span data-stu-id="006e6-103">How-To Guide: Integrating with Graph Notifications (iOS)</span></span>

<span data-ttu-id="006e6-104">Graph 通知を使用すると、アプリはユーザーをターゲットにした通知を複数のデバイスにまたがって送信および管理できます。</span><span class="sxs-lookup"><span data-stu-id="006e6-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="006e6-105">iOS 上の Project Rome クライアント側 SDK によって、iOS アプリは、ログイン中のユーザーをターゲットにしてアプリ サーバーから発行された通知を受信するための登録ができます。</span><span class="sxs-lookup"><span data-stu-id="006e6-105">With the Project Rome client-side SDK on iOS, your iOS app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="006e6-106">アプリ クライアントは SDK を使用して、新しい着信通知ペイロードを受信したり、既存の通知の状態を管理したり、通知履歴を取得したりできます。</span><span class="sxs-lookup"><span data-stu-id="006e6-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="006e6-107">通知の詳細と、それによって人間が主体の通知配信が実現するしくみについては、[Microsoft Graph 通知の概要](index.md)に関するページを参照してください</span><span class="sxs-lookup"><span data-stu-id="006e6-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="006e6-108">Graph 通知などを含む Project Rome SDK のすべての機能は、Connected Devices Platform と呼ばれる基盤プラットフォーム上に構築されています。</span><span class="sxs-lookup"><span data-stu-id="006e6-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="006e6-109">このガイドの目的は、Connected Devices Platform を初めて使用するために必要な手順、および、Graph 通知に固有の機能を実装するために SDK で API を使用する方法について説明することです。</span><span class="sxs-lookup"><span data-stu-id="006e6-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="006e6-110">この手順では、GitHub から入手できる [Project Rome iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)のコードを参照します。</span><span class="sxs-lookup"><span data-stu-id="006e6-110">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="006e6-111">通知のシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-ios/index.md)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="006e6-111">See the [API reference](api-reference-for-ios/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="006e6-112">Connected Devices Platform と通知の設定</span><span class="sxs-lookup"><span data-stu-id="006e6-112">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="006e6-113">プラットフォームの使用</span><span class="sxs-lookup"><span data-stu-id="006e6-113">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="006e6-114">Graph 通知チャネルの初期化</span><span class="sxs-lookup"><span data-stu-id="006e6-114">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="006e6-115">Graph 通知、ユーザー アクティビティなど、さまざまな種類のユーザー データを受信および管理するために、アプリで Project Rome SDK を使用してさまざまなチャネルに登録することができます。</span><span class="sxs-lookup"><span data-stu-id="006e6-115">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="006e6-116">これらはすべて **MCDUserDataFeed** に格納され、同期されます。</span><span class="sxs-lookup"><span data-stu-id="006e6-116">These are all stored and synced in **MCDUserDataFeed**.</span></span> <span data-ttu-id="006e6-117">**MCDUserNotification** は、Graph 通知を介して送信される、ユーザーをターゲットにした通知に対応するクラスおよびデータ型です。</span><span class="sxs-lookup"><span data-stu-id="006e6-117">**MCDUserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span>
<span data-ttu-id="006e6-118">Graph 通知と統合して、アプリ サーバーによって発行された MCDUserNotification の受信を開始するには、まず **MCDUserNotificationChannel** を作成してユーザー データ フィードを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="006e6-118">To integrate with Graph Notification and start receiving MCDUserNotification published by your app server, you will first need to initialize the user data feed by creating a **MCDUserNotificationChannel**.</span></span> <span data-ttu-id="006e6-119">これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="006e6-119">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span>

<span data-ttu-id="006e6-120">次のメソッドは **MCDUserNotificationChannel** を初期化します。</span><span class="sxs-lookup"><span data-stu-id="006e6-120">The following methods initialize a **MCDUserNotificationChannel**.</span></span>
```ObjectiveC
// You must be logged in to use UserNotifications
NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
if (accounts.count > 0)
{
    // Get a UserNotification channel, getting the default channel
    NSLog(@"Creating UserNotificationChannel");
    NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
    MCDUserDataFeed* userDataFeed = [MCDUserDataFeed userDataFeedForAccount:accounts[0]
        platform:[AppDataSource sharedInstance].platform
        activitySourceHost:CROSS_PLATFORM_APP_ID];
    NSArray<MCDSyncScope*>* syncScopes = @[ [MCDUserNotificationChannel syncScope] ];
    [userDataFeed addSyncScopes:syncScopes];
    self.channel = [MCDUserNotificationChannel userNotificationChannelWithUserDataFeed:userDataFeed];
}
else
{
    NSLog(@"Must log in to receive notifications for the logged in user!");
    self.createNotificationStatusField.text = @"Need to be logged in!";
}
```
<span data-ttu-id="006e6-121">この時点で、**MCDUserNotificationChannel** の参照が `channel` にあるはずです。</span><span class="sxs-lookup"><span data-stu-id="006e6-121">At this point, you should have a **MCDUserNotificationChannel** reference in `channel`.</span></span>

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a><span data-ttu-id="006e6-122">MCDUserNotificationReader を作成して着信 MCDUserNotification を受信し MCDUserNotification の履歴にアクセスする</span><span class="sxs-lookup"><span data-stu-id="006e6-122">Create a MCDUserNotificationReader to receive incoming MCDUserNotifications and access MCDUserNotification history</span></span>
<span data-ttu-id="006e6-123">前に説明したように、アプリ クライアントに到着する初期の APNS サイレント メッセージにはショルダー タップしか含まれておらず、そのショルダー タップ ペイロードを Connected Devices Platform に渡して、Connected Device サーバーとの完全同期を SDK に実行させる必要があります。このサーバーには、アプリ サーバーによって発行されたすべての MCDUserNotification が格納されます。</span><span class="sxs-lookup"><span data-stu-id="006e6-123">As we showed previously, the initial APNS silent message arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the MCDUserNotifications published by your app server.</span></span> <span data-ttu-id="006e6-124">これにより、アプリ サーバーによって発行され、このショルダー タップに対応している完全な通知ペイロードが取得されます (また、発行されたがデバイス接続性またはその他の問題のためこのアプリ クライアントで受信されなかった以前の通知がある場合、それらも同時に取得されます)。</span><span class="sxs-lookup"><span data-stu-id="006e6-124">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="006e6-125">これらのリアルタイム同期が継続的に SDK によって実行されるので、アプリ クライアントはこのログイン中ユーザーの MCDUserNotification データ フィードのローカル キャッシュにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="006e6-125">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s MCDUserNotification data feed.</span></span> <span data-ttu-id="006e6-126">この場合、アプリ クライアントは MCDUserNotificationReader を使用してこのデータ フィードにアクセスし、イベント リスナーを介して最新の通知ペイロードを受信したり、ユーザーの通知履歴のビュー モデルとして使用できる完全な MCDUserNotification コレクションにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="006e6-126">A MCDUserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full MCDUserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-mcdusernotifications"></a><span data-ttu-id="006e6-127">MCDUserNotification の受信</span><span class="sxs-lookup"><span data-stu-id="006e6-127">Receiving MCDUserNotifications</span></span>
<span data-ttu-id="006e6-128">実現しようとしているエクスペリエンスのためにその情報を利用することに関心がある場合は、まず MCDUserNotificationReader をインスタンス化し、既にリーダーにある既存の MCDUserNotification をすべて取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="006e6-128">First you need to instantiate a MCDUserNotificationReader, and get all the existing MCDUserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="006e6-129">この特定のデバイス エンドポイントが、ユーザーがアプリをインストールした唯一または最初のエンドポイントではない可能性を考えると、アプリ サーバーはこのログイン中ユーザーに通知を発行済みであると常に想定するのが安全です。</span><span class="sxs-lookup"><span data-stu-id="006e6-129">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> <span data-ttu-id="006e6-130">次に、Connected Device プラットフォームで同期が完了し、通知する新しい変更がある時点でトリガーされるイベント リスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="006e6-130">Then, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="006e6-131">Graph 通知の場合、新しい変更として可能性があるのは、アプリ サーバーによって発行された MCDUserNotification の新規着信、または、サーバーから発生したか同じユーザーがログインした他の登録済みエンドポイントから発生した MCDUserNotifcation の更新、削除、期限切れです。</span><span class="sxs-lookup"><span data-stu-id="006e6-131">In the case of Graph Notifications, new changes could be new incoming MCDUserNotifications published by your app server, or MCDUserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span>

> [!TIP] 
> <span data-ttu-id="006e6-132">このイベント リスナーは、メインのビジネス ロジックを処理し、シナリオに基づいて通知ペイロードの内容を "消費" する場所です。</span><span class="sxs-lookup"><span data-stu-id="006e6-132">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="006e6-133">現在 APNS サイレント通知を使用して OS レベルの通知センターで視覚的な通知を作成している場合、またはサイレント通知の内容を使用して何らかのアプリ内 UI を更新している場合、ここがそれらの処理を実行する場所です。</span><span class="sxs-lookup"><span data-stu-id="006e6-133">If you currently use APNS silent notification to construct a visual notification in the OS-level notification center, or if you use the content in the silent notification to update some in-app UI, this is the place to do that.</span></span> 

```ObjectiveC
// Instantiate the reader from a MCDUserNotificationChannel
// Add a data change listener to subscribe to new changes when new notifications or notification updates are received
- (void)setupWithAccount:(MCDUserAccount*)account {
    dispatch_async(dispatch_get_global_queue(QOS_CLASS_DEFAULT, 0), ^{
        @synchronized (self) {
            MCDUserDataFeed* dataFeed = [MCDUserDataFeed userDataFeedForAccount:account platform:_platform activitySourceHost:@"graphnotifications.sample.windows.com"];
            [dataFeed addSyncScopes:@[[MCDUserNotificationChannel syncScope]]];
            self.channel = [MCDUserNotificationChannel userNotificationChannelWithUserDataFeed:dataFeed];
            self.reader = [self.channel createReader];
            
            __weak typeof(self) weakSelf = self;
            _readerRegistrationToken = [self.reader addDataChangedListener:^(__unused MCDUserNotificationReader* source) {
                NSLog(@"ME123 Got a change!");
                if (weakSelf) {
                    [weakSelf forceRead];
                } else {
                    NSLog(@"ME123 WEAKSELF FOR CHANGES IS NULL!!!");
                }
            }];
            
            [self forceRead];
        }
    });
}

// this is your own business logic when the event listener is fired
// In this case, the app reads the existing batch of notifications in the store and handle any new incoming notifications or notification updates after that
- (void)forceRead {
    NSLog(@"ME123 Forced to read!");
    [self.reader readBatchAsyncWithMaxSize:NSUIntegerMax completion:^(NSArray<MCDUserNotification *> * _Nullable notifications, NSError * _Nullable error) {
        if (error) {
            NSLog(@"ME123 Failed to read batch with error %@", error);
        } else {
            [self _handleNotifications:notifications];
            NSLog(@"ME123 Have %ld listeners", self.listenerMap.count);
            for (void (^listener)(void) in self.listenerMap.allValues) {
                NSLog(@"ME123 Calling a listener about an update!");
                listener();
            }
        }
    }];
}

```

## <a name="update-the-state-of-an-existing-mcdusernotification"></a><span data-ttu-id="006e6-134">既存の MCDUserNotification の状態を更新する</span><span class="sxs-lookup"><span data-stu-id="006e6-134">Update the state of an existing MCDUserNotification</span></span>
<span data-ttu-id="006e6-135">前のセクションで説明しましたが、時として、リーダー経由で受信した MCDUserNotification の変更は、既存の MCDUserNotification の状態更新 (それが無視とマークされているか既読とマークされているかは問わない) である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="006e6-135">In the previous section, we mentioned that sometimes a MCDUserNotification change received through the reader could be a state update on an existing MCDUserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="006e6-136">この場合アプリ クライアントは、この特定のデバイス上で対応する視覚的通知を削除することによって全体無視を有効化するなど、実行する処理を選択できます。</span><span class="sxs-lookup"><span data-stu-id="006e6-136">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="006e6-137">少し話を戻すと、多くの場合、この MCDUserNotification の変更更新を最初に別のデバイスから開始したのはアプリ クライアントです。</span><span class="sxs-lookup"><span data-stu-id="006e6-137">Taking a step back, your app client is often the one that initiated this MCDUserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="006e6-138">MCDUserNotification の状態を更新するタイミングは選択できますが、それは通常、対応する視覚的通知がそのデバイス上でユーザーによって処理された時点、または、有効化する何らかのアプリ内エクスペリエンスでその通知がユーザーによってさらに処理された時点です。</span><span class="sxs-lookup"><span data-stu-id="006e6-138">You can choose the time to update the state of your MCDUserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="006e6-139">フローがどのようになるかの例を次に示します。アプリ サーバーはユーザー A をターゲットに通知を発行します。ユーザー A は、アプリ クライアントがインストールされている PC と電話の両方でこの通知を受信します。</span><span class="sxs-lookup"><span data-stu-id="006e6-139">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="006e6-140">ユーザーは PC で通知をクリックし、対応するタスクを処理するためにアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="006e6-140">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="006e6-141">その後、この PC 上のアプリ クライアントが Connected Devices Platform SDK を呼び出して、対応するユーザー通知の状態を更新し、このユーザーのすべてのデバイス間でこの更新を同期します。</span><span class="sxs-lookup"><span data-stu-id="006e6-141">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding User Notification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="006e6-142">他のアプリ クライアントは、この状態更新をリアルタイムで受信すると、対応する視覚的アラート/メッセージ/トースト通知をデバイスの通知センター/通知トレイ/アクション センターから削除します。</span><span class="sxs-lookup"><span data-stu-id="006e6-142">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="006e6-143">これは、ユーザーのデバイス間で通知が全体無視されるしくみです。</span><span class="sxs-lookup"><span data-stu-id="006e6-143">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP]
> <span data-ttu-id="006e6-144">MCDUserNotification クラスは現在、2 種類の状態更新を提供します。MCDUserNotificationReadState または MCDUserNotificationUserActionState を変更し、通知が更新されたときに実行する処理について独自のロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="006e6-144">MCDUserNotification class currently provides 2 types of state updates – you can modify the MCDUserNotificationReadState or the MCDUserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="006e6-145">たとえば、アクションの状態を Activated (アクティブ化) または Dismissed (無視) とマークし、その値を基準にして全体無視を実装できます。</span><span class="sxs-lookup"><span data-stu-id="006e6-145">For example, you can mark the action state to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="006e6-146">その代わりに、または同時に、読み取り状態を Read (既読) または Unread (未読) とマークし、それに基づいて、どの通知をアプリ内通知の履歴ビューに表示するかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="006e6-146">Alternatively, or at the same time, you can mark read state as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> 

```ObjectiveC
- (void)dismissNotification:(MCDUserNotification*)notification {
    @synchronized (self) {
        notification.userActionState = MCDUserNotificationUserActionStateDismissed;
        [notification saveAsync:^(__unused MCDUserNotificationUpdateResult * _Nullable result, __unused NSError * _Nullable err) {
            NSLog(@"ME123 Dismiss notification with result %d error %@", result.succeeded, err);
        }];
    }
}

```
