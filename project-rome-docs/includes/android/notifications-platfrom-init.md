---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 9f679e13-b1b3-40f8-bd44-679e4dffc0d4
ms.localizationpriority: medium
ms.openlocfilehash: eafd435f0cd9eabc5aa121cdb5288bd0b522df60
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801797"
---
### <a name="add-the-sdk"></a><span data-ttu-id="4402c-103">SDK の追加</span><span class="sxs-lookup"><span data-stu-id="4402c-103">Add the SDK</span></span>

<span data-ttu-id="4402c-104">次のリポジトリ参照を、プロジェクトのルートにある *build.gradle* ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="4402c-104">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="4402c-105">続いて、次の依存関係を、プロジェクト フォルダーにある _build.gradle_ ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="4402c-105">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="4402c-106">アプリで ProGuard を使用する場合は、これらの新しい API 用の ProGuard 規則を追加します。</span><span class="sxs-lookup"><span data-stu-id="4402c-106">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="4402c-107">*proguard-rules.txt* という名前のファイルをプロジェクトの *App* フォルダーに作成し、[ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt) の内容を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="4402c-107">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="4402c-108">プロジェクトの *AndroidManifest.xml* ファイルで、`<manifest>` 要素の内側に次のアクセス許可を追加します (まだ存在しない場合)。</span><span class="sxs-lookup"><span data-stu-id="4402c-108">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="4402c-109">これにより、インターネットに接続して、デバイスで Bluetooth 検出を有効にするためのアクセス許可がアプリに付与されます。</span><span class="sxs-lookup"><span data-stu-id="4402c-109">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="4402c-110">Bluetooth 関連のアクセス許可は、Bluetooth 検出を使用するために必要なだけであり、Connected Devices Platform の他の機能には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4402c-110">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="4402c-111">また、`ACCESS_COARSE_LOCATION` は Android SDK 21 以降でのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="4402c-111">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="4402c-112">Android SDK 23 以降では、開発者はユーザーにプロンプトを表示して実行時に位置情報へのアクセスを許可する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="4402c-112">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="4402c-113">次に、Connected Devices 機能を追加するアクティビティ クラスに移動します。</span><span class="sxs-lookup"><span data-stu-id="4402c-113">Next, go to the activity class(es) where you would like to add the Connected Devices functionality.</span></span> <span data-ttu-id="4402c-114">**connecteddevices** 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="4402c-114">Import the **connecteddevices** namespaces.</span></span>

```java
import com.microsoft.connecteddevices.*;
```

<span data-ttu-id="4402c-115">実装するシナリオによっては、すべての名前空間が必要とは限りません。</span><span class="sxs-lookup"><span data-stu-id="4402c-115">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="4402c-116">将来、他の Android ネイティブ名前空間の追加が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4402c-116">You may also need to add other Android-native namespaces as you progress.</span></span>

### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="4402c-117">Connected Devices Platform の初期化</span><span class="sxs-lookup"><span data-stu-id="4402c-117">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="4402c-118">Connected Devices の機能を使用できるようになる前に、アプリ内でプラットフォームを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4402c-118">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="4402c-119">他の Connected Devices のシナリオが実行可能になる前に初期化手順が必要なため、main クラスの **onCreate** または **onResume** メソッドで初期化手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4402c-119">The initialization steps should occur in your main class' **onCreate** or **onResume** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="4402c-120">**Platform** クラスをインスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4402c-120">You must instantiate the **Platform** class.</span></span> <span data-ttu-id="4402c-121">**Platform** のコンストラクターは、アプリの **Context**、**NotificationProvider**、および **UserAccountProvider** の 3 つのパラメーターを取ります。</span><span class="sxs-lookup"><span data-stu-id="4402c-121">The **Platform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="4402c-122">**NotificationProvider** パラメーターは特定のシナリオでのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="4402c-122">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="4402c-123">Microsoft Graph の通知を使用する場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="4402c-123">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="4402c-124">今は `null` のままにしておきます。ネイティブのプッシュ チャネル経由で受信したユーザー向けの通知をクライアント SDK で処理できるようにする方法について、次のセクションで確認してください。</span><span class="sxs-lookup"><span data-stu-id="4402c-124">Leave it as `null` for now and find out how to enable the client SDK to handle incoming user-centric notifications via native push channels in next section.</span></span>

<span data-ttu-id="4402c-125">**UserAccountProvider** は、Connected Devices Platform への現在のユーザーのアクセスのための OAuth 2.0 アクセス トークンを配信するために必要です。</span><span class="sxs-lookup"><span data-stu-id="4402c-125">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="4402c-126">これは、アプリの初回実行時と、プラットフォーム管理の更新トークンの有効期限が切れたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4402c-126">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="4402c-127">プラットフォームへの開発者のオンボーディングがもっと簡単になるよう、Android および iOS 用のアカウント プロバイダーの実装を提供しています。</span><span class="sxs-lookup"><span data-stu-id="4402c-127">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="4402c-128">[認証プロバイダーのサンプル](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample)にあるこれらの実装を使用して、アプリ用の OAuth 2.0 アクセス トークンおよび更新トークンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="4402c-128">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="4402c-129">次のコードでは、`mSignInHelper` は **MSAAccountProvider** を参照し、これも続けて初期化されます。</span><span class="sxs-lookup"><span data-stu-id="4402c-129">In the code below, `mSignInHelper` references an **MSAAccountProvider**, also initialized below.</span></span> <span data-ttu-id="4402c-130">この提供されたクラスは **UserAccountProvider** インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="4402c-130">This provided class implements the **UserAccountProvider** interface.</span></span>

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

<span data-ttu-id="4402c-131">ここで、**Platform** インスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4402c-131">Now you can construct a **Platform** instance.</span></span> <span data-ttu-id="4402c-132">独立したヘルパー クラスに次のコードを配置したい場合があります。</span><span class="sxs-lookup"><span data-stu-id="4402c-132">You may wish to put the following code in a separate helper class.</span></span> 

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
<span data-ttu-id="4402c-133">main クラスで、`mSignInHelper` が初期化される位置に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="4402c-133">In your main class, where `mSignInHelper` is initialized, add the following code.</span></span>

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

<span data-ttu-id="4402c-134">アプリがフォアグラウンドを終了したら、プラットフォームをシャットダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4402c-134">You should shut down the platform when your app exits the foreground.</span></span>

```Java
mPlatform.shutdownAsync();
```
