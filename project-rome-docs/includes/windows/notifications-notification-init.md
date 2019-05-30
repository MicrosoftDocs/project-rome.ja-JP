---
ms.openlocfilehash: f81fbbffb2ec54f8d9a252a00fc3822f1f3f9582
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800854"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-platform"></a>接続されているデバイス プラットフォームを各プラットフォームのネイティブ プッシュ通知に関連付けます。 

ようにアプリのクライアントは既に触れましたが、各クライアント側の SDK プラットフォームとデバイスの接続されているプラットフォームのグラフを許可するには、登録プロセス中に使用されているネイティブのプッシュ通知のパイプラインに関する知識を提供する必要がありますアプリケーション サーバーは、MS Graph Api を使用してユーザーを対象とした通知を発行するときのアプリのクライアント エンドポイントは各にファンアウト通知を通知サービス。
上記の手順で、初期化せず、プラットフォーム**NotificationProvider**パラメーター。 ここでは、作成して実装するオブジェクトで渡す必要があります**NotificationProvider**します。 参照してください**GraphNotificationProvider.cs**の詳細についてはサンプルです。 



実装でこの登録を配信**NotificationProvider**します。 次に、**プラットフォーム**初期化呼び出しがローカルに提供する必要があります**プラットフォーム**プッシュ通知サービスにアクセスできる、MS Graph の通知サーバー側からデータを受信するアプリを許可します。 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>クライアント SDK にプッシュ通知の受信を渡す
ここで、PushNotificationTrigger、または、リスナーのでネイティブのバック グラウンド タスクが登録されている Windows 内で受信 UserNotification ペイロードを処理できる、 [PushNotificationReceived イベント](https://docs.microsoft.com/en-us/uwp/api/windows.networking.pushnotifications.pushnotificationchannel.pushnotificationreceived)します。 

コンプライアンス、セキュリティ、潜在的な最適化などの理由から、グラフの通知サーバー側から受信した WNS 生通知に最初に、アプリ サーバーによって公開されたデータは含まれませんが、ショルダー タップ可能性があります多くの場合。 アプリ サーバーによって発行された実際の通知コンテンツの取得は、クライアント側 SDK の Api の背後に表示されません。 この場合、SDK は常に、SDK に着信 WNS 生の通知ペイロードを渡すアプリ クライアントを確認します。 これにより、これはグラフの通知シナリオを通知するかどうか、またはしない場合に WNS 未加工のプッシュは、他の目的で、アプリのクライアントによっても使用できます) を決定する SDK ができます。 
