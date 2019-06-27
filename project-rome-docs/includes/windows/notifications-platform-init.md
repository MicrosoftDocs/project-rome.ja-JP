---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "58909694"
---
### <a name="add-the-sdk"></a><span data-ttu-id="3ba34-101">SDK の追加</span><span class="sxs-lookup"><span data-stu-id="3ba34-101">Add the SDK</span></span>

<span data-ttu-id="3ba34-102">Windows では、下位レベルのサポート強化と、より柔軟なリリース スケジュールのために、OS 組み込みの Windows SDK の代わりに、Graph Notification SDK が NuGet パッケージを通じて開発者に提供されます。</span><span class="sxs-lookup"><span data-stu-id="3ba34-102">For Windows, Graph Notification SDK is made available to developers through a NuGet package instead of built-in OS Windows SDK in order to have better down-level support and more flexible release schedule.</span></span> <span data-ttu-id="3ba34-103">NuGet パッケージは msgraphsdkteam によって nuget.org で公開されており、[ここ](https://www.nuget.org/profiles/msgraphsdkteam)から入手できます。</span><span class="sxs-lookup"><span data-stu-id="3ba34-103">The NuGet package is published by msgraphsdkteam on nuget.org and can be found [here](https://www.nuget.org/profiles/msgraphsdkteam).</span></span> 

<span data-ttu-id="3ba34-104">UWP アプリから NuGet パッケージをインクルードして使用する方法については、以下のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ba34-104">For more details on including and consuming NuGet packages from your UWP app, please see these links.</span></span> 
* <span data-ttu-id="3ba34-105">[Use packages from nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav) \(nuget.org からのパッケージを使用する\)</span><span class="sxs-lookup"><span data-stu-id="3ba34-105">[Use packages from nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)</span></span>
* [<span data-ttu-id="3ba34-106">クイック スタート: Visual Studio でパッケージをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="3ba34-106">Quickstart: Install and use a package in Visual Studio</span></span>](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




<span data-ttu-id="3ba34-107">実装するシナリオによっては、すべての名前空間が必要とは限りません。</span><span class="sxs-lookup"><span data-stu-id="3ba34-107">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="3ba34-108">特にグラフ通知の場合は、次に示す名前空間が必要です。</span><span class="sxs-lookup"><span data-stu-id="3ba34-108">For Graph Notifications specifically, you will need the below namespaces as shown.</span></span>


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="3ba34-109">Connected Devices Platform の初期化</span><span class="sxs-lookup"><span data-stu-id="3ba34-109">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="3ba34-110">Connected Devices の機能を使用できるようになる前に、アプリ内でプラットフォームを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ba34-110">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="3ba34-111">他の Connected Devices のシナリオが実行可能になる前に初期化手順が必要なため、main クラスの **OnLaunched** または **onActivated** メソッドで初期化手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ba34-111">The initialization steps should occur in your main class' **OnLaunched** or **onActivated** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="3ba34-112">**ConnectedDevicesPlatform** クラスをインスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ba34-112">You must instantiate the **ConnectedDevicesPlatform** class.</span></span> <span data-ttu-id="3ba34-113">**ConnectedDevicesPlatform** コンストラクターは、アプリの **Context**、**NotificationProvider**、および **UserAccountProvider** の 3 つのパラメーターを取ります。</span><span class="sxs-lookup"><span data-stu-id="3ba34-113">The **ConnectedDevicesPlatform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="3ba34-114">**NotificationProvider** パラメーターは特定のシナリオでのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="3ba34-114">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="3ba34-115">Microsoft Graph の通知を使用する場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="3ba34-115">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="3ba34-116">今は空のままにしておきます。次のセクションで、ネイティブのプッシュ チャネル経由で受信したユーザー向けの通知をクライアント SDK で処理できるようにする方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3ba34-116">Leave it empty for now and find out in next section on how to enable the client SDK to handle incoming user-centric notifications via native push channels.</span></span>

<span data-ttu-id="3ba34-117">**UserAccountProvider** は、Connected Devices Platform への現在のユーザーのアクセスのための OAuth 2.0 アクセス トークンを配信するために必要です。</span><span class="sxs-lookup"><span data-stu-id="3ba34-117">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="3ba34-118">これは、アプリの初回実行時と、プラットフォーム管理の更新トークンの有効期限が切れたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3ba34-118">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="3ba34-119">プラットフォームへの開発者のオンボーディング支援をより簡単にするために、Windows 向けのアカウント プロバイダーの実装をサンプル コードで提供しました。詳細については、**MicrosoftAccountProvider.cs** を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3ba34-119">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Windows in sample code, please make sure to check **MicrosoftAccountProvider.cs** for more details.</span></span> 

<span data-ttu-id="3ba34-120">次に、**Platform** インスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3ba34-120">Then you can construct a **Platform** instance.</span></span> 

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

<span data-ttu-id="3ba34-121">アプリがフォアグラウンドを終了したら、プラットフォームをシャットダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ba34-121">You should shut down the platform when your app exits the foreground.</span></span>

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
