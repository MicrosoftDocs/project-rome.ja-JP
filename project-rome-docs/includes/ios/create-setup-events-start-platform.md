---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 60a4e282fc5446e38a80e72979e12daad51b2026
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907214"
---
### <a name="create-an-instance-of-the-platform"></a><span data-ttu-id="9075f-103">プラットフォームのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9075f-103">Create an instance of the platform</span></span>

<span data-ttu-id="9075f-104">開始する、プラットフォームを単純にインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="9075f-104">To get started simply instantiate the platform.</span></span>

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="9075f-105">MCDConnectedDevicesAccountManager を購読します。</span><span class="sxs-lookup"><span data-stu-id="9075f-105">Subscribe to MCDConnectedDevicesAccountManager</span></span>

<span data-ttu-id="9075f-106">プラットフォームには、プラットフォームへのアクセスに認証されたユーザーが必要です。</span><span class="sxs-lookup"><span data-stu-id="9075f-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="9075f-107">購読を依頼する必要があります**MCDConnectedDevicesAccountManager**のイベントを有効なアカウントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="9075f-107">You'll need to subscribe to **MCDConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span>

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

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="9075f-108">MCDConnectedDevicesNotificationRegistrationManager を購読します。</span><span class="sxs-lookup"><span data-stu-id="9075f-108">Subscribe to MCDConnectedDevicesNotificationRegistrationManager</span></span>

<span data-ttu-id="9075f-109">同様に、プラットフォームは通知を使用して、デバイス間でのコマンドを配布します。</span><span class="sxs-lookup"><span data-stu-id="9075f-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="9075f-110">そのためにサブスクライブする必要があります、 **MCDConnectedDevicesNotificationRegistrationManager**のイベントをクラウドの登録状態が使用されているアカウントに対して有効です。</span><span class="sxs-lookup"><span data-stu-id="9075f-110">Therefore, you must subscribe to the **MCDConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="9075f-111">確認の状態を使用して、 **MCDConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="9075f-111">Verify the the state using **MCDConnectedDevicesNotificationRegistrationState**</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a><span data-ttu-id="9075f-112">プラットフォームを開始します。</span><span class="sxs-lookup"><span data-stu-id="9075f-112">Start the platform</span></span>
<span data-ttu-id="9075f-113">これで、プラットフォームは初期化され、イベント ハンドラーは、配置は、リモート システムのデバイスの検出を開始する準備が完了したらです。</span><span class="sxs-lookup"><span data-stu-id="9075f-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="9075f-114">アプリに既知のユーザー アカウントを取得します。</span><span class="sxs-lookup"><span data-stu-id="9075f-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="9075f-115">アプリに既知のユーザー アカウントの一覧と正しく同期されることを確認することが重要、 **MCDConnectedDevicesAccountManager**します。</span><span class="sxs-lookup"><span data-stu-id="9075f-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **MCDConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="9075f-116">使用**MCDConnectedDevicesAccountManager.addAccountAsync**新しいユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="9075f-116">Use **MCDConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

<span data-ttu-id="9075f-117">使用できる、無効なアカウントを削除する**MCDConnectedDevicesAccountManager.removeAccountAsync**</span><span class="sxs-lookup"><span data-stu-id="9075f-117">To remove an invalid account you can use **MCDConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```