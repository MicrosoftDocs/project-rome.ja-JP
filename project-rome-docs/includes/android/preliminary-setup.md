---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: e2a3dcbff4594a7886a14f90058bb814e85ff39d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804497"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="4a6be-103">接続されているデバイス プラットフォームと通知の暫定的なセットアップ</span><span class="sxs-lookup"><span data-stu-id="4a6be-103">Preliminary setup for the Connected Devices Platform and Notifications</span></span>

<span data-ttu-id="4a6be-104">リモート接続を実装する前に、いくつかの手順にリモート デバイスに接続するだけでなく送信通知を受信し、機能の Android アプリに付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a6be-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices as well as send and receive notifications.</span></span>

### <a name="register-your-app"></a><span data-ttu-id="4a6be-105">アプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="4a6be-105">Register your app</span></span>

<span data-ttu-id="4a6be-106">Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、Project ローマ SDK (近くにある共有 Api の中の例外) のほぼすべての機能に必要です。</span><span class="sxs-lookup"><span data-stu-id="4a6be-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="4a6be-107">MSA をあり、1 つを使用する実行されていない、上のレジスタ[account.microsoft.com](https://account.microsoft.com/account)します。</span><span class="sxs-lookup"><span data-stu-id="4a6be-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="4a6be-108">を、選択した認証メソッドを使用する必要があります、にアプリを登録 Microsoft 次の手順で、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)します。</span><span class="sxs-lookup"><span data-stu-id="4a6be-108">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="4a6be-109">場合は、Microsoft 開発者アカウントがない、1 つを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a6be-109">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="4a6be-110">MSA を使用してアプリを登録するときにクライアントの ID 文字列を受信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a6be-110">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="4a6be-111">後で、これを保存します。</span><span class="sxs-lookup"><span data-stu-id="4a6be-111">Save this for later.</span></span> <span data-ttu-id="4a6be-112">これで、Microsoft のデバイス プラットフォームの接続されているリソースにアクセスするアプリです。</span><span class="sxs-lookup"><span data-stu-id="4a6be-112">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="4a6be-113">AAD を使用している場合は、次を参照してください。 [Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)については、クライアントの ID 文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="4a6be-113">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="4a6be-114">SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="4a6be-114">Add the SDK</span></span>

<span data-ttu-id="4a6be-115">次のリポジトリの参照を挿入、 *build.gradle*プロジェクトのルートにあるファイル。</span><span class="sxs-lookup"><span data-stu-id="4a6be-115">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
<span data-ttu-id="4a6be-116">次の依存関係を次に、挿入、 _build.gradle_プロジェクト フォルダー内にあるファイル。</span><span class="sxs-lookup"><span data-stu-id="4a6be-116">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

<span data-ttu-id="4a6be-117">プロジェクトの*AndroidManifest.xml*ファイルを内部で次のアクセス許可を追加、`<manifest>`要素 (既に存在するがないとき) 場合。</span><span class="sxs-lookup"><span data-stu-id="4a6be-117">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="4a6be-118">これにより、インターネットに接続するデバイスで Bluetooth の検出を有効にして、アプリのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="4a6be-118">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

<span data-ttu-id="4a6be-119">Bluetooth 関連のアクセス許可は、Bluetooth の検出を使用するために必要なだけに注意してください。接続されているデバイス プラットフォームの他の機能は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4a6be-119">Note that the Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="4a6be-120">さらに、`ACCESS_COARSE_LOCATION`は Android Sdk 21 で必要な以降のみです。</span><span class="sxs-lookup"><span data-stu-id="4a6be-120">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="4a6be-121">以降では、Android Sdk 23、開発者が実行時に場所へのアクセスを許可するユーザーを求めもする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a6be-121">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

<span data-ttu-id="4a6be-122">次には、アクティビティ クラスにライブ接続しているデバイス機能に希望します。</span><span class="sxs-lookup"><span data-stu-id="4a6be-122">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="4a6be-123">インポートは、次のパッケージ。</span><span class="sxs-lookup"><span data-stu-id="4a6be-123">Import the the following packages.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
