---
title: グラフの通知を IOs アプリの統合
description: 通知の受信側のエンドポイントに必要な登録手順を実行する方法は、アプリケーション サーバーから発行します。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801314"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a>ハウツー ガイド:グラフの通知 (iOS) との統合

グラフの通知の送信し、複数のデバイスでユーザーを対象とした通知を管理するアプリを有効にします。 

Ios プロジェクト ローマ クライアント側 sdk では、ログインしているユーザーを対象とした、アプリ サーバーから公開通知を受信する iOS アプリを登録できます。 SDK では、アプリ クライアントで新しい受信の通知ペイロードが表示される、既存の通知および通知履歴の取得の状態を管理できるようにします。 通知と人間を中心とした通知の配信を有効にする方法の詳細については、次を参照してください[Microsoft Graph の通知の概要。](index.md)

Project ローマ SDK、includng グラフ通知などのすべての機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームの上に構築されます。 このガイドは、接続されているデバイス プラットフォームの使用を開始して、グラフの通知を実装する SDK の Api を使用する方法を説明するために必要な手順について説明しています-特定の機能です。

この手順はからコードを参照、[プロジェクト ローマ iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)GitHub に用意されています。  

参照してください、 [API リファレンス](api-reference-for-ios/index.md)通知シナリオに関連するリファレンス ドキュメントへのリンクについてのページ。

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>接続されているデバイス プラットフォームと通知を設定します。

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームを使用します。

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a>グラフの通知チャネルを初期化します。
プロジェクトのローマ SDK は、受信し、さまざまな種類のグラフの通知、ユーザーのアクティビティを含む – ユーザー データを管理するためにさまざまなチャネルをサブスクライブするアプリを使用できます。 これらはすべてストアドとで同期された**MCDUserDataFeed**します。 **MCDUserNotification**はグラフの通知を使用して送信するユーザーを対象と通知に対応するクラスとデータ型です。
グラフの通知とアプリケーション サーバーによって発行された MCDUserNotification の受信開始とを統合する必要がありますユーザー データを作成してフィードを初期化するために、 **MCDUserNotificationChannel**します。 これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。

次のメソッドの初期化、 **MCDUserNotificationChannel**します。
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
この時点では、必要な**MCDUserNotificationChannel**で参照`channel`します。

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a>着信 MCDUserNotifications を受信し、MCDUserNotification 履歴へのアクセスの MCDUserNotificationReader を作成します。
紹介したよう以前は、初期の APNS サイレント ショルダー タップにはがアプリのクライアントのみに到着したメッセージに含まれていて、接続されているデバイス プラットフォームに接続されているデバイスに完全同期を実行する SDK をトリガーするためにそのショルダー タップ ペイロードを渡す必要があります。サーバーは、アプリケーション サーバーによって発行されたすべての MCDUserNotifications が含まれています。 このショルダー タップに対応するアプリケーション サーバーによって発行されたすべての通知ペイロード ダウンがプルされます (は、場合も、以前の通知発行しますが、このアプリのクライアント デバイスの接続またはその他の問題が原因で受信しない場合プルダウンも)。 リアルタイム同期が SDK によって実行される継続的にこれらをアプリのクライアントがこのログインしているユーザーの MCDUserNotification データ フィードのローカル キャッシュにアクセスできます。 この場合により、アプリ クライアントのこのデータ フィード – へのアクセス、MCDUserNotificationReader イベントのリスナーを使用して最新の通知ペイロードを受信するか、ユーザーの通知のビュー モデルとして使用できる完全な MCDUserNotification コレクションにアクセスするには履歴。  
### <a name="receiving-mcdusernotifications"></a>受信側 MCDUserNotifications
まずの MCDUserNotificationReader をインスタンス化しを有効にしようとして、エクスペリエンスの情報の使用に関心がある場合、リーダーで既に既存のすべての MCDUserNotifications を取得する必要があります。 常に、アプリ サーバーは既に公開通知ユーザー、ログインしているこの特定のデバイス エンドポイントにしかできない可能性がありますまたは最初のエンドポイントをユーザーにアプリがインストールされていることを想定することも安全です。 次に、接続されているデバイスのプラットフォームが同期が完了し、新しい変更がユーザーに通知するトリガーを取得するイベント リスナーを追加します。 グラフの通知の場合、新しい変更が、新しい可能性があります、アプリのサーバー、または MCDUserNotifcation 更新プログラムの削除によって受信 MCDUserNotifications が発行され、有効期限の設定または他のサーバーから発生したエンドポイントの登録を同じユーザーログに記録します。

> [!TIP] 
> このイベント リスナーとは、主要なビジネス ロジックを処理して、シナリオに基づいた通知ペイロードのコンテンツを「使用」です。 現在、OS レベル通知センターでのビジュアル通知を構築する APNS サイレント通知を使用する場合、またはアプリ内 UI を更新するサイレント通知では、コンテンツを使用する場合は、この処理にはそのためには場所です。 

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

## <a name="update-the-state-of-an-existing-mcdusernotification"></a>既存の MCDUserNotification の状態を更新します。
前のセクションで説明した場合があります、リーダーから受信した MCDUserNotification 変更がある、既存の MCDUserNotification – で状態の更新済みまたはとしてマークされた既読としてマークされたされているかどうか。 この場合、アプリ クライアントは、ユニバーサルの有効化など、この特定のデバイスに対応するのビジュアル通知を削除することで無視することはできます。 バックアップ手順を実行するには、アプリのクライアントは、多くの場合、別のデバイスから始めに – この MCDUserNotification 変更の更新を開始したされます。 、、MCDUserNotifications の状態を更新するときに選択することができますが、通常、更新、そのデバイスでユーザーが、対応する通知が処理され、通知はさらに処理によってアプリ内エクスペリエンスでユーザーがします。有効にします。 次のフローがどのような例に示します。A. ユーザー A が彼の PC とアプリのクライアントがインストールされている電話の両方でこの通知を受け取るユーザーを対象とした通知をアプリケーション サーバーに発行します。 ユーザーは、PC では、通知をクリックしては追跡、アプリへのハンドルに対応するタスク。 この PC でアプリのクライアント後、この更新プログラムをこのユーザーのすべてのデバイス間で同期するためには、対応するユーザー通知の状態を更新するデバイス プラットフォーム SDK の接続に呼び出します。 これを受信すると、他のアプリ クライアントをリアルタイムで更新プログラムの状態、されますし、対応する視覚的な警告を削除/メッセージ/デバイスの通知センターからの通知のトースト/通知トレイ アクション センター。 これは、通知の取得、ユーザーのデバイス間で破棄普遍的方法です。 

> [!TIP]
> MCDUserNotification クラスは、2 種類の状態の更新プログラムを現在提供 – MCDUserNotificationReadState、または、MCDUserNotificationUserActionState を変更し、通知が更新されるときの動作で独自のロジックを定義できます。 たとえばをアクティブ化済みまたは無視、アクションの状態をマークすることができ、ピボット ユニバーサルを実装するには、その値を無視します。 または、または、同時にマークできます読み取り未読として状態を読み取って、に基づいて通知がアプリ内通知の履歴ビューに表示する必要がありますを決定します。 

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
