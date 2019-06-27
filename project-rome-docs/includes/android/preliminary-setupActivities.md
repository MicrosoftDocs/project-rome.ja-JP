---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 45aa2364c2b1f7a30e94e2b720a0e4b14d4bff27
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801664"
---
## <a name="preliminary-setup-for-the-connected-devices-platform"></a><span data-ttu-id="745fb-103">Connected Devices Platform の準備段階のセットアップ</span><span class="sxs-lookup"><span data-stu-id="745fb-103">Preliminary setup for the Connected Devices Platform</span></span>

<span data-ttu-id="745fb-104">リモート接続を実装する前に、いくつかの手順を実行して、リモート デバイスへの接続機能を Android アプリに提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="745fb-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices.</span></span>

### <a name="sign-in"></a><span data-ttu-id="745fb-105">サインイン</span><span class="sxs-lookup"><span data-stu-id="745fb-105">Sign-in</span></span>

<span data-ttu-id="745fb-106">Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、近距離共有 API を除いた SDK のすべての機能に必要です。</span><span class="sxs-lookup"><span data-stu-id="745fb-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for all features of the SDK, except for the Nearby sharing APIs.</span></span> 

<span data-ttu-id="745fb-107">MSA をまだ所有しておらず、使用したい場合は、[account.microsoft.com](https://account.microsoft.com/account) で登録してください。</span><span class="sxs-lookup"><span data-stu-id="745fb-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="745fb-108">次に、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)の指示に従って、アプリを Microsoft に登録する必要があります (Microsoft 開発者アカウントを所有していない場合は、最初に作成する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="745fb-108">Next, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="745fb-109">アプリのクライアント ID 文字列を受け取ります。これは、保存しておいて後で使用します。</span><span class="sxs-lookup"><span data-stu-id="745fb-109">You should receive a client ID string for your app; save this for later.</span></span> <span data-ttu-id="745fb-110">これにより、アプリが Microsoft の Connected Devices Platform リソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="745fb-110">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="745fb-111">AAD を使用している場合は、クライアント ID 文字列を取得する手順について「[Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="745fb-111">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="745fb-112">SDK の追加</span><span class="sxs-lookup"><span data-stu-id="745fb-112">Add the SDK</span></span>

<span data-ttu-id="745fb-113">次のリポジトリ参照を、プロジェクトのルートにある *build.gradle* ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="745fb-113">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="745fb-114">続いて、次の依存関係を、プロジェクト フォルダーにある _build.gradle_ ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="745fb-114">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="745fb-115">アプリで ProGuard を使用する場合は、これらの新しい API 用の ProGuard 規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="745fb-115">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="745fb-116">*proguard-rules.txt* という名前のファイルをプロジェクトの *App* フォルダーに作成し、[ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt) の内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="745fb-116">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="745fb-117">プロジェクトの *AndroidManifest.xml* ファイルで、`<manifest>` 要素の内側に次のアクセス許可を追加します (まだ存在しない場合)。</span><span class="sxs-lookup"><span data-stu-id="745fb-117">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="745fb-118">これにより、インターネットに接続して、デバイスで Bluetooth 検出を有効にするためのアクセス許可がアプリに付与されます。</span><span class="sxs-lookup"><span data-stu-id="745fb-118">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="745fb-119">Bluetooth 関連のアクセス許可は、Bluetooth 検出を使用するために必要なだけであり、Connected Devices Platform の他の機能には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="745fb-119">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="745fb-120">また、`ACCESS_COARSE_LOCATION` は Android SDK 21 以降でのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="745fb-120">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="745fb-121">Android SDK 23 以降では、開発者はユーザーにプロンプトを表示して実行時に位置情報へのアクセスを許可する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="745fb-121">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="745fb-122">次に、Connected Devices 機能を有効にするアクティビティ クラスに移動します。</span><span class="sxs-lookup"><span data-stu-id="745fb-122">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="745fb-123">次の名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="745fb-123">Import the the following namespaces.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
