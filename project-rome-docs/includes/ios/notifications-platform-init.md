---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: cf4bc236-1a9c-4192-b3fe-2d78331316c0
ms.localizationpriority: medium
ms.openlocfilehash: 6de00cdfd4595f67a655a672dc46fea75806a51f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801604"
---
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

## <a name="initialize-the-connected-devices-platform"></a>接続されたデバイス プラットフォームを初期化します。

接続されたデバイスの機能を使用できますが、前に、プラットフォームは、アプリ内で初期化しなければなりません。 

インスタンス化する必要があります、 **MCDPlatform**クラス。 **MCDPlatform**の`platformWithAccountProvider:`メソッドは 2 つのパラメーターを受け取ります。 を**MCDUserAccountProvider**と**MCDNotificationProvider**します。 **MCDNotificationProvider**パラメーターは、リモート アプリのホスト、およびユーザーのアクティビティは、このガイドで扱わないのみ必要です。 ままでかまいません`nil`今のところです。

**MCDUserAccountProvider**接続されているデバイス プラットフォームに現在のユーザーのアクセス用の OAuth 2.0 アクセス トークンを提供するが必要です。 アプリが実行され、更新トークンのプラットフォームで管理された期限切れには、最初に呼び出されます。 

簡単に、プラットフォームをオンボード開発者を支援するために提供していますアカウント Android および iOS 用のプロバイダーの実装。 これらの実装にある、[認証プロバイダーのサンプル](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample)、OAuth 2.0 アクセス トークンを取得し、アプリのトークンを更新するために使用できます。

[!INCLUDE [auth-scopes](../auth-scopes.md)]

サンプル アプリから次のコードは、プラットフォームの初期化を示しています。

```ObjectiveC
- (void)initializePlatform
{
    // Only register for APNs if this app is enabled for push notifications
    NotificationProvider* notificationProvider;
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        notificationProvider = [AppDataSource sharedInstance].notificationProvider;
    }
    else
    {
        NSLog(@"Initializing platform without a notification provider!");
        notificationProvider = nil;
    }

    // Initialize platform
    [AppDataSource sharedInstance].platform = [MCDPlatform platformWithAccountProvider:[AppDataSource sharedInstance].accountProvider notificationProvider:notificationProvider];

    // ...
}
```

アプリが呼び出すことによって、フォア グラウンドを終了するときに、プラットフォームをシャット ダウン、`shutdownAsync:`メソッド。
