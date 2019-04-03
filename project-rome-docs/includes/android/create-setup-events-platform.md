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
### <a name="create-the-platform"></a><span data-ttu-id="03aea-103">プラットフォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="03aea-103">Create the platform</span></span>

<span data-ttu-id="03aea-104">開始する、プラットフォームを単純にインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="03aea-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="03aea-105">ユーザー アカウントを処理するために ConnectedDevicesAccountManager イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="03aea-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="03aea-106">プラットフォームには、プラットフォームへのアクセスに認証されたユーザーが必要です。</span><span class="sxs-lookup"><span data-stu-id="03aea-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="03aea-107">購読を依頼する必要があります**ConnectedDevicesAccountManager**のイベントを有効なアカウントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="03aea-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="03aea-108">ConnectedDevicesNotificationRegistrationManager イベントにサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="03aea-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="03aea-109">同様に、プラットフォームは通知を使用して、デバイス間でのコマンドを配布します。</span><span class="sxs-lookup"><span data-stu-id="03aea-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="03aea-110">そのためにサブスクライブする必要があります、 **ConnectedDevicesNotificationRegistrationManager**のイベントをクラウドの登録状態が使用されているアカウントに対して有効です。</span><span class="sxs-lookup"><span data-stu-id="03aea-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="03aea-111">確認の状態を使用して、 **ConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="03aea-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
    // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```