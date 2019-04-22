---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 45aa2364c2b1f7a30e94e2b720a0e4b14d4bff27
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801664"
---
## <a name="preliminary-setup-for-the-connected-devices-platform"></a>接続されているデバイス プラットフォームの暫定的なセットアップ

リモート接続を実装する前に、いくつかの手順にリモート デバイスに接続する機能の Android アプリに付与する必要があります。

### <a name="sign-in"></a>サインイン

Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は Nearby 共有を除く、SDK のすべての機能に必要な Api。 

MSA をあり、1 つを使用する実行されていない、上のレジスタ[account.microsoft.com](https://account.microsoft.com/account)します。

次の手順で次に、Microsoft と、アプリを登録する必要があります、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)(場合は、Microsoft 開発者アカウントがない、1 つを作成する必要があります最初)。 アプリのクライアント ID の文字列を受信する必要があります。後で、これを保存します。 これで、Microsoft のデバイス プラットフォームの接続されているリソースにアクセスするアプリです。 AAD を使用している場合は、次を参照してください。 [Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)については、クライアントの ID 文字列を取得します。

### <a name="add-the-sdk"></a>SDK を追加します。

次のリポジトリの参照を挿入、 *build.gradle*プロジェクトのルートにあるファイル。

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
次の依存関係を次に、挿入、 _build.gradle_プロジェクト フォルダー内にあるファイル。

```Java
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

次には、アクティビティ クラスにライブ接続しているデバイス機能に希望します。 インポート、次の名前空間。

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
