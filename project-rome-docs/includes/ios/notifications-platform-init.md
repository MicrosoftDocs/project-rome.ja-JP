---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: cf4bc236-1a9c-4192-b3fe-2d78331316c0
ms.localizationpriority: medium
ms.openlocfilehash: 6de00cdfd4595f67a655a672dc46fea75806a51f
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801604"
---
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

## <a name="initialize-the-connected-devices-platform"></a>Connected Devices Platform の初期化

Connected Devices の機能を使用できるようになる前に、アプリ内でプラットフォームを初期化する必要があります。 

**MCDPlatform** クラスをインスタンス化する必要があります。 **MCDPlatform** の `platformWithAccountProvider:` メソッドは、**MCDUserAccountProvider** と **MCDNotificationProvider** の 2 つのパラメーターを取ります。 **MCDNotificationProvider** パラメーターは、リモート アプリ ホスティングおよびユーザー アクティビティのみに必要であり、これらの機能についてはこのガイドでは扱いません。 今のところは `nil` のままでかまいません。

**MCDUserAccountProvider** は、Connected Devices Platform への現在のユーザーのアクセスのための OAuth 2.0 アクセス トークンを配信するために必要です。 これは、アプリの初回実行時と、プラットフォーム管理の更新トークンの有効期限が切れたときに呼び出されます。 

プラットフォームへの開発者のオンボーディングがもっと簡単になるよう、Android および iOS 用のアカウント プロバイダーの実装を提供しています。 [認証プロバイダーのサンプル](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample)にあるこれらの実装を使用して、アプリ用の OAuth 2.0 アクセス トークンおよび更新トークンを取得できます。

[!INCLUDE [auth-scopes](../auth-scopes.md)]

サンプル アプリの次のコードは、プラットフォームの初期化を示しています。

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

アプリがフォアグラウンドを終了したら、`shutdownAsync:` メソッドを呼び出してプラットフォームをシャットダウンします。
