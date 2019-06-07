---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b979c0b7891aaa6ce5c422d8349809b429a47201
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755762"
---
### <a name="register-your-app"></a>アプリを登録します。

Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、Project ローマ SDK (近くにある共有 Api の中の例外) のほぼすべての機能に必要です。 MSA をあり、1 つを使用する実行されていない、上のレジスタ[account.microsoft.com](https://account.microsoft.com/account)します。

> [!NOTE]
> デバイスの Relay Api では、azure Active Directory (AAD) アカウントはサポートされていません。

を、選択した認証メソッドを使用する必要があります、にアプリを登録 Microsoft 次の手順で、[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)します。 場合は、Microsoft 開発者アカウントがない、1 つを作成する必要があります。

MSA を使用してアプリを登録するときにクライアントの ID 文字列を受信する必要があります。 後で、これを保存します。 これで、Microsoft のデバイス プラットフォームの接続されているリソースにアクセスするアプリです。 AAD を使用している場合は、次を参照してください。 [Azure Active Directory 認証ライブラリ](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries)については、クライアントの ID 文字列を取得します。

### <a name="add-the-sdk"></a>SDK を追加します。

IOS アプリに接続されているデバイス プラットフォームを追加する最も簡単な方法を使用して、 [CocoaPods](https://cocoapods.org/)依存関係マネージャーです。 IOS プロジェクトの移動*Podfile*し、次のエントリを挿入します。

```ObjectiveC
platform :ios, "10.0"
workspace 'iOSSample'

target 'iOSSample' do
  # Uncomment the next line if you're using Swift or would like to use dynamic frameworks
  # use_frameworks!

    pod 'ProjectRomeSdk'

  # Pods for iOSSample
```

> [!NOTE]
> CocoaPod を使用するために使用する必要があります、 _.xcworkspace_プロジェクト内のファイル。
