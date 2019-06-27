---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "58909694"
---
### <a name="add-the-sdk"></a>SDK の追加

Windows では、下位レベルのサポート強化と、より柔軟なリリース スケジュールのために、OS 組み込みの Windows SDK の代わりに、Graph Notification SDK が NuGet パッケージを通じて開発者に提供されます。 NuGet パッケージは msgraphsdkteam によって nuget.org で公開されており、[ここ](https://www.nuget.org/profiles/msgraphsdkteam)から入手できます。 

UWP アプリから NuGet パッケージをインクルードして使用する方法については、以下のリンクを参照してください。 
* [Use packages from nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav) \(nuget.org からのパッケージを使用する\)
* [クイック スタート: Visual Studio でパッケージをインストールして使用する](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




実装するシナリオによっては、すべての名前空間が必要とは限りません。 特にグラフ通知の場合は、次に示す名前空間が必要です。


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a>Connected Devices Platform の初期化

Connected Devices の機能を使用できるようになる前に、アプリ内でプラットフォームを初期化する必要があります。 他の Connected Devices のシナリオが実行可能になる前に初期化手順が必要なため、main クラスの **OnLaunched** または **onActivated** メソッドで初期化手順を実行する必要があります。 

**ConnectedDevicesPlatform** クラスをインスタンス化する必要があります。 **ConnectedDevicesPlatform** コンストラクターは、アプリの **Context**、**NotificationProvider**、および **UserAccountProvider** の 3 つのパラメーターを取ります。

**NotificationProvider** パラメーターは特定のシナリオでのみ必要です。 Microsoft Graph の通知を使用する場合は必須です。 今は空のままにしておきます。次のセクションで、ネイティブのプッシュ チャネル経由で受信したユーザー向けの通知をクライアント SDK で処理できるようにする方法を確認してください。

**UserAccountProvider** は、Connected Devices Platform への現在のユーザーのアクセスのための OAuth 2.0 アクセス トークンを配信するために必要です。 これは、アプリの初回実行時と、プラットフォーム管理の更新トークンの有効期限が切れたときに呼び出されます。 

プラットフォームへの開発者のオンボーディング支援をより簡単にするために、Windows 向けのアカウント プロバイダーの実装をサンプル コードで提供しました。詳細については、**MicrosoftAccountProvider.cs** を確認してください。 

次に、**Platform** インスタンスを作成できます。 

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

アプリがフォアグラウンドを終了したら、プラットフォームをシャットダウンする必要があります。

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
