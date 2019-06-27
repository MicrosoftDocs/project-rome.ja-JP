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
### <a name="create-the-platform"></a><span data-ttu-id="be4e0-103">プラットフォームの作成</span><span class="sxs-lookup"><span data-stu-id="be4e0-103">Create the platform</span></span>

<span data-ttu-id="be4e0-104">開始するには、単純にプラットフォームをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="be4e0-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="be4e0-105">ユーザー アカウントを処理するための ConnectedDevicesAccountManager イベントに登録する</span><span class="sxs-lookup"><span data-stu-id="be4e0-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="be4e0-106">プラットフォームは、認証済みのユーザーがプラットフォームにアクセスすることを要求します。</span><span class="sxs-lookup"><span data-stu-id="be4e0-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="be4e0-107">有効なアカウントが使用されていることを保証するために、**ConnectedDevicesAccountManager** イベントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be4e0-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="be4e0-108">ConnectedDevicesNotificationRegistrationManager イベントに登録する</span><span class="sxs-lookup"><span data-stu-id="be4e0-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="be4e0-109">同様に、プラットフォームは通知を使用してデバイス間でコマンドを配信します。</span><span class="sxs-lookup"><span data-stu-id="be4e0-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="be4e0-110">したがって、使用されているアカウントに対してクラウドの登録状態が有効であることを保証するために、**ConnectedDevicesNotificationRegistrationManager** イベントに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="be4e0-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="be4e0-111">**ConnectedDevicesNotificationRegistrationState** を使用して状態を確認する</span><span class="sxs-lookup"><span data-stu-id="be4e0-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
    // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```