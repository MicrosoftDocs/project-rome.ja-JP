---
ms.openlocfilehash: f81fbbffb2ec54f8d9a252a00fc3822f1f3f9582
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59800854"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-platform"></a>Connected Devices Platform を各プラットフォームのネイティブのプッシュ通知に関連付けます。 

既に触れたように、アプリ クライアントは、登録プロセスの間、各プラットフォームで使用されているネイティブのプッシュ通知パイプラインに関する情報を、クライアント側 SDK と Connected Devices Platform に提供する必要があります。これは、ユーザーをターゲットにした通知をアプリ サーバーが MS Graph API を使って発行したときに、Graph の通知サービスが個々のアプリ クライアント エンドポイントに通知を拡散できるようにするためです。
上記の手順では、**NotificationProvider** パラメーターなしでプラットフォームを初期化しました。 ここでは、**NotificationProvider** を実装するオブジェクトを作成して渡す必要があります。 詳細については、サンプルの **GraphNotificationProvider.cs** を参照してください。 



**NotificationProvider** の実装でこの登録を配信します。 次に、**Platform** の初期化呼び出しで、プッシュ通知サービスへのアクセスをローカルの **Platform** に提供して、サーバー側の MS Graph 通知からアプリがデータを受信できるようにする必要があります。 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>着信プッシュ通知をクライアント SDK に渡す
これで、着信 UserNotification ペイロードを、PushNotificationTrigger に登録された Windows ネイティブのバックグラウンド タスク内で、または [PushNotificationReceived イベント](https://docs.microsoft.com/en-us/uwp/api/windows.networking.pushnotifications.pushnotificationchannel.pushnotificationreceived)のリスナーで処理できます。 

コンプライアンス、セキュリティ、潜在的な最適化などの理由から、サーバー側の Graph 通知から受信する WNS 直接通知は、多くの場合、アプリ サーバーによって最初に公開される一切のデータを含まないショルダー タップである可能性があります。 アプリ サーバーによって発行された実際の通知内容の取得は、クライアント側の SDK API の背後に隠されています。 この場合、SDK は常に、着信 WNS 直接通知ペイロードを SDK に渡すことをアプリ クライアントに求めます。 SDK はこれによって、(WNS 直接プッシュがアプリ クライアントによって他の目的にも使用される可能性がある場合に) これが Graph 通知のシナリオ用の通知であるかどうかを判断できます。 
