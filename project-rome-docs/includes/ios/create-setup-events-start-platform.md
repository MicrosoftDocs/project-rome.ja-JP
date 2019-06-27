---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 60a4e282fc5446e38a80e72979e12daad51b2026
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59804501"
---
### <a name="create-an-instance-of-the-platform"></a>プラットフォームのインスタンスの作成

開始するには、単純にプラットフォームをインスタンス化します。

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a>MCDConnectedDevicesAccountManager への登録

プラットフォームは、認証済みのユーザーがプラットフォームにアクセスすることを要求します。  有効なアカウントが使用されていることを保証するために、**MCDConnectedDevicesAccountManager** イベントに登録する必要があります。

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager.accessTokenRequested
     subscribe:^(MCDConnectedDevicesAccountManager* _Nonnull manager __unused,
                 MCDConnectedDevicesAccessTokenRequestedEventArgs* _Nonnull request __unused) {

                    // Get access token

                 }
```

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.platform.accountManager.accessTokenInvalidated
     subscribe:^(MCDConnectedDevicesAccountManager* _Nonnull manager __unused,
                 MCDConnectedDevicesAccessTokenInvalidatedEventArgs* _Nonnull request) {

                      // Refresh and renew existing access token

                 }
```

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a>MCDConnectedDevicesNotificationRegistrationManager への登録

同様に、プラットフォームは通知を使用してデバイス間でコマンドを配信します。  したがって、使用されているアカウントに対してクラウドの登録状態が有効であることを保証するために、**MCDConnectedDevicesNotificationRegistrationManager** イベントに登録する必要があります。  **MCDConnectedDevicesNotificationRegistrationState** を使用して状態を確認する

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a>プラットフォームの開始
プラットフォームが初期化され、イベント ハンドラーが配置されたので、リモート システム デバイスの検出を開始する準備ができました。  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a>アプリが認識しているユーザー アカウントの取得

アプリが認識しているユーザー アカウントの一覧を、確実に **MCDConnectedDevicesAccountManager** と正しく同期することが重要です。

**MCDConnectedDevicesAccountManager.addAccountAsync** を使用して新しいユーザー アカウントを追加します。

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

無効なアカウントを削除するには、**MCDConnectedDevicesAccountManager.removeAccountAsync** を使用できます。

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```