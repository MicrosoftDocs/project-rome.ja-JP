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
### <a name="add-the-sdk"></a>SDK を追加します。

次のリポジトリの参照を挿入、 *build.gradle*プロジェクトのルートにあるファイル。

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
次の依存関係を次に、挿入、 _build.gradle_プロジェクト フォルダー内にあるファイル。

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

アプリで ProGuard を使用する場合は、これらの新しい Api の ProGuard のルールを追加します。 という名前のファイルを作成する*proguard rules.txt*で、*アプリ*フォルダー、プロジェクト、および貼り付けの内容の[ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt)します。

プロジェクトの*AndroidManifest.xml*ファイルを内部で次のアクセス許可を追加、`<manifest>`要素 (既に存在するがないとき) 場合。 これにより、インターネットに接続するデバイスで Bluetooth の検出を有効にして、アプリのアクセス許可。

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> Bluetooth 関連のアクセス許可は、Bluetooth の検出を使用するために必要なだけ接続されているデバイス プラットフォームの他の機能は必要ありません。 さらに、`ACCESS_COARSE_LOCATION`は Android Sdk 21 で必要な以降のみです。 以降では、Android Sdk 23、開発者が実行時に場所へのアクセスを許可するユーザーを求めもする必要があります。

次に、接続されたデバイスの機能を追加するには移動もアクティビティ クラスにします。 インポート、 **connecteddevices**名前空間。

```java
import com.microsoft.connecteddevices.*;
```

実装するシナリオ、に応じてを多く必要はありませんすべての名前空間。 またの進行に合わせて他の Android ネイティブ名前空間を追加する必要があります。

### <a name="initialize-the-connected-devices-platform"></a>接続されているデバイス プラットフォームを初期化します。

接続されたデバイスの機能を使用できますが、前に、プラットフォームは、アプリ内で初期化しなければなりません。 初期化の手順は、メインのクラスで発生する必要があります**onCreate**または**onResume**メソッド、その他の接続されたデバイス シナリオを実行する前に必要なためです。 

インスタンス化する必要があります、**プラットフォーム**クラス。 **プラットフォーム**コンス トラクターは 3 つのパラメーターを受け取ります。**コンテキスト**アプリの場合、 **NotificationProvider**、および**UserAccountProvider**.

**NotificationProvider**パラメーターは特定のシナリオでのみ必要です。 Microsoft Graph の通知を使用する場合が必要です。 そのまま使用`null`ここでは、クライアントは次のセクションで、ネイティブのプッシュ チャネルを使用してユーザーを中心とした通知の受信を処理するために SDK を有効にする方法を調べるとします。

**UserAccountProvider**接続されているデバイス プラットフォームに現在のユーザーのアクセス用の OAuth 2.0 アクセス トークンを提供するが必要です。 アプリが実行され、更新トークンのプラットフォームで管理された期限切れには、最初に呼び出されます。 

簡単に、プラットフォームをオンボード開発者を支援するために提供していますアカウント Android および iOS 用のプロバイダーの実装。 これらの実装にある、[認証プロバイダーのサンプル](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample)、OAuth 2.0 アクセス トークンを取得し、アプリのトークンを更新するために使用できます。

[!INCLUDE [auth-scopes](../auth-scopes.md)]

次のコードで`mSignInHelper`参照、 **MSAAccountProvider**、以下も初期化します。 これは、クラスの実装を提供、 **UserAccountProvider**インターフェイス。

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

構築することができますので、**プラットフォーム**インスタンス。 別のヘルパー クラスに次のコードを配置したい場合があります。 

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
メイン クラスで、`mSignInHelper`は初期化するには、次のコードを追加します。

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

アプリがフォア グラウンドを終了するときは、プラットフォームをシャット ダウンする必要があります。

```Java
mPlatform.shutdownAsync();
```
