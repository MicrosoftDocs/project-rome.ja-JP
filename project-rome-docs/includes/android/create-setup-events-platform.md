---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 559752038bb8d73c95d853dcc39be061e64b322f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907684"
---
### <a name="create-the-platform"></a>プラットフォームを作成します。

開始する、プラットフォームを単純にインスタンス化します。

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>ユーザー アカウントを処理するために ConnectedDevicesAccountManager イベントにサブスクライブします。 

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