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
### <a name="create-the-platform"></a><span data-ttu-id="da718-103">プラットフォームの作成</span><span class="sxs-lookup"><span data-stu-id="da718-103">Create the platform</span></span>


<span data-ttu-id="da718-104">開始するには、単純にプラットフォームをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="da718-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="da718-105">ユーザー アカウントを処理するための ConnectedDevicesAccountManager イベントに登録する</span><span class="sxs-lookup"><span data-stu-id="da718-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="da718-106">プラットフォームは、認証済みのユーザーがプラットフォームにアクセスすることを要求します。</span><span class="sxs-lookup"><span data-stu-id="da718-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="da718-107">有効なアカウントが使用されていることを保証するために、**ConnectedDevicesAccountManager** イベントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da718-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="da718-108">ConnectedDevicesNotificationRegistrationManager イベントに登録する</span><span class="sxs-lookup"><span data-stu-id="da718-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="da718-109">同様に、プラットフォームは通知を使用してデバイス間でコマンドを配信します。</span><span class="sxs-lookup"><span data-stu-id="da718-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="da718-110">したがって、使用されているアカウントに対してクラウドの登録状態が有効であることを保証するために、**ConnectedDevicesNotificationRegistrationManager** イベントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da718-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="da718-111">**ConnectedDevicesNotificationRegistrationState** を使用して状態を確認する</span><span class="sxs-lookup"><span data-stu-id="da718-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a><span data-ttu-id="da718-112">プラットフォームの開始</span><span class="sxs-lookup"><span data-stu-id="da718-112">Start the platform</span></span>
<span data-ttu-id="da718-113">プラットフォームが初期化され、イベント ハンドラーが配置されたので、リモート システム デバイスの検出を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="da718-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="da718-114">アプリが認識しているユーザー アカウントの取得</span><span class="sxs-lookup"><span data-stu-id="da718-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="da718-115">アプリが認識しているユーザー アカウントの一覧を、確実に **ConnectedDevicesAccountManager** と正しく同期することが重要です。</span><span class="sxs-lookup"><span data-stu-id="da718-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **ConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="da718-116">**ConnectedDevicesAccountManager.addAccountAsync** を使用して新しいユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="da718-116">Use **ConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

<span data-ttu-id="da718-117">無効なアカウントを削除するには、**ConnectedDevicesAccountManager.removeAccountAsync** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="da718-117">To remove an invalid account you can use **ConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```