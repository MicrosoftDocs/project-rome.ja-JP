---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 45aa2364c2b1f7a30e94e2b720a0e4b14d4bff27
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907794"
---
## <a name="preliminary-setup-for-the-connected-devices-platform"></a><span data-ttu-id="5d0f9-103">接続されているデバイス プラットフォームの暫定的なセットアップ</span><span class="sxs-lookup"><span data-stu-id="5d0f9-103">Preliminary setup for the Connected Devices Platform</span></span>

<span data-ttu-id="5d0f9-104">リモート接続を実装する前に、いくつかの手順にリモート デバイスに接続する機能の Android アプリに付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices.</span></span>

### <a name="sign-in"></a><span data-ttu-id="5d0f9-105">サインイン</span><span class="sxs-lookup"><span data-stu-id="5d0f9-105">Sign-in</span></span>

<span data-ttu-id="5d0f9-106">Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は Nearby 共有を除く、SDK のすべての機能に必要な Api。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for all features of the SDK, except for the Nearby sharing APIs.</span></span> 

<span data-ttu-id="5d0f9-107">MSA をあり、1 つを使用する実行されていない、上のレジスタ[account.microsoft.com](https://account.microsoft.com/account)します。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="5d0f9-108">次の手順で次に、Microsoft と、アプリを登録する必要があります、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)(場合は、Microsoft 開発者アカウントがない、1 つを作成する必要があります最初)。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-108">Next, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="5d0f9-109">アプリのクライアント ID の文字列を受信する必要があります。後で、これを保存します。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-109">You should receive a client ID string for your app; save this for later.</span></span> <span data-ttu-id="5d0f9-110">これで、Microsoft のデバイス プラットフォームの接続されているリソースにアクセスするアプリです。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-110">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="5d0f9-111">AAD を使用している場合は、次を参照してください。 [Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)については、クライアントの ID 文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-111">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="5d0f9-112">SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-112">Add the SDK</span></span>

<span data-ttu-id="5d0f9-113">次のリポジトリの参照を挿入、 *build.gradle*プロジェクトのルートにあるファイル。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-113">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="5d0f9-114">次の依存関係を次に、挿入、 _build.gradle_プロジェクト フォルダー内にあるファイル。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-114">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="5d0f9-115">アプリで ProGuard を使用する場合は、これらの新しい Api の ProGuard のルールを追加します。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-115">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="5d0f9-116">という名前のファイルを作成する*proguard rules.txt*で、*アプリ*フォルダー、プロジェクト、および貼り付けの内容の[ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt)します。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-116">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="5d0f9-117">プロジェクトの*AndroidManifest.xml*ファイルを内部で次のアクセス許可を追加、`<manifest>`要素 (既に存在するがないとき) 場合。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-117">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="5d0f9-118">これにより、インターネットに接続するデバイスで Bluetooth の検出を有効にして、アプリのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-118">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="5d0f9-119">Bluetooth 関連のアクセス許可は、Bluetooth の検出を使用するために必要なだけ接続されているデバイス プラットフォームの他の機能は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-119">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="5d0f9-120">さらに、`ACCESS_COARSE_LOCATION`は Android Sdk 21 で必要な以降のみです。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-120">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="5d0f9-121">以降では、Android Sdk 23、開発者が実行時に場所へのアクセスを許可するユーザーを求めもする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-121">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="5d0f9-122">次には、アクティビティ クラスにライブ接続しているデバイス機能に希望します。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-122">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="5d0f9-123">インポート、次の名前空間。</span><span class="sxs-lookup"><span data-stu-id="5d0f9-123">Import the the following namespaces.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
