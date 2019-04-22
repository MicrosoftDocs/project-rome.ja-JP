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
### <a name="create-the-platform"></a><span data-ttu-id="2558f-103">プラットフォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="2558f-103">Create the platform</span></span>


<span data-ttu-id="2558f-104">開始する、プラットフォームを単純にインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="2558f-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="2558f-105">ユーザー アカウントを処理するために ConnectedDevicesAccountManager イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="2558f-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="2558f-106">プラットフォームには、プラットフォームへのアクセスに認証されたユーザーが必要です。</span><span class="sxs-lookup"><span data-stu-id="2558f-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="2558f-107">購読を依頼する必要があります**ConnectedDevicesAccountManager**のイベントを有効なアカウントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="2558f-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="2558f-108">ConnectedDevicesNotificationRegistrationManager イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="2558f-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="2558f-109">同様に、プラットフォームは通知を使用して、デバイス間でのコマンドを配布します。</span><span class="sxs-lookup"><span data-stu-id="2558f-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="2558f-110">そのためにサブスクライブする必要があります、 **ConnectedDevicesNotificationRegistrationManager**のイベントをクラウドの登録状態が使用されているアカウントに対して有効です。</span><span class="sxs-lookup"><span data-stu-id="2558f-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="2558f-111">確認の状態を使用して、 **ConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="2558f-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a><span data-ttu-id="2558f-112">プラットフォームを開始します。</span><span class="sxs-lookup"><span data-stu-id="2558f-112">Start the platform</span></span>
<span data-ttu-id="2558f-113">これで、プラットフォームは初期化され、イベント ハンドラーは、配置は、リモート システムのデバイスの検出を開始する準備が完了したらです。</span><span class="sxs-lookup"><span data-stu-id="2558f-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="2558f-114">アプリに既知のユーザー アカウントを取得します。</span><span class="sxs-lookup"><span data-stu-id="2558f-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="2558f-115">アプリに既知のユーザー アカウントの一覧と正しく同期されることを確認することが重要、 **ConnectedDevicesAccountManager**します。</span><span class="sxs-lookup"><span data-stu-id="2558f-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **ConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="2558f-116">使用**ConnectedDevicesAccountManager.addAccountAsync**新しいユーザー アカウントを追加します。</span><span class="sxs-lookup"><span data-stu-id="2558f-116">Use **ConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

<span data-ttu-id="2558f-117">使用できる、無効なアカウントを削除する**ConnectedDevicesAccountManager.removeAccountAsync**</span><span class="sxs-lookup"><span data-stu-id="2558f-117">To remove an invalid account you can use **ConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```