---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 9f679e13-b1b3-40f8-bd44-679e4dffc0d4
ms.localizationpriority: medium
ms.openlocfilehash: eafd435f0cd9eabc5aa121cdb5288bd0b522df60
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907154"
---
### <a name="add-the-sdk"></a><span data-ttu-id="bc328-103">SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="bc328-103">Add the SDK</span></span>

<span data-ttu-id="bc328-104">次のリポジトリの参照を挿入、 *build.gradle*プロジェクトのルートにあるファイル。</span><span class="sxs-lookup"><span data-stu-id="bc328-104">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="bc328-105">次の依存関係を次に、挿入、 _build.gradle_プロジェクト フォルダー内にあるファイル。</span><span class="sxs-lookup"><span data-stu-id="bc328-105">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="bc328-106">アプリで ProGuard を使用する場合は、これらの新しい Api の ProGuard のルールを追加します。</span><span class="sxs-lookup"><span data-stu-id="bc328-106">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="bc328-107">という名前のファイルを作成する*proguard rules.txt*で、*アプリ*フォルダー、プロジェクト、および貼り付けの内容の[ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt)します。</span><span class="sxs-lookup"><span data-stu-id="bc328-107">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="bc328-108">プロジェクトの*AndroidManifest.xml*ファイルを内部で次のアクセス許可を追加、`<manifest>`要素 (既に存在するがないとき) 場合。</span><span class="sxs-lookup"><span data-stu-id="bc328-108">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="bc328-109">これにより、インターネットに接続するデバイスで Bluetooth の検出を有効にして、アプリのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="bc328-109">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="bc328-110">Bluetooth 関連のアクセス許可は、Bluetooth の検出を使用するために必要なだけ接続されているデバイス プラットフォームの他の機能は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="bc328-110">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="bc328-111">さらに、`ACCESS_COARSE_LOCATION`は Android Sdk 21 で必要な以降のみです。</span><span class="sxs-lookup"><span data-stu-id="bc328-111">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="bc328-112">以降では、Android Sdk 23、開発者が実行時に場所へのアクセスを許可するユーザーを求めもする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc328-112">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="bc328-113">次に、接続されたデバイスの機能を追加するには移動もアクティビティ クラスにします。</span><span class="sxs-lookup"><span data-stu-id="bc328-113">Next, go to the activity class(es) where you would like to add the Connected Devices functionality.</span></span> <span data-ttu-id="bc328-114">インポート、 **connecteddevices**名前空間。</span><span class="sxs-lookup"><span data-stu-id="bc328-114">Import the **connecteddevices** namespaces.</span></span>

```java
import com.microsoft.connecteddevices.*;
```

<span data-ttu-id="bc328-115">実装するシナリオ、に応じてを多く必要はありませんすべての名前空間。</span><span class="sxs-lookup"><span data-stu-id="bc328-115">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="bc328-116">またの進行に合わせて他の Android ネイティブ名前空間を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc328-116">You may also need to add other Android-native namespaces as you progress.</span></span>

### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="bc328-117">接続されているデバイス プラットフォームを初期化します。</span><span class="sxs-lookup"><span data-stu-id="bc328-117">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="bc328-118">接続されたデバイスの機能を使用できますが、前に、プラットフォームは、アプリ内で初期化しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="bc328-118">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="bc328-119">初期化の手順は、メインのクラスで発生する必要があります**onCreate**または**onResume**メソッド、その他の接続されたデバイス シナリオを実行する前に必要なためです。</span><span class="sxs-lookup"><span data-stu-id="bc328-119">The initialization steps should occur in your main class' **onCreate** or **onResume** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="bc328-120">インスタンス化する必要があります、**プラットフォーム**クラス。</span><span class="sxs-lookup"><span data-stu-id="bc328-120">You must instantiate the **Platform** class.</span></span> <span data-ttu-id="bc328-121">**プラットフォーム**コンス トラクターは 3 つのパラメーターを受け取ります。**コンテキスト**アプリの場合、 **NotificationProvider**、および**UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="bc328-121">The **Platform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="bc328-122">**NotificationProvider**パラメーターは特定のシナリオでのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="bc328-122">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="bc328-123">Microsoft Graph の通知を使用する場合が必要です。</span><span class="sxs-lookup"><span data-stu-id="bc328-123">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="bc328-124">そのまま使用`null`ここでは、クライアントは次のセクションで、ネイティブのプッシュ チャネルを使用してユーザーを中心とした通知の受信を処理するために SDK を有効にする方法を調べるとします。</span><span class="sxs-lookup"><span data-stu-id="bc328-124">Leave it as `null` for now and find out how to enable the client SDK to handle incoming user-centric notifications via native push channels in next section.</span></span>

<span data-ttu-id="bc328-125">**UserAccountProvider**接続されているデバイス プラットフォームに現在のユーザーのアクセス用の OAuth 2.0 アクセス トークンを提供するが必要です。</span><span class="sxs-lookup"><span data-stu-id="bc328-125">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="bc328-126">アプリが実行され、更新トークンのプラットフォームで管理された期限切れには、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bc328-126">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="bc328-127">簡単に、プラットフォームをオンボード開発者を支援するために提供していますアカウント Android および iOS 用のプロバイダーの実装。</span><span class="sxs-lookup"><span data-stu-id="bc328-127">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="bc328-128">これらの実装にある、[認証プロバイダーのサンプル](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample)、OAuth 2.0 アクセス トークンを取得し、アプリのトークンを更新するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="bc328-128">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="bc328-129">次のコードで`mSignInHelper`参照、 **MSAAccountProvider**、以下も初期化します。</span><span class="sxs-lookup"><span data-stu-id="bc328-129">In the code below, `mSignInHelper` references an **MSAAccountProvider**, also initialized below.</span></span> <span data-ttu-id="bc328-130">これは、クラスの実装を提供、 **UserAccountProvider**インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="bc328-130">This provided class implements the **UserAccountProvider** interface.</span></span>

```java
private MSAAccountProvider mSignInHelper;

// ...

// Create sign-in helper from helper lib, which does user account and access token management for us
// Takes two parameters: a client id for msa, and the Context
mSignInHelper = new MSAAccountProvider(Secrets.MSA_CLIENT_ID, getContext());

// add an event listener, which changes the button text when account state changes
mSignInHelper.addUserAccountChangedListener(new EventListener<UserAccountProvider, Void>() {
    @Override
    public void onEvent(UserAccountProvider provider, Void aVoid){
        if (mSignInHelper.isSignedIn()) {
            // update the UI indicating a user is signed in.
        }
        else
        {
            // update the UI indicating a user is not signed in.
        }
    }
});
```

<span data-ttu-id="bc328-131">構築することができますので、**プラットフォーム**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="bc328-131">Now you can construct a **Platform** instance.</span></span> <span data-ttu-id="bc328-132">別のヘルパー クラスに次のコードを配置したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="bc328-132">You may wish to put the following code in a separate helper class.</span></span> 

```java
// Platform helper class:

private static Platform sPlatform;

//...

// This is the main Platform-generating method
public static synchronized Platform getOrCreatePlatform(Context context, UserAccountProvider accountProvider, NotificationProvider notificationProvider) {
    // check whether the local platform variable is already initialized.
    Platform platform = getPlatform();

    if (platform == null) {
        // if it is not initialized, do so:
        platform = createPlatform(context, accountProvider, notificationProvider);
    }
    return platform;
}

// gets the local platform variable
public static synchronized Platform getPlatform() {
        return sPlatform;
}

// creates and returns a new Platform instance
public static synchronized Platform createPlatform(Context context, UserAccountProvider accountProvider, NotificationProvider notificationProvider) {
    sPlatform = new Platform(context, accountProvider, notificationProvider);
    return sPlatform;
}
```
<span data-ttu-id="bc328-133">メイン クラスで、`mSignInHelper`は初期化するには、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="bc328-133">In your main class, where `mSignInHelper` is initialized, add the following code.</span></span>

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

<span data-ttu-id="bc328-134">アプリがフォア グラウンドを終了するときは、プラットフォームをシャット ダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bc328-134">You should shut down the platform when your app exits the foreground.</span></span>

```Java
mPlatform.shutdownAsync();
```
