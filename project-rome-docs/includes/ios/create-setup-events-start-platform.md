---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 60a4e282fc5446e38a80e72979e12daad51b2026
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "59804501"
---
### <a name="create-an-instance-of-the-platform"></a><span data-ttu-id="ad3c8-103">プラットフォームのインスタンスの作成</span><span class="sxs-lookup"><span data-stu-id="ad3c8-103">Create an instance of the platform</span></span>

<span data-ttu-id="ad3c8-104">開始するには、単純にプラットフォームをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-104">To get started simply instantiate the platform.</span></span>

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="ad3c8-105">MCDConnectedDevicesAccountManager への登録</span><span class="sxs-lookup"><span data-stu-id="ad3c8-105">Subscribe to MCDConnectedDevicesAccountManager</span></span>

<span data-ttu-id="ad3c8-106">プラットフォームは、認証済みのユーザーがプラットフォームにアクセスすることを要求します。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="ad3c8-107">有効なアカウントが使用されていることを保証するために、**MCDConnectedDevicesAccountManager** イベントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-107">You'll need to subscribe to **MCDConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span>

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

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="ad3c8-108">MCDConnectedDevicesNotificationRegistrationManager への登録</span><span class="sxs-lookup"><span data-stu-id="ad3c8-108">Subscribe to MCDConnectedDevicesNotificationRegistrationManager</span></span>

<span data-ttu-id="ad3c8-109">同様に、プラットフォームは通知を使用してデバイス間でコマンドを配信します。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="ad3c8-110">したがって、使用されているアカウントに対してクラウドの登録状態が有効であることを保証するために、**MCDConnectedDevicesNotificationRegistrationManager** イベントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-110">Therefore, you must subscribe to the **MCDConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="ad3c8-111">**MCDConnectedDevicesNotificationRegistrationState** を使用して状態を確認する</span><span class="sxs-lookup"><span data-stu-id="ad3c8-111">Verify the the state using **MCDConnectedDevicesNotificationRegistrationState**</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a><span data-ttu-id="ad3c8-112">プラットフォームの開始</span><span class="sxs-lookup"><span data-stu-id="ad3c8-112">Start the platform</span></span>
<span data-ttu-id="ad3c8-113">プラットフォームが初期化され、イベント ハンドラーが配置されたので、リモート システム デバイスの検出を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="ad3c8-114">アプリが認識しているユーザー アカウントの取得</span><span class="sxs-lookup"><span data-stu-id="ad3c8-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="ad3c8-115">アプリが認識しているユーザー アカウントの一覧を、確実に **MCDConnectedDevicesAccountManager** と正しく同期することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **MCDConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="ad3c8-116">**MCDConnectedDevicesAccountManager.addAccountAsync** を使用して新しいユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-116">Use **MCDConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

<span data-ttu-id="ad3c8-117">無効なアカウントを削除するには、**MCDConnectedDevicesAccountManager.removeAccountAsync** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad3c8-117">To remove an invalid account you can use **MCDConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```