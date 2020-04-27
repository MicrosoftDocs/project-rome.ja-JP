---
title: UWP アプリと Graph 通知の統合
description: アプリ サーバーから発行された通知の受信エンドポイントになるために必要な登録手順を実行する方法。
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801304"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a>使い方ガイド: MS Graph 通知との統合 (Windows UWP)

Windows の Graph 通知クライアント側 SDK を使用すると、Windows UWP アプリは、必要な登録手順を実行して、ユーザーをターゲットにしてアプリ サーバーから発行された通知を受信する受信エンドポイントになることができます。 その後は、このクライアントに到着した新しい通知ペイロードの受信、通知の状態の管理、通知履歴の取得など、クライアント側で通知を管理するためにこの SDK を使用します。 MS Graph 通知の詳細と、それによって人間が主体の通知配信が実現するしくみについては、[Microsoft Graph 通知の概要](index.md)に関するページを参照してください

通知のシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-windows/index.md)のページを参照してください。

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a>Connected Devices Platform にアクセスして Graph 通知を使用するための準備段階のセットアップ 
Graph 通知と統合するために、いくつかの手順を実行する必要があります。
* MSA または AAD アプリ登録
* クロスプラットフォームのアプリ ID とプッシュ通知資格情報を提供するためのデベロッパー センターでのオンボーディング
* SDK の追加と Connected Devices Platform の初期化
* 通知サービスと Connected Devices Platform の関連付け

まず、MSA/AAD アプリ登録を完了する必要があります。 これが既に完了している場合、次のセクションに進みます。
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
次に、Graph 通知の使用などのクロスデバイス エクスペリエンスと統合するために、Microsoft Windows デベロッパー センターでオンボーディングを行い、Connected Device Platform にアクセスできるようにする必要があります。 これが既に完了している場合、次のセクションに進みます。
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
次に、Project Rome SDK をプロジェクトに追加して、Connected Devices Platform を初期化する必要があります。 これが既に完了している場合、次のセクションに進みます。
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
最後に、アプリでのプッシュ通知の受信を有効化する必要があります。 これが既に完了している場合、次のセクションに進みます。
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a>Graph 通知チャネルの初期化
大まかに言えば、Graph 通知、ユーザー アクティビティなど、さまざまな種類のユーザー データを受信および管理するために、アプリで SDK を使用してさまざまなチャネルに登録することができます。 これらはすべて **UserDataFeed** に格納され、同期されます。 **UserNotification** は、Graph 通知を介して送信される、ユーザーをターゲットにした通知に対応するクラスおよびデータ型です。 Graph 通知と統合して、アプリ サーバーによって発行された UserNotification の受信を開始するには、まず **UserNotificationChannel** を作成してユーザー データ フィードを初期化する必要があります。 これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>UserNotificationReader を作成して着信 UserNotification を受信し UserNotification の履歴にアクセスする
**UserNotificationChannel** の参照を取得したら、SDK で実際の通知内容をサーバーから取得できるようにするために **UserNotificationReader** が必要です。 この場合、アプリ クライアントは UserNotificationReader を使用してこのデータ フィードにアクセスし、イベント リスナーを介して最新の通知ペイロードを受信したり、ユーザーの通知履歴のビュー モデルとして使用できる完全な UserNotification コレクションにアクセスしたりできます。  

次のコードは、ユーザー通知チャネルをインスタンス化し、ユーザー通知リーダーを作成し、イベント ハンドラーをユーザー通知リーダーに追加する手順を示しています。このイベント ハンドラーは、Connected Device Platform が毎回の同期を完了し、通知が必要な新しい変更があるときにトリガーされます。 

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

### <a name="receiving-usernotifications"></a>UserNotification の受信

前のセクションで、イベント リスナーをユーザー通知リーダーに追加しています。 すべての新しい通知と通知の更新をリーダーから読み取るために、このイベント リスナーを実装する必要があります。また、これらの新しい変更を個々に処理する独自のビジネス ロジックを実装する必要があります。 

> [!TIP] 
> このイベント リスナーは、メインのビジネス ロジックを処理し、シナリオに基づいて通知ペイロードの内容を "消費" する場所です。 現在 WNS の直接通知を使用して OS レベルのアクション センターでローカル トースト通知を作成している場合、または通知の内容を使用して何らかのアプリ内 UI を更新している場合、ここがそれらの処理を実行する場所です。 

次のコードは、サンプル アプリにおいて、アクティブであるすべての着信 UserNotification に対してローカル トースト通知を発生させる方法、また、通知が削除された場合に、それに対応する通知 UI をアプリ内ビューから削除する方法を示しています。 

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
## <a name="update-the-state-of-an-existing-usernotification"></a>既存の UserNotification の状態を更新する
前のセクションで説明しましたが、時として、リーダー経由で受信した UserNotification の変更は、既存の UserNotification の状態更新 (それが無視とマークされているか既読とマークされているかは問わない) である可能性があります。 この場合アプリ クライアントは、この特定のデバイス上で対応する視覚的通知を削除することによって全体無視を有効化するなど、実行する処理を選択できます。 少し話を戻すと、多くの場合、この UserNotification の変更更新を最初に別のデバイスから開始したのはアプリ クライアントです。 UserNotification の状態を更新するタイミングは選択できますが、それは通常、対応する視覚的通知がそのデバイス上でユーザーによって処理された時点、または、有効化する何らかのアプリ内エクスペリエンスでその通知がユーザーによってさらに処理された時点です。 フローがどのようになるかの例を次に示します。アプリ サーバーはユーザー A をターゲットに通知を発行します。ユーザー A は、アプリ クライアントがインストールされている PC と電話の両方でこの通知を受信します。 ユーザーは PC で通知をクリックし、対応するタスクを処理するためにアプリを起動します。 その後、この PC 上のアプリ クライアントが Connected Devices Platform SDK を呼び出して、対応する UserNotification の状態を更新し、このユーザーのすべてのデバイス間でこの更新を同期します。 他のアプリ クライアントは、この状態更新をリアルタイムで受信すると、対応する視覚的アラート/メッセージ/トースト通知をデバイスの通知センター/通知トレイ/アクション センターから削除します。 これは、ユーザーのデバイス間で通知が全体無視されるしくみです。 

> [!TIP] 
> UserNotification クラスは現在、2 種類の状態更新を提供します。UserNotificationReadState または UserNotificationUserActionState を変更し、通知が更新されたときに実行する処理について独自のロジックを定義できます。 たとえば、UserActionState を Activated (アクティブ化) または Dismissed (無視) とマークし、その値を基準にして全体無視を実装できます。 その代わりに、または同時に、ReadState を Read (既読) または Unread (未読) とマークし、それに基づいて、どの通知をアプリ内通知の履歴ビューに表示するかを決定できます。 次のコード スニペットは、通知の UserNotificationUserActionState を Dismissed とマークする方法を示しています。

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
