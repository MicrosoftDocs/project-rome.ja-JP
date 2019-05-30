---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58909694"
---
### <a name="add-the-sdk"></a><span data-ttu-id="af446-101">SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="af446-101">Add the SDK</span></span>

<span data-ttu-id="af446-102">Windows での Graph 通知 SDK が使用できる組み込みの OS の Windows SDK の代わりに NuGet パッケージを使用して、開発者がより下位レベルのサポートとより柔軟なリリース スケジュールするには。</span><span class="sxs-lookup"><span data-stu-id="af446-102">For Windows, Graph Notification SDK is made available to developers through a NuGet package instead of built-in OS Windows SDK in order to have better down-level support and more flexible release schedule.</span></span> <span data-ttu-id="af446-103">NuGet パッケージが nuget.org で msgraphsdkteam によって公開されたを見つかります[ここ](https://www.nuget.org/profiles/msgraphsdkteam)します。</span><span class="sxs-lookup"><span data-stu-id="af446-103">The NuGet package is published by msgraphsdkteam on nuget.org and can be found [here](https://www.nuget.org/profiles/msgraphsdkteam).</span></span> 

<span data-ttu-id="af446-104">など、UWP アプリから NuGet パッケージの使用の詳細については、これらのリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="af446-104">For more details on including and consuming NuGet packages from your UWP app, please see these links.</span></span> 
* [<span data-ttu-id="af446-105">Nuget.org からパッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="af446-105">Use packages from nuget.org</span></span>](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)
* [<span data-ttu-id="af446-106">クイック スタート:インストールして、Visual Studio でパッケージを使用</span><span class="sxs-lookup"><span data-stu-id="af446-106">Quickstart: Install and use a package in Visual Studio</span></span>](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




<span data-ttu-id="af446-107">実装するシナリオ、に応じてを多く必要はありませんすべての名前空間。</span><span class="sxs-lookup"><span data-stu-id="af446-107">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="af446-108">グラフの通知を具体的には、必要があります、次のように名前空間。</span><span class="sxs-lookup"><span data-stu-id="af446-108">For Graph Notifications specifically, you will need the below namespaces as shown.</span></span>


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="af446-109">接続されているデバイス プラットフォームを初期化します。</span><span class="sxs-lookup"><span data-stu-id="af446-109">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="af446-110">接続されたデバイスの機能を使用できますが、前に、プラットフォームは、アプリ内で初期化しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="af446-110">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="af446-111">初期化の手順は、メインのクラスで発生する必要があります**OnLaunched**または**onActivated**メソッド、その他の接続されたデバイス シナリオを実行する前に必要なためです。</span><span class="sxs-lookup"><span data-stu-id="af446-111">The initialization steps should occur in your main class' **OnLaunched** or **onActivated** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="af446-112">インスタンス化する必要があります、 **ConnectedDevicesPlatform**クラス。</span><span class="sxs-lookup"><span data-stu-id="af446-112">You must instantiate the **ConnectedDevicesPlatform** class.</span></span> <span data-ttu-id="af446-113">**ConnectedDevicesPlatform**コンス トラクターは 3 つのパラメーターを受け取ります。**コンテキスト**アプリの場合、 **NotificationProvider**、および**UserAccountProvider**します。</span><span class="sxs-lookup"><span data-stu-id="af446-113">The **ConnectedDevicesPlatform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="af446-114">**NotificationProvider**パラメーターは特定のシナリオでのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="af446-114">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="af446-115">Microsoft Graph の通知を使用する場合が必要です。</span><span class="sxs-lookup"><span data-stu-id="af446-115">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="af446-116">ここでは空のままにし、クライアントのネイティブのプッシュ チャネルを使用してユーザーを中心とした通知の受信を処理するために SDK を有効にする方法に関する次のセクションで詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="af446-116">Leave it empty for now and find out in next section on how to enable the client SDK to handle incoming user-centric notifications via native push channels.</span></span>

<span data-ttu-id="af446-117">**UserAccountProvider**接続されているデバイス プラットフォームに現在のユーザーのアクセス用の OAuth 2.0 アクセス トークンを提供するが必要です。</span><span class="sxs-lookup"><span data-stu-id="af446-117">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="af446-118">アプリが実行され、更新トークンのプラットフォームで管理された期限切れには、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="af446-118">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="af446-119">簡単に、プラットフォームをオンボード開発者を支援するために提供していますアカウント プロバイダーの実装のサンプル コードでの Windows を確認してくださいチェック**MicrosoftAccountProvider.cs**の詳細。</span><span class="sxs-lookup"><span data-stu-id="af446-119">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Windows in sample code, please make sure to check **MicrosoftAccountProvider.cs** for more details.</span></span> 

<span data-ttu-id="af446-120">作成し、**プラットフォーム**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="af446-120">Then you can construct a **Platform** instance.</span></span> 

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

<span data-ttu-id="af446-121">アプリがフォア グラウンドを終了するときは、プラットフォームをシャット ダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="af446-121">You should shut down the platform when your app exits the foreground.</span></span>

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
