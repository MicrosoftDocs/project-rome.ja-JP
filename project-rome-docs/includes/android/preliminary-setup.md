---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b2d1d764c4aae562a1fcafdb490db5a14522cda6
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755749"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="179d4-103">Connected Devices Platform と通知の準備段階のセットアップ</span><span class="sxs-lookup"><span data-stu-id="179d4-103">Preliminary setup for the Connected Devices Platform and Notifications</span></span>

<span data-ttu-id="179d4-104">リモート接続を実装する前に、いくつかの手順を実行して、リモート デバイスへの接続機能と通知の送受信機能を Android アプリに提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="179d4-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices as well as send and receive notifications.</span></span>

### <a name="register-your-app"></a><span data-ttu-id="179d4-105">アプリの登録</span><span class="sxs-lookup"><span data-stu-id="179d4-105">Register your app</span></span>

<span data-ttu-id="179d4-106">Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、Project Rome SDK のほとんどすべての機能に必要です (例外は近距離共有 API です)。</span><span class="sxs-lookup"><span data-stu-id="179d4-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="179d4-107">MSA をまだ所有しておらず、使用したい場合は、[account.microsoft.com](https://account.microsoft.com/account) で登録してください。</span><span class="sxs-lookup"><span data-stu-id="179d4-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

> [!NOTE]
> <span data-ttu-id="179d4-108">Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="179d4-108">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="179d4-109">選択した認証方法を使用して、また[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)の指示に従ってアプリを Microsoft に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="179d4-109">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="179d4-110">Microsoft 開発者アカウントがない場合、作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="179d4-110">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="179d4-111">MSA を使用してアプリを登録したら、クライアント ID 文字列が届くはずです。</span><span class="sxs-lookup"><span data-stu-id="179d4-111">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="179d4-112">これは後で使用しますので、保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="179d4-112">Save this for later.</span></span> <span data-ttu-id="179d4-113">これにより、アプリが Microsoft の Connected Devices Platform リソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="179d4-113">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="179d4-114">AAD を使用している場合は、クライアント ID 文字列を取得する手順について「[Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="179d4-114">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="179d4-115">SDK の追加</span><span class="sxs-lookup"><span data-stu-id="179d4-115">Add the SDK</span></span>

<span data-ttu-id="179d4-116">次のリポジトリ参照を、プロジェクトのルートにある *build.gradle* ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="179d4-116">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
<span data-ttu-id="179d4-117">続いて、次の依存関係を、プロジェクト フォルダーにある _build.gradle_ ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="179d4-117">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

<span data-ttu-id="179d4-118">プロジェクトの *AndroidManifest.xml* ファイルで、`<manifest>` 要素の内側に次のアクセス許可を追加します (まだ存在しない場合)。</span><span class="sxs-lookup"><span data-stu-id="179d4-118">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="179d4-119">これにより、インターネットに接続して、デバイスで Bluetooth 検出を有効にするためのアクセス許可がアプリに付与されます。</span><span class="sxs-lookup"><span data-stu-id="179d4-119">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

<span data-ttu-id="179d4-120">Bluetooth 関連のアクセス許可は、Bluetooth 検出を使用するために必要なだけであり、Connected Devices Platform の他の機能には必要ないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="179d4-120">Note that the Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="179d4-121">また、`ACCESS_COARSE_LOCATION` は Android SDK 21 以降でのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="179d4-121">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="179d4-122">Android SDK 23 以降では、開発者はユーザーにプロンプトを表示して実行時に位置情報へのアクセスを許可する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="179d4-122">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

<span data-ttu-id="179d4-123">次に、Connected Devices 機能を有効にするアクティビティ クラスに移動します。</span><span class="sxs-lookup"><span data-stu-id="179d4-123">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="179d4-124">次のパッケージをインポートします。</span><span class="sxs-lookup"><span data-stu-id="179d4-124">Import the the following packages.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
