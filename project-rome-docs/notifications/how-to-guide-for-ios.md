---
title: グラフの通知を IOs アプリの統合
description: 通知の受信側のエンドポイントに必要な登録手順を実行する方法は、アプリケーション サーバーから発行します。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909624"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a><span data-ttu-id="e4348-103">ハウツー ガイド:グラフの通知 (iOS) との統合</span><span class="sxs-lookup"><span data-stu-id="e4348-103">How-To Guide: Integrating with Graph Notifications (iOS)</span></span>

<span data-ttu-id="e4348-104">グラフの通知の送信し、複数のデバイスでユーザーを対象とした通知を管理するアプリを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e4348-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="e4348-105">Ios プロジェクト ローマ クライアント側 sdk では、ログインしているユーザーを対象とした、アプリ サーバーから公開通知を受信する iOS アプリを登録できます。</span><span class="sxs-lookup"><span data-stu-id="e4348-105">With the Project Rome client-side SDK on iOS, your iOS app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="e4348-106">SDK では、アプリ クライアントで新しい受信の通知ペイロードが表示される、既存の通知および通知履歴の取得の状態を管理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e4348-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="e4348-107">通知と人間を中心とした通知の配信を有効にする方法の詳細については、次を参照してください[Microsoft Graph の通知の概要。](index.md)</span><span class="sxs-lookup"><span data-stu-id="e4348-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="e4348-108">Project ローマ SDK、includng グラフ通知などのすべての機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームの上に構築されます。</span><span class="sxs-lookup"><span data-stu-id="e4348-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="e4348-109">このガイドは、接続されているデバイス プラットフォームの使用を開始して、グラフの通知を実装する SDK の Api を使用する方法を説明するために必要な手順について説明しています-特定の機能です。</span><span class="sxs-lookup"><span data-stu-id="e4348-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="e4348-110">この手順はからコードを参照、[プロジェクト ローマ iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)GitHub に用意されています。</span><span class="sxs-lookup"><span data-stu-id="e4348-110">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="e4348-111">参照してください、 [API リファレンス](api-reference-for-ios/index.md)通知シナリオに関連するリファレンス ドキュメントへのリンクについてのページ。</span><span class="sxs-lookup"><span data-stu-id="e4348-111">See the [API reference](api-reference-for-ios/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="e4348-112">接続されているデバイス プラットフォームと通知を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4348-112">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="e4348-113">プラットフォームを使用します。</span><span class="sxs-lookup"><span data-stu-id="e4348-113">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="e4348-114">グラフの通知チャネルを初期化します。</span><span class="sxs-lookup"><span data-stu-id="e4348-114">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="e4348-115">プロジェクトのローマ SDK は、受信し、さまざまな種類のグラフの通知、ユーザーのアクティビティを含む – ユーザー データを管理するためにさまざまなチャネルをサブスクライブするアプリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e4348-115">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="e4348-116">これらはすべてストアドとで同期された**MCDUserDataFeed**します。</span><span class="sxs-lookup"><span data-stu-id="e4348-116">These are all stored and synced in **MCDUserDataFeed**.</span></span> <span data-ttu-id="e4348-117">**MCDUserNotification**はグラフの通知を使用して送信するユーザーを対象と通知に対応するクラスとデータ型です。</span><span class="sxs-lookup"><span data-stu-id="e4348-117">**MCDUserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span>
<span data-ttu-id="e4348-118">グラフの通知とアプリケーション サーバーによって発行された MCDUserNotification の受信開始とを統合する必要がありますユーザー データを作成してフィードを初期化するために、 **MCDUserNotificationChannel**します。</span><span class="sxs-lookup"><span data-stu-id="e4348-118">To integrate with Graph Notification and start receiving MCDUserNotification published by your app server, you will first need to initialize the user data feed by creating a **MCDUserNotificationChannel**.</span></span> <span data-ttu-id="e4348-119">これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4348-119">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span>

<span data-ttu-id="e4348-120">次のメソッドの初期化、 **MCDUserNotificationChannel**します。</span><span class="sxs-lookup"><span data-stu-id="e4348-120">The following methods initialize a **MCDUserNotificationChannel**.</span></span>
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
<span data-ttu-id="e4348-121">この時点では、必要な**MCDUserNotificationChannel**で参照`channel`します。</span><span class="sxs-lookup"><span data-stu-id="e4348-121">At this point, you should have a **MCDUserNotificationChannel** reference in `channel`.</span></span>

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a><span data-ttu-id="e4348-122">着信 MCDUserNotifications を受信し、MCDUserNotification 履歴へのアクセスの MCDUserNotificationReader を作成します。</span><span class="sxs-lookup"><span data-stu-id="e4348-122">Create a MCDUserNotificationReader to receive incoming MCDUserNotifications and access MCDUserNotification history</span></span>
<span data-ttu-id="e4348-123">紹介したよう以前は、初期の APNS サイレント ショルダー タップにはがアプリのクライアントのみに到着したメッセージに含まれていて、接続されているデバイス プラットフォームに接続されているデバイスに完全同期を実行する SDK をトリガーするためにそのショルダー タップ ペイロードを渡す必要があります。サーバーは、アプリケーション サーバーによって発行されたすべての MCDUserNotifications が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e4348-123">As we showed previously, the initial APNS silent message arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the MCDUserNotifications published by your app server.</span></span> <span data-ttu-id="e4348-124">このショルダー タップに対応するアプリケーション サーバーによって発行されたすべての通知ペイロード ダウンがプルされます (は、場合も、以前の通知発行しますが、このアプリのクライアント デバイスの接続またはその他の問題が原因で受信しない場合プルダウンも)。</span><span class="sxs-lookup"><span data-stu-id="e4348-124">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="e4348-125">リアルタイム同期が SDK によって実行される継続的にこれらをアプリのクライアントがこのログインしているユーザーの MCDUserNotification データ フィードのローカル キャッシュにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e4348-125">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s MCDUserNotification data feed.</span></span> <span data-ttu-id="e4348-126">この場合により、アプリ クライアントのこのデータ フィード – へのアクセス、MCDUserNotificationReader イベントのリスナーを使用して最新の通知ペイロードを受信するか、ユーザーの通知のビュー モデルとして使用できる完全な MCDUserNotification コレクションにアクセスするには履歴。</span><span class="sxs-lookup"><span data-stu-id="e4348-126">A MCDUserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full MCDUserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-mcdusernotifications"></a><span data-ttu-id="e4348-127">受信側 MCDUserNotifications</span><span class="sxs-lookup"><span data-stu-id="e4348-127">Receiving MCDUserNotifications</span></span>
<span data-ttu-id="e4348-128">まずの MCDUserNotificationReader をインスタンス化しを有効にしようとして、エクスペリエンスの情報の使用に関心がある場合、リーダーで既に既存のすべての MCDUserNotifications を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4348-128">First you need to instantiate a MCDUserNotificationReader, and get all the existing MCDUserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="e4348-129">常に、アプリ サーバーは既に公開通知ユーザー、ログインしているこの特定のデバイス エンドポイントにしかできない可能性がありますまたは最初のエンドポイントをユーザーにアプリがインストールされていることを想定することも安全です。</span><span class="sxs-lookup"><span data-stu-id="e4348-129">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> <span data-ttu-id="e4348-130">次に、接続されているデバイスのプラットフォームが同期が完了し、新しい変更がユーザーに通知するトリガーを取得するイベント リスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e4348-130">Then, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="e4348-131">グラフの通知の場合、新しい変更が、新しい可能性があります、アプリのサーバー、または MCDUserNotifcation 更新プログラムの削除によって受信 MCDUserNotifications が発行され、有効期限の設定または他のサーバーから発生したエンドポイントの登録を同じユーザーログに記録します。</span><span class="sxs-lookup"><span data-stu-id="e4348-131">In the case of Graph Notifications, new changes could be new incoming MCDUserNotifications published by your app server, or MCDUserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span>

> [!TIP] 
> <span data-ttu-id="e4348-132">このイベント リスナーとは、主要なビジネス ロジックを処理して、シナリオに基づいた通知ペイロードのコンテンツを「使用」です。</span><span class="sxs-lookup"><span data-stu-id="e4348-132">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="e4348-133">現在、OS レベル通知センターでのビジュアル通知を構築する APNS サイレント通知を使用する場合、またはアプリ内 UI を更新するサイレント通知では、コンテンツを使用する場合は、この処理にはそのためには場所です。</span><span class="sxs-lookup"><span data-stu-id="e4348-133">If you currently use APNS silent notification to construct a visual notification in the OS-level notification center, or if you use the content in the silent notification to update some in-app UI, this is the place to do that.</span></span> 

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

## <a name="update-the-state-of-an-existing-mcdusernotification"></a><span data-ttu-id="e4348-134">既存の MCDUserNotification の状態を更新します。</span><span class="sxs-lookup"><span data-stu-id="e4348-134">Update the state of an existing MCDUserNotification</span></span>
<span data-ttu-id="e4348-135">前のセクションで説明した場合があります、リーダーから受信した MCDUserNotification 変更がある、既存の MCDUserNotification – で状態の更新済みまたはとしてマークされた既読としてマークされたされているかどうか。</span><span class="sxs-lookup"><span data-stu-id="e4348-135">In the previous section, we mentioned that sometimes a MCDUserNotification change received through the reader could be a state update on an existing MCDUserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="e4348-136">この場合、アプリ クライアントは、ユニバーサルの有効化など、この特定のデバイスに対応するのビジュアル通知を削除することで無視することはできます。</span><span class="sxs-lookup"><span data-stu-id="e4348-136">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="e4348-137">バックアップ手順を実行するには、アプリのクライアントは、多くの場合、別のデバイスから始めに – この MCDUserNotification 変更の更新を開始したされます。</span><span class="sxs-lookup"><span data-stu-id="e4348-137">Taking a step back, your app client is often the one that initiated this MCDUserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="e4348-138">、、MCDUserNotifications の状態を更新するときに選択することができますが、通常、更新、そのデバイスでユーザーが、対応する通知が処理され、通知はさらに処理によってアプリ内エクスペリエンスでユーザーがします。有効にします。</span><span class="sxs-lookup"><span data-stu-id="e4348-138">You can choose the time to update the state of your MCDUserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="e4348-139">次のフローがどのような例に示します。A. ユーザー A が彼の PC とアプリのクライアントがインストールされている電話の両方でこの通知を受け取るユーザーを対象とした通知をアプリケーション サーバーに発行します。</span><span class="sxs-lookup"><span data-stu-id="e4348-139">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="e4348-140">ユーザーは、PC では、通知をクリックしては追跡、アプリへのハンドルに対応するタスク。</span><span class="sxs-lookup"><span data-stu-id="e4348-140">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="e4348-141">この PC でアプリのクライアント後、この更新プログラムをこのユーザーのすべてのデバイス間で同期するためには、対応するユーザー通知の状態を更新するデバイス プラットフォーム SDK の接続に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e4348-141">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding User Notification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="e4348-142">これを受信すると、他のアプリ クライアントをリアルタイムで更新プログラムの状態、されますし、対応する視覚的な警告を削除/メッセージ/デバイスの通知センターからの通知のトースト/通知トレイ アクション センター。</span><span class="sxs-lookup"><span data-stu-id="e4348-142">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="e4348-143">これは、通知の取得、ユーザーのデバイス間で破棄普遍的方法です。</span><span class="sxs-lookup"><span data-stu-id="e4348-143">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP]
> <span data-ttu-id="e4348-144">MCDUserNotification クラスは、2 種類の状態の更新プログラムを現在提供 – MCDUserNotificationReadState、または、MCDUserNotificationUserActionState を変更し、通知が更新されるときの動作で独自のロジックを定義できます。</span><span class="sxs-lookup"><span data-stu-id="e4348-144">MCDUserNotification class currently provides 2 types of state updates – you can modify the MCDUserNotificationReadState or the MCDUserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="e4348-145">たとえばをアクティブ化済みまたは無視、アクションの状態をマークすることができ、ピボット ユニバーサルを実装するには、その値を無視します。</span><span class="sxs-lookup"><span data-stu-id="e4348-145">For example, you can mark the action state to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="e4348-146">または、または、同時にマークできます読み取り未読として状態を読み取って、に基づいて通知がアプリ内通知の履歴ビューに表示する必要がありますを決定します。</span><span class="sxs-lookup"><span data-stu-id="e4348-146">Alternatively, or at the same time, you can mark read state as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> 

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
