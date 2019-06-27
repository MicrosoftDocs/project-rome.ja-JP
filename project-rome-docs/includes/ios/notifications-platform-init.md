---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: cf4bc236-1a9c-4192-b3fe-2d78331316c0
ms.localizationpriority: medium
ms.openlocfilehash: 6de00cdfd4595f67a655a672dc46fea75806a51f
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801604"
---
### <a name="add-the-sdk"></a><span data-ttu-id="01909-103">SDK の追加</span><span class="sxs-lookup"><span data-stu-id="01909-103">Add the SDK</span></span>

<span data-ttu-id="01909-104">Connected Devices Platform を iOS アプリに追加する最も簡単な方法は、[CocoaPods](https://cocoapods.org/) 依存関係マネージャーを使用することです。</span><span class="sxs-lookup"><span data-stu-id="01909-104">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="01909-105">iOS プロジェクトの *Podfile* に移動し、次のエントリを挿入します。</span><span class="sxs-lookup"><span data-stu-id="01909-105">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

```ObjectiveC
platform :ios, "10.0"
workspace 'iOSSample'

target 'iOSSample' do
  # Uncomment the next line if you're using Swift or would like to use dynamic frameworks
  # use_frameworks!

    pod 'ProjectRomeSdk'

  # Pods for iOSSample
```

> [!NOTE]
> <span data-ttu-id="01909-106">CocoaPod を利用するためには、プロジェクト内の _.xcworkspace_ ファイルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01909-106">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>

## <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="01909-107">Connected Devices Platform の初期化</span><span class="sxs-lookup"><span data-stu-id="01909-107">Initialize the Connected Devices platform</span></span>

<span data-ttu-id="01909-108">Connected Devices の機能を使用できるようになる前に、アプリ内でプラットフォームを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01909-108">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> 

<span data-ttu-id="01909-109">**MCDPlatform** クラスをインスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01909-109">You must instantiate the **MCDPlatform** class.</span></span> <span data-ttu-id="01909-110">**MCDPlatform** の `platformWithAccountProvider:` メソッドは、**MCDUserAccountProvider** と **MCDNotificationProvider** の 2 つのパラメーターを取ります。</span><span class="sxs-lookup"><span data-stu-id="01909-110">The **MCDPlatform**'s `platformWithAccountProvider:` method takes two parameters: a **MCDUserAccountProvider** and a **MCDNotificationProvider**.</span></span> <span data-ttu-id="01909-111">**MCDNotificationProvider** パラメーターは、リモート アプリ ホスティングおよびユーザー アクティビティのみに必要であり、これらの機能についてはこのガイドでは扱いません。</span><span class="sxs-lookup"><span data-stu-id="01909-111">The **MCDNotificationProvider** parameter is only needed for remote app hosting and User Activities, which are not covered in this guide.</span></span> <span data-ttu-id="01909-112">今のところは `nil` のままでかまいません。</span><span class="sxs-lookup"><span data-stu-id="01909-112">It can be left `nil` for now.</span></span>

<span data-ttu-id="01909-113">**MCDUserAccountProvider** は、Connected Devices Platform への現在のユーザーのアクセスのための OAuth 2.0 アクセス トークンを配信するために必要です。</span><span class="sxs-lookup"><span data-stu-id="01909-113">The **MCDUserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="01909-114">これは、アプリの初回実行時と、プラットフォーム管理の更新トークンの有効期限が切れたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="01909-114">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="01909-115">プラットフォームへの開発者のオンボーディングがもっと簡単になるよう、Android および iOS 用のアカウント プロバイダーの実装を提供しています。</span><span class="sxs-lookup"><span data-stu-id="01909-115">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="01909-116">[認証プロバイダーのサンプル](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample)にあるこれらの実装を使用して、アプリ用の OAuth 2.0 アクセス トークンおよび更新トークンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="01909-116">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="01909-117">サンプル アプリの次のコードは、プラットフォームの初期化を示しています。</span><span class="sxs-lookup"><span data-stu-id="01909-117">The following code from the sample app shows the initialization of the platform.</span></span>

```ObjectiveC
- (void)initializePlatform
{
    // Only register for APNs if this app is enabled for push notifications
    NotificationProvider* notificationProvider;
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        notificationProvider = [AppDataSource sharedInstance].notificationProvider;
    }
    else
    {
        NSLog(@"Initializing platform without a notification provider!");
        notificationProvider = nil;
    }

    // Initialize platform
    [AppDataSource sharedInstance].platform = [MCDPlatform platformWithAccountProvider:[AppDataSource sharedInstance].accountProvider notificationProvider:notificationProvider];

    // ...
}
```

<span data-ttu-id="01909-118">アプリがフォアグラウンドを終了したら、`shutdownAsync:` メソッドを呼び出してプラットフォームをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="01909-118">Shut down the platform when your app exits the foreground by calling the `shutdownAsync:` method.</span></span>
