---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 559752038bb8d73c95d853dcc39be061e64b322f
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59800294"
---
### <a name="create-the-platform"></a>プラットフォームの作成

開始するには、単純にプラットフォームをインスタンス化します。

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>ユーザー アカウントを処理するための ConnectedDevicesAccountManager イベントに登録する 

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