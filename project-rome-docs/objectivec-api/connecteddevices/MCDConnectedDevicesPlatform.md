---
title: MCDConnectedDevicesPlatform
description: 接続されているデバイス プラットフォームを表し、アプリの接続を管理するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 33fdb6f7dfd7d11831da1f7710215e35306d79d1
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801784"
---
# <a name="class-mcdconnecteddevicesplatform"></a><span data-ttu-id="8afc4-104">クラス `MCDConnectedDevicesPlatform`</span><span class="sxs-lookup"><span data-stu-id="8afc4-104">class `MCDConnectedDevicesPlatform`</span></span> 

```
@interface MCDConnectedDevicesPlatform : NSObject
```  
<span data-ttu-id="8afc4-105">このクラスが接続されているデバイス プラットフォームを表し、アプリの接続を管理するには。</span><span class="sxs-lookup"><span data-stu-id="8afc4-105">This class to represent the Connected Devices Platform and manage the app's connection to it.</span></span>

## <a name="properties"></a><span data-ttu-id="8afc4-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8afc4-106">Properties</span></span>

### <a name="accountmanager"></a><span data-ttu-id="8afc4-107">accountManager</span><span class="sxs-lookup"><span data-stu-id="8afc4-107">accountManager</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccountManager* accountManager;`

<span data-ttu-id="8afc4-108">プラットフォームによって保持されている MCDConnectedDevicesAccountManager インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8afc4-108">MCDConnectedDevicesAccountManager instance held by the platform.</span></span>

### <a name="notificationregistrationmanager"></a><span data-ttu-id="8afc4-109">notificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="8afc4-109">notificationRegistrationManager</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistrationManager* notificationRegistrationManager;`

<span data-ttu-id="8afc4-110">プラットフォームによって保持されている MCDConnectedDevicesNotificationRegistrationManager インスタンス。</span><span class="sxs-lookup"><span data-stu-id="8afc4-110">MCDConnectedDevicesNotificationRegistrationManager instance held by platform.</span></span>

## <a name="constructors"></a><span data-ttu-id="8afc4-111">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="8afc4-111">Constructors</span></span>

### <a name="platformwithsettings"></a><span data-ttu-id="8afc4-112">platformWithSettings</span><span class="sxs-lookup"><span data-stu-id="8afc4-112">platformWithSettings</span></span>
`+ (nullable instancetype)platformWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

<span data-ttu-id="8afc4-113">指定したプラットフォームの設定では、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8afc4-113">A new instance of this class with specified platform settings.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8afc4-114">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afc4-114">Parameters</span></span> 
* `settings` 

<span data-ttu-id="8afc4-115">プラットフォームのアプリの設定を格納する MCDConnectedDevicesPlatformSettings オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8afc4-115">The MCDConnectedDevicesPlatformSettings object which stores the app's settings of the platform.</span></span>

#### <a name="returns"></a><span data-ttu-id="8afc4-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afc4-116">Returns</span></span>

<span data-ttu-id="8afc4-117">アプリのプラットフォームの設定を含む MCDConnectedDevicesPlatform オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8afc4-117">Returns an MCDConnectedDevicesPlatform object containing the app's platform settings.</span></span>

### <a name="initwithsettings"></a><span data-ttu-id="8afc4-118">initWithSettings</span><span class="sxs-lookup"><span data-stu-id="8afc4-118">initWithSettings</span></span>
`- (nullable instancetype)initWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

<span data-ttu-id="8afc4-119">プラットフォームの設定では、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8afc4-119">A new instance of this class with the platform settings.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8afc4-120">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afc4-120">Parameters</span></span> 
* `settings` 

<span data-ttu-id="8afc4-121">プラットフォームのアプリの設定を格納する MCDConnectedDevicesPlatformSettings オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8afc4-121">The MCDConnectedDevicesPlatformSettings object which stores the app's settings of the platform.</span></span>

#### <a name="returns"></a><span data-ttu-id="8afc4-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afc4-122">Returns</span></span>

<span data-ttu-id="8afc4-123">アプリのプラットフォームの設定を使用して初期化 MCDConnectedDevicesPlatform オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8afc4-123">Returns an MCDConnectedDevicesPlatform object initialized with the app's platform settings.</span></span>

## <a name="methods"></a><span data-ttu-id="8afc4-124">メソッド</span><span class="sxs-lookup"><span data-stu-id="8afc4-124">Methods</span></span>

### <a name="processnotification"></a><span data-ttu-id="8afc4-125">processNotification</span><span class="sxs-lookup"><span data-stu-id="8afc4-125">processNotification</span></span>
`- (MCDConnectedDevicesProcessNotificationOperation* _Nonnull)processNotification:(NSDictionary* _Nonnull)notification;`

<span data-ttu-id="8afc4-126">受信した APNs 通知を処理します。</span><span class="sxs-lookup"><span data-stu-id="8afc4-126">Process incoming APNs notification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8afc4-127">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afc4-127">Parameters</span></span> 
* `notification` 

<span data-ttu-id="8afc4-128">APNs 通知処理にはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8afc4-128">Contains the APNs notification to process.</span></span>

#### <a name="returns"></a><span data-ttu-id="8afc4-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="8afc4-129">Returns</span></span>

<span data-ttu-id="8afc4-130">MCDConnectedDevicesProcessNotificationOperation クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="8afc4-130">An instance of the MCDConnectedDevicesProcessNotificationOperation class.</span></span>

### <a name="start"></a><span data-ttu-id="8afc4-131">start</span><span class="sxs-lookup"><span data-stu-id="8afc4-131">start</span></span>
`- (void) start;`

<span data-ttu-id="8afc4-132">プラットフォームを起動します。</span><span class="sxs-lookup"><span data-stu-id="8afc4-132">Start the platform.</span></span>

### <a name="shutdownasync"></a><span data-ttu-id="8afc4-133">shutdownAsync</span><span class="sxs-lookup"><span data-stu-id="8afc4-133">shutdownAsync</span></span>
`- (void)shutdownAsync:(void (^_Nonnull)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="8afc4-134">接続されているデバイス プラットフォームをシャット ダウンします。</span><span class="sxs-lookup"><span data-stu-id="8afc4-134">Shuts down the Connected Devices Platform.</span></span>

#### <a name="parameters"></a><span data-ttu-id="8afc4-135">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8afc4-135">Parameters</span></span> 
* `completionBlock` 

<span data-ttu-id="8afc4-136">完了時に呼び出すブロックします。</span><span class="sxs-lookup"><span data-stu-id="8afc4-136">The block to invoke upon completion.</span></span>