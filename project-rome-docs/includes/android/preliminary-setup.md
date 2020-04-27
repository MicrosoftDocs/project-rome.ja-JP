---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b2d1d764c4aae562a1fcafdb490db5a14522cda6
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755749"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a>Connected Devices Platform と通知の準備段階のセットアップ

リモート接続を実装する前に、いくつかの手順を実行して、リモート デバイスへの接続機能と通知の送受信機能を Android アプリに提供する必要があります。

### <a name="register-your-app"></a>アプリの登録

Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、Project Rome SDK のほとんどすべての機能に必要です (例外は近距離共有 API です)。 MSA をまだ所有しておらず、使用したい場合は、[account.microsoft.com](https://account.microsoft.com/account) で登録してください。

> [!NOTE]
> Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。

選択した認証方法を使用して、また[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)の指示に従ってアプリを Microsoft に登録する必要があります。 Microsoft 開発者アカウントがない場合、作成する必要があります。

MSA を使用してアプリを登録したら、クライアント ID 文字列が届くはずです。 これは後で使用しますので、保存しておいてください。 これにより、アプリが Microsoft の Connected Devices Platform リソースにアクセスできるようになります。 AAD を使用している場合は、クライアント ID 文字列を取得する手順について「[Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)」を参照してください。

### <a name="add-the-sdk"></a>SDK の追加

次のリポジトリ参照を、プロジェクトのルートにある *build.gradle* ファイルに挿入します。

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
続いて、次の依存関係を、プロジェクト フォルダーにある _build.gradle_ ファイルに挿入します。

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

プロジェクトの *AndroidManifest.xml* ファイルで、`<manifest>` 要素の内側に次のアクセス許可を追加します (まだ存在しない場合)。 これにより、インターネットに接続して、デバイスで Bluetooth 検出を有効にするためのアクセス許可がアプリに付与されます。

Bluetooth 関連のアクセス許可は、Bluetooth 検出を使用するために必要なだけであり、Connected Devices Platform の他の機能には必要ないことに注意してください。 また、`ACCESS_COARSE_LOCATION` は Android SDK 21 以降でのみ必要です。 Android SDK 23 以降では、開発者はユーザーにプロンプトを表示して実行時に位置情報へのアクセスを許可する必要もあります。


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

次に、Connected Devices 機能を有効にするアクティビティ クラスに移動します。 次のパッケージをインポートします。

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
