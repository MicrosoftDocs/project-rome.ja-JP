---
title: MCDConnectedDevicesNotificationRegistration
description: このクラスは、(プロジェクト ローマ シナリオによっては必要に応じて) プッシュ通知サービスでのアプリの登録を表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 38cd140538d6e6dabddda39ba98f736fc708ade7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908884"
---
# <a name="class-mcdconnecteddevicesnotificationregistration"></a><span data-ttu-id="1f7f9-104">クラス `MCDConnectedDevicesNotificationRegistration`</span><span class="sxs-lookup"><span data-stu-id="1f7f9-104">class `MCDConnectedDevicesNotificationRegistration`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistration : NSObject
```  
 <span data-ttu-id="1f7f9-105">このクラスは、(プロジェクト ローマ シナリオによっては必要に応じて) プッシュ通知サービスでのアプリの登録を表します。</span><span class="sxs-lookup"><span data-stu-id="1f7f9-105">This class represents the app's registration with a push notification service (necessary for some Project Rome scenarios).</span></span> <span data-ttu-id="1f7f9-106">これは、接続されているデバイス プラットフォームには、この情報を伝えます。</span><span class="sxs-lookup"><span data-stu-id="1f7f9-106">It conveys this information to the Connected Devices Platform.</span></span>

## <a name="properties"></a><span data-ttu-id="1f7f9-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1f7f9-107">Properties</span></span>

### <a name="type"></a><span data-ttu-id="1f7f9-108">type</span><span class="sxs-lookup"><span data-stu-id="1f7f9-108">type</span></span>
`@property(nonatomic, readwrite) MCDConnectedDevicesNotificationType type;`

<span data-ttu-id="1f7f9-109">このセットアップでの通知の種類。</span><span class="sxs-lookup"><span data-stu-id="1f7f9-109">The type of notifications in this setup.</span></span>

### <a name="token"></a><span data-ttu-id="1f7f9-110">トークン</span><span class="sxs-lookup"><span data-stu-id="1f7f9-110">token</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* token;`

<span data-ttu-id="1f7f9-111">登録トークンです。</span><span class="sxs-lookup"><span data-stu-id="1f7f9-111">The registration token.</span></span>

### <a name="appid"></a><span data-ttu-id="1f7f9-112">AppId</span><span class="sxs-lookup"><span data-stu-id="1f7f9-112">appId</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* appId;`

<span data-ttu-id="1f7f9-113">プッシュ通知登録のアプリ ID です。</span><span class="sxs-lookup"><span data-stu-id="1f7f9-113">The app ID for push notification registration.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="1f7f9-114">AppDisplayName</span><span class="sxs-lookup"><span data-stu-id="1f7f9-114">appDisplayName</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* appDisplayName;`

<span data-ttu-id="1f7f9-115">アプリの表示名。</span><span class="sxs-lookup"><span data-stu-id="1f7f9-115">The app display name.</span></span> <span data-ttu-id="1f7f9-116">Microsoft デベロッパー ポータルに登録されているアプリの名前があります。</span><span class="sxs-lookup"><span data-stu-id="1f7f9-116">This should be the name of the app that was used for registration on the Microsoft dev portal.</span></span>