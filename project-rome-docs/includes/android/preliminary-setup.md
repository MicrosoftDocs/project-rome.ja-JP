---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: e2a3dcbff4594a7886a14f90058bb814e85ff39d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909374"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a>接続されているデバイス プラットフォームと通知の暫定的なセットアップ

リモート接続を実装する前に、いくつかの手順にリモート デバイスに接続するだけでなく送信通知を受信し、機能の Android アプリに付与する必要があります。

### <a name="register-your-app"></a>アプリを登録します。

Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、Project ローマ SDK (近くにある共有 Api の中の例外) のほぼすべての機能に必要です。 MSA をあり、1 つを使用する実行されていない、上のレジスタ[account.microsoft.com](https://account.microsoft.com/account)します。

を、選択した認証メソッドを使用する必要があります、にアプリを登録 Microsoft 次の手順で、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)します。 場合は、Microsoft 開発者アカウントがない、1 つを作成する必要があります。

MSA を使用してアプリを登録するときにクライアントの ID 文字列を受信する必要があります。 後で、これを保存します。 これで、Microsoft のデバイス プラットフォームの接続されているリソースにアクセスするアプリです。 AAD を使用している場合は、次を参照してください。 [Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)については、クライアントの ID 文字列を取得します。

### <a name="add-the-sdk"></a>SDK を追加します。

次のリポジトリの参照を挿入、 *build.gradle*プロジェクトのルートにあるファイル。

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
次の依存関係を次に、挿入、 _build.gradle_プロジェクト フォルダー内にあるファイル。

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

プロジェクトの*AndroidManifest.xml*ファイルを内部で次のアクセス許可を追加、`<manifest>`要素 (既に存在するがないとき) 場合。 これにより、インターネットに接続するデバイスで Bluetooth の検出を有効にして、アプリのアクセス許可。

Bluetooth 関連のアクセス許可は、Bluetooth の検出を使用するために必要なだけに注意してください。接続されているデバイス プラットフォームの他の機能は必要ありません。 さらに、`ACCESS_COARSE_LOCATION`は Android Sdk 21 で必要な以降のみです。 以降では、Android Sdk 23、開発者が実行時に場所へのアクセスを許可するユーザーを求めもする必要があります。


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

次には、アクティビティ クラスにライブ接続しているデバイス機能に希望します。 インポートは、次のパッケージ。

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
