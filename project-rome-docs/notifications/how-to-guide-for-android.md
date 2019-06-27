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
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a>使い方ガイド: Graph 通知との統合 (Android)

Graph 通知を使用すると、アプリはユーザーをターゲットにした通知を複数のデバイスにまたがって送信および管理できます。 

Android 上の Project Rome クライアント側 SDK によって、Android アプリは、ログイン中のユーザーをターゲットにしてアプリ サーバーから発行された通知を受信するための登録ができます。 アプリ クライアントは SDK を使用して、新しい着信通知ペイロードを受信したり、既存の通知の状態を管理したり、通知履歴を取得したりできます。 通知の詳細と、それによって人間が主体の通知配信が実現するしくみについては、[Microsoft Graph 通知の概要](index.md)に関するページを参照してください

Graph 通知などを含む Project Rome SDK のすべての機能は、Connected Devices Platform と呼ばれる基盤プラットフォーム上に構築されています。 このガイドの目的は、Connected Devices Platform を初めて使用するために必要な手順、および、Graph 通知に固有の機能を実装するために SDK で API を使用する方法について説明することです。

通知のシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-android.md)のページを参照してください。

この手順では、[Project Rome Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)のコードを参照します。

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a>Graph 通知チャネルの初期化
Graph 通知、ユーザー アクティビティなど、さまざまな種類のユーザー データを受信および管理するために、アプリで Project Rome SDK を使用してさまざまなチャネルに登録することができます。 これらはすべて **UserDataFeed** に格納され、同期されます。 **UserNotification** は、Graph 通知を介して送信される、ユーザーをターゲットにした通知に対応するクラスおよびデータ型です。 Graph 通知と統合して、アプリ サーバーによって発行された UserNotification の受信を開始するには、まず **UserNotificationChannel** を作成してユーザー データ フィードを初期化する必要があります。 これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。 

次のメソッドは **UserNotificationChannel** を初期化します。

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
この時点で、**UserNotificationChannel** の参照が `mNotificationChannel` にあるはずです。

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>UserNotificationReader を作成して着信 UserNotification を受信し UserNotification の履歴にアクセスする
前に説明したように、アプリ クライアントに到着する初期の Google Cloud Messaging 通知にはショルダー タップしか含まれておらず、そのショルダー タップ ペイロードを Connected Devices Platform に渡して、Connected Device サーバーとの完全同期を SDK に実行させる必要があります。このサーバーには、アプリ サーバーによって発行されたすべての UserNotification が格納されます。 これにより、アプリ サーバーによって発行され、このショルダー タップに対応している完全な通知ペイロードが取得されます (また、発行されたがデバイス接続性またはその他の問題のためこのアプリ クライアントで受信されなかった以前の通知がある場合、それらも同時に取得されます)。 これらのリアルタイム同期が継続的に SDK によって実行されるので、アプリ クライアントはこのログイン中ユーザーの UserNotification データ フィードのローカル キャッシュにアクセスできます。 この場合、アプリ クライアントは UserNotificationReader を使用してこのデータ フィードにアクセスし、イベント リスナーを介して最新の通知ペイロードを受信したり、ユーザーの通知履歴のビュー モデルとして使用できる完全な UserNotification コレクションにアクセスしたりできます。  
### <a name="receiving-usernotifications"></a>UserNotification の受信
実現しようとしているエクスペリエンスのためにその情報を利用することに関心がある場合は、まず UserNotificationReader をインスタンス化し、既にリーダーにある既存の UserNotification をすべて取得する必要があります。 この特定のデバイス エンドポイントが、ユーザーがアプリをインストールした唯一または最初のエンドポイントではない可能性を考えると、アプリ サーバーはこのログイン中ユーザーに通知を発行済みであると常に想定するのが安全です。 
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
ここで、Connected Devices Platform で同期が完了し、通知する新しい変更がある時点でトリガーされるイベント リスナーを追加します。 Graph 通知の場合、新しい変更として可能性があるのは、アプリ サーバーによって発行された UserNotification の新規着信、または、サーバーから発生したか同じユーザーがログインした他の登録済みエンドポイントから発生した UserNotifcation の更新、削除、期限切れです。 
> [!TIP] 
> このイベント リスナーは、メインのビジネス ロジックを処理し、シナリオに基づいて通知ペイロードの内容を "消費" する場所です。 現在 Google Cloud Messaging のデータ メッセージを使用して OS レベルの通知トレイで視覚的な通知を作成している場合、または通知の内容を使用して何らかのアプリ内 UI を更新している場合、ここがそれらの処理を実行する場所です。 
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
## <a name="update-the-state-of-an-existing-usernotification"></a>既存の UserNotification の状態を更新する
前のセクションで説明しましたが、時として、リーダー経由で受信した UserNotification の変更は、既存の UserNotification の状態更新 (それが無視とマークされているか既読とマークされているかは問わない) である可能性があります。 この場合アプリ クライアントは、この特定のデバイス上で対応する視覚的通知を削除することによって全体無視を有効化するなど、実行する処理を選択できます。 少し話を戻すと、多くの場合、この UserNotification の変更更新を最初に別のデバイスから開始したのはアプリ クライアントです。 UserNotification の状態を更新するタイミングは選択できますが、それは通常、対応する視覚的通知がそのデバイス上でユーザーによって処理された時点、または、有効化する何らかのアプリ内エクスペリエンスでその通知がユーザーによってさらに処理された時点です。 フローがどのようになるかの例を次に示します。アプリ サーバーはユーザー A をターゲットに通知を発行します。ユーザー A は、アプリ クライアントがインストールされている PC と電話の両方でこの通知を受信します。 ユーザーは PC で通知をクリックし、対応するタスクを処理するためにアプリを起動します。 その後、この PC 上のアプリ クライアントが Connected Devices Platform SDK を呼び出して、対応する UserNotification の状態を更新し、このユーザーのすべてのデバイス間でこの更新を同期します。 他のアプリ クライアントは、この状態更新をリアルタイムで受信すると、対応する視覚的アラート/メッセージ/トースト通知をデバイスの通知センター/通知トレイ/アクション センターから削除します。 これは、ユーザーのデバイス間で通知が全体無視されるしくみです。 

> [!TIP] 
> UserNotification クラスは現在、2 種類の状態更新を提供します。UserNotificationReadState または UserNotificationUserActionState を変更し、通知が更新されたときに実行する処理について独自のロジックを定義できます。 たとえば、UserActionState を Activated (アクティブ化) または Dismissed (無視) とマークし、その値を基準にして全体無視を実装できます。 その代わりに、または同時に、ReadState を Read (既読) または Unread (未読) とマークし、それに基づいて、どの通知をアプリ内通知の履歴ビューに表示するかを決定できます。 次のコード スニペットは、通知の UserNotificationUserActionState を Dismissed とマークする方法を示しています。

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
