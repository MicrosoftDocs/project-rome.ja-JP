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
## <a name="preliminary-setup-for-the-connected-devices-platform"></a>Connected Devices Platform の準備段階のセットアップ

リモート接続を実装する前に、いくつかの手順を実行して、リモート デバイスへの接続機能を Android アプリに提供する必要があります。

### <a name="sign-in"></a>サインイン

Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、近距離共有 API を除いた SDK のすべての機能に必要です。 

MSA をまだ所有しておらず、使用したい場合は、[account.microsoft.com](https://account.microsoft.com/account) で登録してください。

次に、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)の指示に従って、アプリを Microsoft に登録する必要があります (Microsoft 開発者アカウントを所有していない場合は、最初に作成する必要があります)。 アプリのクライアント ID 文字列を受け取ります。これは、保存しておいて後で使用します。 これにより、アプリが Microsoft の Connected Devices Platform リソースにアクセスできるようになります。 AAD を使用している場合は、クライアント ID 文字列を取得する手順について「[Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)」を参照してください。

### <a name="add-the-sdk"></a>SDK の追加

次のリポジトリ参照を、プロジェクトのルートにある *build.gradle* ファイルに挿入します。

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
続いて、次の依存関係を、プロジェクト フォルダーにある _build.gradle_ ファイルに挿入します。

```Java
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

次に、Connected Devices 機能を有効にするアクティビティ クラスに移動します。 次の名前空間をインポートします。

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
