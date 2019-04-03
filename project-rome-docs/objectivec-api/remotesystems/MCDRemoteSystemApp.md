---
title: MCDRemoteSystemApp
description: 接続に使用されるリモート システム上のアプリケーションを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 28ec3fbe03150cb45c0a554a0499f1a6b657e50d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907654"
---
# <a name="class-mcdremotesystemapp"></a><span data-ttu-id="cd7db-104">クラス `MCDRemoteSystemApp`</span><span class="sxs-lookup"><span data-stu-id="cd7db-104">class `MCDRemoteSystemApp`</span></span> 

```
@interface MCDRemoteSystemApp : NSObject
```  

<span data-ttu-id="cd7db-105">接続に使用されるリモート システム上のアプリケーションを表します。</span><span class="sxs-lookup"><span data-stu-id="cd7db-105">Represents an application on a remote system that is available for connectivity.</span></span>

## <a name="properties"></a><span data-ttu-id="cd7db-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cd7db-106">Properties</span></span>

### <a name="appid"></a><span data-ttu-id="cd7db-107">AppId</span><span class="sxs-lookup"><span data-stu-id="cd7db-107">appId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* appId;`

<span data-ttu-id="cd7db-108">このアプリケーションの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="cd7db-108">A unique identifier for this application.</span></span>

### <a name="displayname"></a><span data-ttu-id="cd7db-109">displayName</span><span class="sxs-lookup"><span data-stu-id="cd7db-109">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="cd7db-110">このアプリケーションのわかりやすい表示名。</span><span class="sxs-lookup"><span data-stu-id="cd7db-110">The friendly display name for this application.</span></span> <span data-ttu-id="cd7db-111">Bluetooth の識別については、デバイスで使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="cd7db-111">This is the name used by the device for Bluetooth identification.</span></span> <span data-ttu-id="cd7db-112">これが設定されていないか、デバイスが Bluetooth をサポートされていません、このフィールドは空になります。</span><span class="sxs-lookup"><span data-stu-id="cd7db-112">If this hasn't been set or the device doesn't support Bluetooth, this field will be empty.</span></span>

### <a name="availablebyproximity"></a><span data-ttu-id="cd7db-113">availableByProximity</span><span class="sxs-lookup"><span data-stu-id="cd7db-113">availableByProximity</span></span>
`@property(nonatomic, readonly, getter=isAvailableByProximity) BOOL availableByProximity;`

<span data-ttu-id="cd7db-114">このアプリケーションが位の接続で現在使用できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cd7db-114">Indicates whether this application is currently available for proximal connection.</span></span>

### <a name="availablebyspatialproximity"></a><span data-ttu-id="cd7db-115">availableBySpatialProximity</span><span class="sxs-lookup"><span data-stu-id="cd7db-115">availableBySpatialProximity</span></span>
`@property(nonatomic, readonly, getter=isAvailableBySpatialProximity) BOOL availableBySpatialProximity;`

<span data-ttu-id="cd7db-116">このアプリケーションは、空間の共有接続で現在使用できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="cd7db-116">Indicates whether this application is currently available for spatial sharing connection.</span></span>

### <a name="attributes"></a><span data-ttu-id="cd7db-117">属性</span><span class="sxs-lookup"><span data-stu-id="cd7db-117">attributes</span></span>
`@property(nonatomic, readonly, nonnull) NSDictionary<NSString*, NSString*>* attributes;`

<span data-ttu-id="cd7db-118">このアプリケーションの属性を定義するキー/値ペアのディクショナリ。</span><span class="sxs-lookup"><span data-stu-id="cd7db-118">A dictionary of key/value pairs defining the attributes of this application.</span></span>

### <a name="appservices"></a><span data-ttu-id="cd7db-119">appServices</span><span class="sxs-lookup"><span data-stu-id="cd7db-119">appServices</span></span>
`@property(nonatomic, readonly, nullable) NSArray<MCDAppServiceDescription*>* appServices;`

<span data-ttu-id="cd7db-120">このアプリケーションがリモート接続用に提供するアプリ サービスを記述する MCDAppServiceDescription インスタンスの配列。</span><span class="sxs-lookup"><span data-stu-id="cd7db-120">An array of MCDAppServiceDescription instances describing the app services that this application provides for remote connectivity.</span></span>

### <a name="accounts"></a><span data-ttu-id="cd7db-121">アカウント</span><span class="sxs-lookup"><span data-stu-id="cd7db-121">accounts</span></span>
`@property(nonatomic, readonly, nullable) NSArray<MCDConnectedDevicesAccount*>* accounts;`

<span data-ttu-id="cd7db-122">アクセス許可について知っておく必要のある MCDRemoteSystemApp に関連付けられているアカウント。</span><span class="sxs-lookup"><span data-stu-id="cd7db-122">The Account associated with the MCDRemoteSystemApp that you have permissions to know about.</span></span> <span data-ttu-id="cd7db-123">MCDRemoteSystemWatcher が開始されると、MCDConnectedDevicesAccountManager で、MCDConnectedDevicesAccount が存在するかどうかは、アクセス許可が決まります。</span><span class="sxs-lookup"><span data-stu-id="cd7db-123">What determines permissions is if the MCDConnectedDevicesAccount exists in the MCDConnectedDevicesAccountManager when the MCDRemoteSystemWatcher is started.</span></span>