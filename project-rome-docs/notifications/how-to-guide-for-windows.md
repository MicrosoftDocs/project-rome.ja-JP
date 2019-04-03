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
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a>ハウツー ガイド:MS Graph 通知 (Windows UWP) との統合

Windows 上のグラフの通知のクライアント側 sdk では、Windows UWP アプリは、ユーザーを対象とした、アプリ サーバーから公開通知を受信する受信側のエンドポイントに必要な登録手順を実行できます。 SDK を使用し、ペイロードがこのクライアントに到着した新しい通知の受信通知の状態の管理、通知履歴の取得など、クライアント側で通知を管理できます。 MS Graph の通知と人間を中心とした通知の配信を有効にする方法の詳細については、次を参照してください[Microsoft Graph の通知の概要。](index.md)

参照してください、 [API リファレンス](api-reference-for-windows/index.md)通知シナリオに関連するリファレンス ドキュメントへのリンクについてのページ。

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a>グラフの通知を使用するには、接続されているデバイス プラットフォームにアクセスするための暫定的なセットアップ 
グラフの通知との統合を行う必要がありますをいくつかの手順します。
* MSA または AAD アプリの登録
* クロス プラットフォーム アプリ Id を提供するデベロッパー センター オンボードし、プッシュ通知の資格情報
* SDK を追加して、接続されているデバイス プラットフォームの初期化
* 通知サービスに接続されているデバイス プラットフォームを関連付ける

まず、MSA または AAD アプリの登録を完了する必要があります。 これが既に完了したら場合、次のセクションに進みます。
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
次に、する必要がありますオンボード グラフ通知の使用を含むクロス デバイス エクスペリエンスと統合するために接続されているデバイスのプラットフォームへのアクセスを取得する Microsoft Windows デベロッパー センターでします。 これが既に完了したら場合、次のセクションに進みます。
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
次に、プロジェクトのローマ SDK をプロジェクトに追加し、接続されているデバイス プラットフォームを初期化する必要があります。 これが既に完了したら場合、次のセクションに進みます。
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
最後に、アプリをプッシュ通知の受信を有効にする必要があります。 これが既に完了したら場合、次のセクションに進みます。
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a>グラフの通知チャネルを初期化します。
大まかに言えば、SDK によって、アプリを受信し、さまざまな種類のグラフの通知、ユーザーのアクティビティを含む – ユーザー データを管理するためにさまざまなチャネルにサブスクライブできます。 これらはすべてストアドとで同期された**UserDataFeed**します。 **UserNotification**はグラフの通知を使用して送信するユーザーを対象と通知に対応するクラスとデータ型です。 グラフの通知とアプリケーション サーバーによって発行された UserNotification の受信開始とを統合する必要がありますユーザー データを作成してフィードを初期化するために、 **UserNotificationChannel**します。 これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>着信 UserNotifications を受信し、UserNotification 履歴へのアクセスの UserNotificationReader を作成します。
**UserNotificationChannel**必要がある、参照、 **UserNotificationReader**サーバーから実際の通知の内容をフェッチする SDK を許可するためにします。 この場合により、アプリ クライアントのこのデータ フィード – へのアクセス、UserNotificationReader イベントのリスナーを使用して最新の通知ペイロードを受信するか、ユーザーの通知履歴のビュー モデルとして使用できる完全な UserNotification コレクションにアクセスします。  

次のコードは、ユーザーの通知チャネルをインスタンス化し、ユーザー通知のリーダーを作成し、ユーザー通知リーダーが接続されているデバイスのプラットフォームは、各同期が完了しへの新しい変更がトリガーされた取得のイベント ハンドラーを追加する手順を示しています。について通知します。 

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

### <a name="receiving-usernotifications"></a>受信側 UserNotifications

前のセクションで、ユーザー通知のリーダーに、イベント リスナーを追加することがわかります。 すべての新しい通知と通知の更新プログラムをリーダーから読み取りをするには、このイベント リスナーを実装し、それぞれこれらの新しい変更を処理するために、独自のビジネス ロジックを実装する必要があります。 

> [!TIP] 
> このイベント リスナーとは、主要なビジネス ロジックを処理して、シナリオに基づいた通知ペイロードのコンテンツを「使用」です。 現在、OS レベルのアクション センターのローカルのトースト通知を構築する WNS の生の通知を使用する場合、またはアプリ内 UI を更新する通知では、コンテンツを使用する場合は、この処理にはそのためには場所です。 

次のコードは、アクティブ、および通知が削除された場合、アプリ内のビューに対応する通知の UI が削除されるすべての着信 UserNotification のローカルのトースト通知を発生させるサンプル アプリを選択する方法を示します。 

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
## <a name="update-the-state-of-an-existing-usernotification"></a>既存の UserNotification の状態を更新します。
前のセクションで説明した場合があります、リーダーから受信した UserNotification 変更がある、既存の UserNotification – で状態の更新済みまたはとしてマークされた既読としてマークされたされているかどうか。 この場合、アプリ クライアントは、ユニバーサルの有効化など、この特定のデバイスに対応するのビジュアル通知を削除することで無視することはできます。 バックアップ手順を実行するには、アプリのクライアントは、多くの場合、別のデバイスから始めに – この UserNotification 変更の更新を開始したされます。 、、UserNotifications の状態を更新する時間を選択できますが、通常、更新、そのデバイス上のユーザーにより、対応する通知が処理されます。 または、通知が有効にすると一部のアプリ内エクスペリエンスでユーザーがさらに処理されるときに. 次のフローがどのような例に示します。A. ユーザー A が彼の PC とアプリのクライアントがインストールされている電話の両方でこの通知を受け取るユーザーを対象とした通知をアプリケーション サーバーに発行します。 ユーザーは、PC では、通知をクリックしては追跡、アプリへのハンドルに対応するタスク。 この PC でアプリのクライアント後、この更新プログラムをこのユーザーのすべてのデバイス間で同期するためには対応する UserNotification の状態を更新するデバイス プラットフォーム SDK の接続に呼び出します。 これを受信すると、他のアプリ クライアントをリアルタイムで更新プログラムの状態、されますし、対応する視覚的な警告を削除/メッセージ/デバイスの通知センターからの通知のトースト/通知トレイ アクション センター。 これは、通知の取得、ユーザーのデバイス間で破棄普遍的方法です。 

> [!TIP] 
> UserNotification クラスは、2 種類の状態の更新プログラムを現在提供 – UserNotificationReadState、または、UserNotificationUserActionState を変更し、通知が更新されるときの動作で独自のロジックを定義できます。 たとえばをアクティブ化済みまたは無視、UserActionState をマークすることができ、ピボット ユニバーサルを実装するには、その値を無視します。 または、または同時に ReadState を読み取りまたは未読としてマークでき、その指定に基づいて、通知がアプリ内通知の履歴ビューに表示する必要がありますを決定します。 次のコード スニペットは、通知を破棄としての UserNotificationUserActionState をマークする方法を示しています。

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
