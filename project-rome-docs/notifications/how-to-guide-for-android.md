---
title: グラフの通知と Android アプリの統合
description: 通知の受信側のエンドポイントに必要な登録手順を実行する方法は、アプリケーション サーバーから発行します。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801204"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a>ハウツー ガイド:グラフの通知 (Android) との統合

グラフの通知の送信し、複数のデバイスでユーザーを対象とした通知を管理するアプリを有効にします。 

Android プロジェクト ローマ クライアント側 sdk では、ログインしているユーザーを対象とした、アプリ サーバーから公開通知を受信する Android アプリを登録できます。 SDK では、アプリ クライアントで新しい受信の通知ペイロードが表示される、既存の通知および通知履歴の取得の状態を管理できるようにします。 通知と人間を中心とした通知の配信を有効にする方法の詳細については、次を参照してください[Microsoft Graph の通知の概要。](index.md)

Project ローマ SDK、includng グラフ通知などのすべての機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームの上に構築されます。 このガイドは、接続されているデバイス プラットフォームの使用を開始して、グラフの通知を実装する SDK の Api を使用する方法を説明するために必要な手順について説明しています-特定の機能です。

参照してください、 [API リファレンス](api-reference-for-android.md)通知シナリオに関連するリファレンス ドキュメントへのリンクについてのページ。

この手順はからコードを参照、[プロジェクト ローマ Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)します。

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a>グラフの通知チャネルを初期化します。
プロジェクトのローマ SDK は、受信し、さまざまな種類のグラフの通知、ユーザーのアクティビティを含む – ユーザー データを管理するためにさまざまなチャネルをサブスクライブするアプリを使用できます。 これらはすべてストアドとで同期された**UserDataFeed**します。 **UserNotification**はグラフの通知を使用して送信するユーザーを対象と通知に対応するクラスとデータ型です。 グラフの通知とアプリケーション サーバーによって発行された UserNotification の受信開始とを統合する必要がありますユーザー データを作成してフィードを初期化するために、 **UserNotificationChannel**します。 これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。 

次のメソッドの初期化、 **UserNotificationChannel**します。

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
この時点では、必要な**UserNotificationChannel**で参照`mNotificationChannel`します。

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>着信 UserNotifications を受信し、UserNotification 履歴へのアクセスの UserNotificationReader を作成します。
到着最初、Google Cloud Messaging に通知を見せ以前は、アプリのクライアントのみが含まれる肩のタップと接続されているデバイス プラットフォームに完全な同期を実行する SDK をトリガーするためにそのショルダー タップ ペイロードを渡す必要がある、アプリケーション サーバーによって発行されたすべての UserNotifications を含むデバイス サーバーに接続されています。 このショルダー タップに対応するアプリケーション サーバーによって発行されたすべての通知ペイロード ダウンがプルされます (は、場合も、以前の通知発行しますが、このアプリのクライアント デバイスの接続またはその他の問題が原因で受信しない場合プルダウンも)。 リアルタイム同期が SDK によって実行される継続的にこれらをアプリのクライアントがこのログインしているユーザーの UserNotification データ フィードのローカル キャッシュにアクセスできます。 この場合により、アプリ クライアントのこのデータ フィード – へのアクセス、UserNotificationReader イベントのリスナーを使用して最新の通知ペイロードを受信するか、ユーザーの通知履歴のビュー モデルとして使用できる完全な UserNotification コレクションにアクセスします。  
### <a name="receiving-usernotifications"></a>受信側 UserNotifications
まずの UserNotificationReader をインスタンス化しを有効にしようとして、エクスペリエンスの情報の使用に関心がある場合、リーダーで既に既存のすべての UserNotifications を取得する必要があります。 常に、アプリ サーバーは既に公開通知ユーザー、ログインしているこの特定のデバイス エンドポイントにしかできない可能性がありますまたは最初のエンドポイントをユーザーにアプリがインストールされていることを想定することも安全です。 
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
接続されているデバイスのプラットフォームが同期が完了し、新しい変更がユーザーに通知するトリガーを取得するイベント リスナーを追加します。 グラフの通知の場合、新しい変更が、新しい可能性があります、アプリのサーバー、または UserNotifcation 更新プログラムの削除によって受信 UserNotifications が発行され、有効期限の設定または他のサーバーから発生した同じユーザーがログインしてエンドポイントを登録します。でします。 
> [!TIP] 
> このイベント リスナーとは、主要なビジネス ロジックを処理して、シナリオに基づいた通知ペイロードのコンテンツを「使用」です。 現在、OS レベル通知トレイで視覚的に通知を作成するデータの Google Cloud Messaging のメッセージを使用する場合、またはアプリ内 UI を更新する通知では、コンテンツを使用する場合は、この処理にはそのためには場所です。 
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
## <a name="update-the-state-of-an-existing-usernotification"></a>既存の UserNotification の状態を更新します。
前のセクションで説明した場合があります、リーダーから受信した UserNotification 変更がある、既存の UserNotification – で状態の更新済みまたはとしてマークされた既読としてマークされたされているかどうか。 この場合、アプリ クライアントは、ユニバーサルの有効化など、この特定のデバイスに対応するのビジュアル通知を削除することで無視することはできます。 バックアップ手順を実行するには、アプリのクライアントは、多くの場合、別のデバイスから始めに – この UserNotification 変更の更新を開始したされます。 、、UserNotifications の状態を更新する時間を選択できますが、通常、更新、そのデバイス上のユーザーにより、対応する通知が処理されます。 または、通知が有効にすると一部のアプリ内エクスペリエンスでユーザーがさらに処理されるときに. 次のフローがどのような例に示します。A. ユーザー A が彼の PC とアプリのクライアントがインストールされている電話の両方でこの通知を受け取るユーザーを対象とした通知をアプリケーション サーバーに発行します。 ユーザーは、PC では、通知をクリックしては追跡、アプリへのハンドルに対応するタスク。 この PC でアプリのクライアント後、この更新プログラムをこのユーザーのすべてのデバイス間で同期するためには対応する UserNotification の状態を更新するデバイス プラットフォーム SDK の接続に呼び出します。 これを受信すると、他のアプリ クライアントをリアルタイムで更新プログラムの状態、されますし、対応する視覚的な警告を削除/メッセージ/デバイスの通知センターからの通知のトースト/通知トレイ アクション センター。 これは、通知の取得、ユーザーのデバイス間で破棄普遍的方法です。 

> [!TIP] 
> UserNotification クラスは、2 種類の状態の更新プログラムを現在提供 – UserNotificationReadState、または、UserNotificationUserActionState を変更し、通知が更新されるときの動作で独自のロジックを定義できます。 たとえばをアクティブ化済みまたは無視、UserActionState をマークすることができ、ピボット ユニバーサルを実装するには、その値を無視します。 または、または同時に ReadState を読み取りまたは未読としてマークでき、その指定に基づいて、通知がアプリ内通知の履歴ビューに表示する必要がありますを決定します。 次のコード スニペットは、通知を破棄としての UserNotificationUserActionState をマークする方法を示しています。

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
