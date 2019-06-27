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
### <a name="add-the-sdk"></a>SDK の追加

次のリポジトリ参照を、プロジェクトのルートにある *build.gradle* ファイルに挿入します。

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
続いて、次の依存関係を、プロジェクト フォルダーにある _build.gradle_ ファイルに挿入します。

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

アプリで ProGuard を使用する場合は、これらの新しい API 用の ProGuard 規則を追加します。 *proguard-rules.txt* という名前のファイルをプロジェクトの *App* フォルダーに作成し、[ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt) の内容を貼り付けます。

プロジェクトの *AndroidManifest.xml* ファイルで、`<manifest>` 要素の内側に次のアクセス許可を追加します (まだ存在しない場合)。 これにより、インターネットに接続して、デバイスで Bluetooth 検出を有効にするためのアクセス許可がアプリに付与されます。

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> Bluetooth 関連のアクセス許可は、Bluetooth 検出を使用するために必要なだけであり、Connected Devices Platform の他の機能には必要ありません。 また、`ACCESS_COARSE_LOCATION` は Android SDK 21 以降でのみ必要です。 Android SDK 23 以降では、開発者はユーザーにプロンプトを表示して実行時に位置情報へのアクセスを許可する必要もあります。

次に、Connected Devices 機能を追加するアクティビティ クラスに移動します。 **connecteddevices** 名前空間をインポートします。

```java
import com.microsoft.connecteddevices.*;
```

実装するシナリオによっては、すべての名前空間が必要とは限りません。 将来、他の Android ネイティブ名前空間の追加が必要になる場合があります。

### <a name="initialize-the-connected-devices-platform"></a>Connected Devices Platform の初期化

Connected Devices の機能を使用できるようになる前に、アプリ内でプラットフォームを初期化する必要があります。 他の Connected Devices のシナリオが実行可能になる前に初期化手順が必要なため、main クラスの **onCreate** または **onResume** メソッドで初期化手順を実行する必要があります。 

**Platform** クラスをインスタンス化する必要があります。 **Platform** のコンストラクターは、アプリの **Context**、**NotificationProvider**、および **UserAccountProvider** の 3 つのパラメーターを取ります。

**NotificationProvider** パラメーターは特定のシナリオでのみ必要です。 Microsoft Graph の通知を使用する場合は必須です。 今は `null` のままにしておきます。ネイティブのプッシュ チャネル経由で受信したユーザー向けの通知をクライアント SDK で処理できるようにする方法について、次のセクションで確認してください。

**UserAccountProvider** は、Connected Devices Platform への現在のユーザーのアクセスのための OAuth 2.0 アクセス トークンを配信するために必要です。 これは、アプリの初回実行時と、プラットフォーム管理の更新トークンの有効期限が切れたときに呼び出されます。 

プラットフォームへの開発者のオンボーディングがもっと簡単になるよう、Android および iOS 用のアカウント プロバイダーの実装を提供しています。 [認証プロバイダーのサンプル](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample)にあるこれらの実装を使用して、アプリ用の OAuth 2.0 アクセス トークンおよび更新トークンを取得できます。

[!INCLUDE [auth-scopes](../auth-scopes.md)]

次のコードでは、`mSignInHelper` は **MSAAccountProvider** を参照し、これも続けて初期化されます。 この提供されたクラスは **UserAccountProvider** インターフェイスを実装します。

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

ここで、**Platform** インスタンスを作成できます。 独立したヘルパー クラスに次のコードを配置したい場合があります。 

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
main クラスで、`mSignInHelper` が初期化される位置に次のコードを追加します。

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

アプリがフォアグラウンドを終了したら、プラットフォームをシャットダウンする必要があります。

```Java
mPlatform.shutdownAsync();
```
