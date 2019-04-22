---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 53cbe2ec68785c257341caf110439d535b8f83be
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804500"
---
### <a name="register-your-app"></a><span data-ttu-id="a179e-103">アプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="a179e-103">Register your app</span></span>

<span data-ttu-id="a179e-104">Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、Project ローマ SDK (近くにある共有 Api の中の例外) のほぼすべての機能に必要です。</span><span class="sxs-lookup"><span data-stu-id="a179e-104">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="a179e-105">MSA をあり、1 つを使用する実行されていない、上のレジスタ[account.microsoft.com](https://account.microsoft.com/account)します。</span><span class="sxs-lookup"><span data-stu-id="a179e-105">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="a179e-106">を、選択した認証メソッドを使用する必要があります、にアプリを登録 Microsoft 次の手順で、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)します。</span><span class="sxs-lookup"><span data-stu-id="a179e-106">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="a179e-107">場合は、Microsoft 開発者アカウントがない、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a179e-107">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="a179e-108">MSA を使用してアプリを登録するときにクライアントの ID 文字列を受信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a179e-108">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="a179e-109">後で、これを保存します。</span><span class="sxs-lookup"><span data-stu-id="a179e-109">Save this for later.</span></span> <span data-ttu-id="a179e-110">これで、Microsoft のデバイス プラットフォームの接続されているリソースにアクセスするアプリです。</span><span class="sxs-lookup"><span data-stu-id="a179e-110">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="a179e-111">AAD を使用している場合は、次を参照してください。 [Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)については、クライアントの ID 文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="a179e-111">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="a179e-112">SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="a179e-112">Add the SDK</span></span>

<span data-ttu-id="a179e-113">IOS アプリに接続されているデバイス プラットフォームを追加する最も簡単な方法を使用して、 [CocoaPods](https://cocoapods.org/)依存関係マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="a179e-113">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="a179e-114">IOS プロジェクトの移動*Podfile*し、次のエントリを挿入します。</span><span class="sxs-lookup"><span data-stu-id="a179e-114">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

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
> <span data-ttu-id="a179e-115">CocoaPod を使用するために使用する必要があります、 _.xcworkspace_プロジェクト内のファイル。</span><span class="sxs-lookup"><span data-stu-id="a179e-115">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>
