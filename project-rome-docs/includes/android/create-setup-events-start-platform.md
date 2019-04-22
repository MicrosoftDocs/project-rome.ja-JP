---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: d498d192b6ac909e8b3978b54e6996eef98d2814
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804498"
---
### <a name="create-the-platform"></a>プラットフォームを作成します。


開始する、プラットフォームを単純にインスタンス化します。

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>ユーザー アカウントを処理するために ConnectedDevicesAccountManager イベントにサブスクライブします。 

プラットフォームには、プラットフォームへのアクセスに認証されたユーザーが必要です。  購読を依頼する必要があります**ConnectedDevicesAccountManager**のイベントを有効なアカウントが使用されています。 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a>ConnectedDevicesNotificationRegistrationManager イベントにサブスクライブします。

同様に、プラットフォームは通知を使用して、デバイス間でのコマンドを配布します。  そのためにサブスクライブする必要があります、 **ConnectedDevicesNotificationRegistrationManager**のイベントをクラウドの登録状態が使用されているアカウントに対して有効です。  確認の状態を使用して、 **ConnectedDevicesNotificationRegistrationState**

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a>プラットフォームを開始します。
これで、プラットフォームは初期化され、イベント ハンドラーは、配置は、リモート システムのデバイスの検出を開始する準備が完了したらです。  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a>アプリに既知のユーザー アカウントを取得します。

アプリに既知のユーザー アカウントの一覧と正しく同期されることを確認することが重要、 **ConnectedDevicesAccountManager**します。

使用**ConnectedDevicesAccountManager.addAccountAsync**新しいユーザー アカウントを追加します。

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

使用できる、無効なアカウントを削除する**ConnectedDevicesAccountManager.removeAccountAsync**

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```