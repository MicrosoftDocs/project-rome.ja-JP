---
title: MCDConnectedDevicesNotificationRegistration
description: このクラスは、(プロジェクト ローマ シナリオによっては必要に応じて) プッシュ通知サービスでのアプリの登録を表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 38cd140538d6e6dabddda39ba98f736fc708ade7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801434"
---
# <a name="class-mcdconnecteddevicesnotificationregistration"></a><span data-ttu-id="e8a7e-104">クラス `MCDConnectedDevicesNotificationRegistration`</span><span class="sxs-lookup"><span data-stu-id="e8a7e-104">class `MCDConnectedDevicesNotificationRegistration`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistration : NSObject
```  
 <span data-ttu-id="e8a7e-105">このクラスは、(プロジェクト ローマ シナリオによっては必要に応じて) プッシュ通知サービスでのアプリの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="e8a7e-105">This class represents the app's registration with a push notification service (necessary for some Project Rome scenarios).</span></span> <span data-ttu-id="e8a7e-106">これは、接続されているデバイス プラットフォームには、この情報を伝えます。</span><span class="sxs-lookup"><span data-stu-id="e8a7e-106">It conveys this information to the Connected Devices Platform.</span></span>

## <a name="properties"></a><span data-ttu-id="e8a7e-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e8a7e-107">Properties</span></span>

### <a name="type"></a><span data-ttu-id="e8a7e-108">type</span><span class="sxs-lookup"><span data-stu-id="e8a7e-108">type</span></span>
`@property(nonatomic, readwrite) MCDConnectedDevicesNotificationType type;`

<span data-ttu-id="e8a7e-109">このセットアップでの通知の種類。</span><span class="sxs-lookup"><span data-stu-id="e8a7e-109">The type of notifications in this setup.</span></span>

### <a name="token"></a><span data-ttu-id="e8a7e-110">トークン</span><span class="sxs-lookup"><span data-stu-id="e8a7e-110">token</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* token;`

<span data-ttu-id="e8a7e-111">登録トークンです。</span><span class="sxs-lookup"><span data-stu-id="e8a7e-111">The registration token.</span></span>

### <a name="appid"></a><span data-ttu-id="e8a7e-112">AppId</span><span class="sxs-lookup"><span data-stu-id="e8a7e-112">appId</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* appId;`

<span data-ttu-id="e8a7e-113">プッシュ通知登録のアプリ ID です。</span><span class="sxs-lookup"><span data-stu-id="e8a7e-113">The app ID for push notification registration.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="e8a7e-114">AppDisplayName</span><span class="sxs-lookup"><span data-stu-id="e8a7e-114">appDisplayName</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* appDisplayName;`

<span data-ttu-id="e8a7e-115">アプリの表示名。</span><span class="sxs-lookup"><span data-stu-id="e8a7e-115">The app display name.</span></span> <span data-ttu-id="e8a7e-116">Microsoft デベロッパー ポータルに登録されているアプリの名前があります。</span><span class="sxs-lookup"><span data-stu-id="e8a7e-116">This should be the name of the app that was used for registration on the Microsoft dev portal.</span></span>