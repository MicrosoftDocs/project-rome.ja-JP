---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 0ac6a543cc63be9154e40482e587a8f373f56798
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755803"
---
### <a name="create-the-platform"></a>プラットフォームの作成


開始するには、単純にプラットフォームをインスタンス化します。

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>ユーザー アカウントを処理するための ConnectedDevicesAccountManager イベントに登録する 

プラットフォームは、認証済みのユーザーがプラットフォームにアクセスすることを要求します。  有効なアカウントが使用されていることを保証するために、**ConnectedDevicesAccountManager** イベントに登録する必要があります。 

```Java
 ConnectedDevicesPlatform sPlatform.getAccountManager().accessTokenRequested().subscribe((accountManager, args) -> {

    // Get access token
}
```

```Java
 ConnectedDevicesPlatform sPlatform.getAccountManager().accessTokenInvalidated().subscribe((accountManager, args) -> {

    // Refresh and renew existing access token
}
```


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a>ConnectedDevicesNotificationRegistrationManager イベントに登録する

同様に、プラットフォームは通知を使用してデバイス間でコマンドを配信します。  したがって、使用されているアカウントに対してクラウドの登録状態が有効であることを保証するために、**ConnectedDevicesNotificationRegistrationManager** イベントに登録する必要があります。  **ConnectedDevicesNotificationRegistrationState** を使用して状態を確認する

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a>プラットフォームの開始
プラットフォームが初期化され、イベント ハンドラーが配置されたので、リモート システム デバイスの検出を開始する準備ができました。  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a>アプリが認識しているユーザー アカウントの取得

アプリが認識しているユーザー アカウントの一覧を、確実に **ConnectedDevicesAccountManager** と正しく同期することが重要です。

**ConnectedDevicesAccountManager.addAccountAsync** を使用して新しいユーザー アカウントを追加します。

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

無効なアカウントを削除するには、**ConnectedDevicesAccountManager.removeAccountAsync** を使用できます。

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```