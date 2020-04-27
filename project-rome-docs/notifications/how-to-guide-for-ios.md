---
title: iOS アプリと Graph 通知の統合
description: アプリ サーバーから発行された通知の受信エンドポイントになるために必要な登録手順を実行する方法。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801314"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a>使い方ガイド: Graph 通知との統合 (iOS)

Graph 通知を使用すると、アプリはユーザーをターゲットにした通知を複数のデバイスにまたがって送信および管理できます。 

iOS 上の Project Rome クライアント側 SDK によって、iOS アプリは、ログイン中のユーザーをターゲットにしてアプリ サーバーから発行された通知を受信するための登録ができます。 アプリ クライアントは SDK を使用して、新しい着信通知ペイロードを受信したり、既存の通知の状態を管理したり、通知履歴を取得したりできます。 通知の詳細と、それによって人間が主体の通知配信が実現するしくみについては、[Microsoft Graph 通知の概要](index.md)に関するページを参照してください

Graph 通知などを含む Project Rome SDK のすべての機能は、Connected Devices Platform と呼ばれる基盤プラットフォーム上に構築されています。 このガイドの目的は、Connected Devices Platform を初めて使用するために必要な手順、および、Graph 通知に固有の機能を実装するために SDK で API を使用する方法について説明することです。

この手順では、GitHub から入手できる [Project Rome iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)のコードを参照します。  

通知のシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-ios/index.md)のページを参照してください。

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Connected Devices Platform と通知の設定

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームの使用

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a>Graph 通知チャネルの初期化
Graph 通知、ユーザー アクティビティなど、さまざまな種類のユーザー データを受信および管理するために、アプリで Project Rome SDK を使用してさまざまなチャネルに登録することができます。 これらはすべて **MCDUserDataFeed** に格納され、同期されます。 **MCDUserNotification** は、Graph 通知を介して送信される、ユーザーをターゲットにした通知に対応するクラスおよびデータ型です。
Graph 通知と統合して、アプリ サーバーによって発行された MCDUserNotification の受信を開始するには、まず **MCDUserNotificationChannel** を作成してユーザー データ フィードを初期化する必要があります。 これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。

次のメソッドは **MCDUserNotificationChannel** を初期化します。
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
この時点で、**MCDUserNotificationChannel** の参照が `channel` にあるはずです。

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a>MCDUserNotificationReader を作成して着信 MCDUserNotification を受信し MCDUserNotification の履歴にアクセスする
前に説明したように、アプリ クライアントに到着する初期の APNS サイレント メッセージにはショルダー タップしか含まれておらず、そのショルダー タップ ペイロードを Connected Devices Platform に渡して、Connected Device サーバーとの完全同期を SDK に実行させる必要があります。このサーバーには、アプリ サーバーによって発行されたすべての MCDUserNotification が格納されます。 これにより、アプリ サーバーによって発行され、このショルダー タップに対応している完全な通知ペイロードが取得されます (また、発行されたがデバイス接続性またはその他の問題のためこのアプリ クライアントで受信されなかった以前の通知がある場合、それらも同時に取得されます)。 これらのリアルタイム同期が継続的に SDK によって実行されるので、アプリ クライアントはこのログイン中ユーザーの MCDUserNotification データ フィードのローカル キャッシュにアクセスできます。 この場合、アプリ クライアントは MCDUserNotificationReader を使用してこのデータ フィードにアクセスし、イベント リスナーを介して最新の通知ペイロードを受信したり、ユーザーの通知履歴のビュー モデルとして使用できる完全な MCDUserNotification コレクションにアクセスしたりできます。  
### <a name="receiving-mcdusernotifications"></a>MCDUserNotification の受信
実現しようとしているエクスペリエンスのためにその情報を利用することに関心がある場合は、まず MCDUserNotificationReader をインスタンス化し、既にリーダーにある既存の MCDUserNotification をすべて取得する必要があります。 この特定のデバイス エンドポイントが、ユーザーがアプリをインストールした唯一または最初のエンドポイントではない可能性を考えると、アプリ サーバーはこのログイン中ユーザーに通知を発行済みであると常に想定するのが安全です。 次に、Connected Device プラットフォームで同期が完了し、通知する新しい変更がある時点でトリガーされるイベント リスナーを追加します。 Graph 通知の場合、新しい変更として可能性があるのは、アプリ サーバーによって発行された MCDUserNotification の新規着信、または、サーバーから発生したか同じユーザーがログインした他の登録済みエンドポイントから発生した MCDUserNotifcation の更新、削除、期限切れです。

> [!TIP] 
> このイベント リスナーは、メインのビジネス ロジックを処理し、シナリオに基づいて通知ペイロードの内容を "消費" する場所です。 現在 APNS サイレント通知を使用して OS レベルの通知センターで視覚的な通知を作成している場合、またはサイレント通知の内容を使用して何らかのアプリ内 UI を更新している場合、ここがそれらの処理を実行する場所です。 

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

## <a name="update-the-state-of-an-existing-mcdusernotification"></a>既存の MCDUserNotification の状態を更新する
前のセクションで説明しましたが、時として、リーダー経由で受信した MCDUserNotification の変更は、既存の MCDUserNotification の状態更新 (それが無視とマークされているか既読とマークされているかは問わない) である可能性があります。 この場合アプリ クライアントは、この特定のデバイス上で対応する視覚的通知を削除することによって全体無視を有効化するなど、実行する処理を選択できます。 少し話を戻すと、多くの場合、この MCDUserNotification の変更更新を最初に別のデバイスから開始したのはアプリ クライアントです。 MCDUserNotification の状態を更新するタイミングは選択できますが、それは通常、対応する視覚的通知がそのデバイス上でユーザーによって処理された時点、または、有効化する何らかのアプリ内エクスペリエンスでその通知がユーザーによってさらに処理された時点です。 フローがどのようになるかの例を次に示します。アプリ サーバーはユーザー A をターゲットに通知を発行します。ユーザー A は、アプリ クライアントがインストールされている PC と電話の両方でこの通知を受信します。 ユーザーは PC で通知をクリックし、対応するタスクを処理するためにアプリを起動します。 その後、この PC 上のアプリ クライアントが Connected Devices Platform SDK を呼び出して、対応するユーザー通知の状態を更新し、このユーザーのすべてのデバイス間でこの更新を同期します。 他のアプリ クライアントは、この状態更新をリアルタイムで受信すると、対応する視覚的アラート/メッセージ/トースト通知をデバイスの通知センター/通知トレイ/アクション センターから削除します。 これは、ユーザーのデバイス間で通知が全体無視されるしくみです。 

> [!TIP]
> MCDUserNotification クラスは現在、2 種類の状態更新を提供します。MCDUserNotificationReadState または MCDUserNotificationUserActionState を変更し、通知が更新されたときに実行する処理について独自のロジックを定義できます。 たとえば、アクションの状態を Activated (アクティブ化) または Dismissed (無視) とマークし、その値を基準にして全体無視を実装できます。 その代わりに、または同時に、読み取り状態を Read (既読) または Unread (未読) とマークし、それに基づいて、どの通知をアプリ内通知の履歴ビューに表示するかを決定できます。 

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
