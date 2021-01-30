---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: d0a91c583bda39cdef57adfdcab185e26e08195e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901558"
---
### <a name="register-your-app"></a>アプリの登録

Microsoft アカウント (MSA) または Azure Active Directory (AAD) 認証は、Project Rome SDK のほとんどすべての機能に必要です (例外は近距離共有 API です)。 MSA をまだ所有しておらず、使用したい場合は、[account.microsoft.com](https://account.microsoft.com/account) で登録してください。

> [!NOTE]
> Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。

選択した認証方法を使用して、また[アプリケーション登録ポータル](https://apps.dev.microsoft.com/)の指示に従ってアプリを Microsoft に登録する必要があります。 Microsoft 開発者アカウントがない場合、作成する必要があります。

MSA を使用してアプリを登録したら、クライアント ID 文字列が届くはずです。 これは後で使用しますので、保存しておいてください。 これにより、アプリが Microsoft の Connected Devices Platform リソースにアクセスできるようになります。 AAD を使用している場合は、クライアント ID 文字列を取得する手順について「[Azure Active Directory 認証ライブラリ](/azure/active-directory/develop/active-directory-authentication-libraries)」を参照してください。

### <a name="add-the-sdk"></a>SDK の追加

Connected Devices Platform を iOS アプリに追加する最も簡単な方法は、[CocoaPods](https://cocoapods.org/) 依存関係マネージャーを使用することです。 iOS プロジェクトの *Podfile* に移動し、次のエントリを挿入します。

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
> CocoaPod を利用するためには、プロジェクト内の _.xcworkspace_ ファイルを使用する必要があります。