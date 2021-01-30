---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: d0a91c583bda39cdef57adfdcab185e26e08195e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901558"
---
### <a name="register-your-app"></a><span data-ttu-id="49d07-103">アプリの登録</span><span class="sxs-lookup"><span data-stu-id="49d07-103">Register your app</span></span>

<span data-ttu-id="49d07-104">Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、Project Rome SDK のほとんどすべての機能に必要です (例外は近距離共有 API です)。</span><span class="sxs-lookup"><span data-stu-id="49d07-104">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="49d07-105">MSA をまだ所有しておらず、使用したい場合は、[account.microsoft.com](https://account.microsoft.com/account) で登録してください。</span><span class="sxs-lookup"><span data-stu-id="49d07-105">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

> [!NOTE]
> <span data-ttu-id="49d07-106">Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="49d07-106">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="49d07-107">選択した認証方法を使用して、また[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)の指示に従ってアプリを Microsoft に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49d07-107">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="49d07-108">Microsoft 開発者アカウントがない場合、作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49d07-108">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="49d07-109">MSA を使用してアプリを登録したら、クライアント ID 文字列が届くはずです。</span><span class="sxs-lookup"><span data-stu-id="49d07-109">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="49d07-110">これは後で使用しますので、保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="49d07-110">Save this for later.</span></span> <span data-ttu-id="49d07-111">これにより、アプリが Microsoft の Connected Devices Platform リソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="49d07-111">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="49d07-112">AAD を使用している場合は、クライアント ID 文字列を取得する手順について「[Azure Active Directory 認証ライブラリ](/azure/active-directory/develop/active-directory-authentication-libraries)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49d07-112">If you're using AAD, see [Azure Active Directory Authentication Libraries](/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="49d07-113">SDK の追加</span><span class="sxs-lookup"><span data-stu-id="49d07-113">Add the SDK</span></span>

<span data-ttu-id="49d07-114">Connected Devices Platform を iOS アプリに追加する最も簡単な方法は、[CocoaPods](https://cocoapods.org/) 依存関係マネージャーを使用することです。</span><span class="sxs-lookup"><span data-stu-id="49d07-114">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="49d07-115">iOS プロジェクトの *Podfile* に移動し、次のエントリを挿入します。</span><span class="sxs-lookup"><span data-stu-id="49d07-115">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

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
> <span data-ttu-id="49d07-116">CocoaPod を利用するためには、プロジェクト内の _.xcworkspace_ ファイルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49d07-116">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>