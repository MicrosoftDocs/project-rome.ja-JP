---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58909694"
---
### <a name="add-the-sdk"></a>SDK を追加します。

Windows での Graph 通知 SDK が使用できる組み込みの OS の Windows SDK の代わりに NuGet パッケージを使用して、開発者がより下位レベルのサポートとより柔軟なリリース スケジュールするには。 NuGet パッケージが nuget.org で msgraphsdkteam によって公開されたを見つかります[ここ](https://www.nuget.org/profiles/msgraphsdkteam)します。 

など、UWP アプリから NuGet パッケージの使用の詳細については、これらのリンクを参照してください。 
* [Nuget.org からパッケージを使用します。](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)
* [クイック スタート:インストールして、Visual Studio でパッケージを使用](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




実装するシナリオ、に応じてを多く必要はありませんすべての名前空間。 グラフの通知を具体的には、必要があります、次のように名前空間。


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a>接続されているデバイス プラットフォームを初期化します。

接続されたデバイスの機能を使用できますが、前に、プラットフォームは、アプリ内で初期化しなければなりません。 初期化の手順は、メインのクラスで発生する必要があります**OnLaunched**または**onActivated**メソッド、その他の接続されたデバイス シナリオを実行する前に必要なためです。 

インスタンス化する必要があります、 **ConnectedDevicesPlatform**クラス。 **ConnectedDevicesPlatform**コンス トラクターは 3 つのパラメーターを受け取ります。**コンテキスト**アプリの場合、 **NotificationProvider**、および**UserAccountProvider**します。

**NotificationProvider**パラメーターは特定のシナリオでのみ必要です。 Microsoft Graph の通知を使用する場合が必要です。 ここでは空のままにし、クライアントのネイティブのプッシュ チャネルを使用してユーザーを中心とした通知の受信を処理するために SDK を有効にする方法に関する次のセクションで詳細を確認します。

**UserAccountProvider**接続されているデバイス プラットフォームに現在のユーザーのアクセス用の OAuth 2.0 アクセス トークンを提供するが必要です。 アプリが実行され、更新トークンのプラットフォームで管理された期限切れには、最初に呼び出されます。 

簡単に、プラットフォームをオンボード開発者を支援するために提供していますアカウント プロバイダーの実装のサンプル コードでの Windows を確認してくださいチェック**MicrosoftAccountProvider.cs**の詳細。 

作成し、**プラットフォーム**インスタンス。 

```C#

public async Task InstantiatePlatform()
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


                }
            }
        });
    }
}

```

アプリがフォア グラウンドを終了するときは、プラットフォームをシャット ダウンする必要があります。

```C#

public async void Reset()
{
    if (m_platform != null)
    {
        await m_platform.ShutdownAsync();
        m_platform = null;
        m_feed = null;
        m_newNotifications.Clear();
        m_historicalNotifications.Clear();
    }
}

```
