---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: cf4bc236-1a9c-4192-b3fe-2d78331316c0
ms.localizationpriority: medium
ms.openlocfilehash: 6de00cdfd4595f67a655a672dc46fea75806a51f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801604"
---
### <a name="add-the-sdk"></a><span data-ttu-id="9e2e4-103">SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-103">Add the SDK</span></span>

<span data-ttu-id="9e2e4-104">IOS アプリに接続されているデバイス プラットフォームを追加する最も簡単な方法を使用して、 [CocoaPods](https://cocoapods.org/)依存関係マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-104">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="9e2e4-105">IOS プロジェクトの移動*Podfile*し、次のエントリを挿入します。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-105">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

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
> <span data-ttu-id="9e2e4-106">CocoaPod を使用するために使用する必要があります、 _.xcworkspace_プロジェクト内のファイル。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-106">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>

## <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="9e2e4-107">接続されたデバイス プラットフォームを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-107">Initialize the Connected Devices platform</span></span>

<span data-ttu-id="9e2e4-108">接続されたデバイスの機能を使用できますが、前に、プラットフォームは、アプリ内で初期化しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-108">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> 

<span data-ttu-id="9e2e4-109">インスタンス化する必要があります、 **MCDPlatform**クラス。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-109">You must instantiate the **MCDPlatform** class.</span></span> <span data-ttu-id="9e2e4-110">**MCDPlatform**の`platformWithAccountProvider:`メソッドは 2 つのパラメーターを受け取ります。 を**MCDUserAccountProvider**と**MCDNotificationProvider**します。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-110">The **MCDPlatform**'s `platformWithAccountProvider:` method takes two parameters: a **MCDUserAccountProvider** and a **MCDNotificationProvider**.</span></span> <span data-ttu-id="9e2e4-111">**MCDNotificationProvider**パラメーターは、リモート アプリのホスト、およびユーザーのアクティビティは、このガイドで扱わないのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-111">The **MCDNotificationProvider** parameter is only needed for remote app hosting and User Activities, which are not covered in this guide.</span></span> <span data-ttu-id="9e2e4-112">ままでかまいません`nil`今のところです。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-112">It can be left `nil` for now.</span></span>

<span data-ttu-id="9e2e4-113">**MCDUserAccountProvider**接続されているデバイス プラットフォームに現在のユーザーのアクセス用の OAuth 2.0 アクセス トークンを提供するが必要です。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-113">The **MCDUserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="9e2e4-114">アプリが実行され、更新トークンのプラットフォームで管理された期限切れには、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-114">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="9e2e4-115">簡単に、プラットフォームをオンボード開発者を支援するために提供していますアカウント Android および iOS 用のプロバイダーの実装。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-115">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="9e2e4-116">これらの実装にある、[認証プロバイダーのサンプル](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample)、OAuth 2.0 アクセス トークンを取得し、アプリのトークンを更新するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-116">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="9e2e4-117">サンプル アプリから次のコードは、プラットフォームの初期化を示しています。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-117">The following code from the sample app shows the initialization of the platform.</span></span>

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

<span data-ttu-id="9e2e4-118">アプリが呼び出すことによって、フォア グラウンドを終了するときに、プラットフォームをシャット ダウン、`shutdownAsync:`メソッド。</span><span class="sxs-lookup"><span data-stu-id="9e2e4-118">Shut down the platform when your app exits the foreground by calling the `shutdownAsync:` method.</span></span>
