---
title: MCDConnectedDevicesPlatform
description: 接続されているデバイス プラットフォームを表し、アプリの接続を管理するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 33fdb6f7dfd7d11831da1f7710215e35306d79d1
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909744"
---
# <a name="class-mcdconnecteddevicesplatform"></a><span data-ttu-id="223dd-104">クラス `MCDConnectedDevicesPlatform`</span><span class="sxs-lookup"><span data-stu-id="223dd-104">class `MCDConnectedDevicesPlatform`</span></span> 

```
@interface MCDConnectedDevicesPlatform : NSObject
```  
<span data-ttu-id="223dd-105">このクラスが接続されているデバイス プラットフォームを表し、アプリの接続を管理するには。</span><span class="sxs-lookup"><span data-stu-id="223dd-105">This class to represent the Connected Devices Platform and manage the app's connection to it.</span></span>

## <a name="properties"></a><span data-ttu-id="223dd-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="223dd-106">Properties</span></span>

### <a name="accountmanager"></a><span data-ttu-id="223dd-107">accountManager</span><span class="sxs-lookup"><span data-stu-id="223dd-107">accountManager</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccountManager* accountManager;`

<span data-ttu-id="223dd-108">プラットフォームによって保持されている MCDConnectedDevicesAccountManager インスタンス。</span><span class="sxs-lookup"><span data-stu-id="223dd-108">MCDConnectedDevicesAccountManager instance held by the platform.</span></span>

### <a name="notificationregistrationmanager"></a><span data-ttu-id="223dd-109">notificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="223dd-109">notificationRegistrationManager</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistrationManager* notificationRegistrationManager;`

<span data-ttu-id="223dd-110">プラットフォームによって保持されている MCDConnectedDevicesNotificationRegistrationManager インスタンス。</span><span class="sxs-lookup"><span data-stu-id="223dd-110">MCDConnectedDevicesNotificationRegistrationManager instance held by platform.</span></span>

## <a name="constructors"></a><span data-ttu-id="223dd-111">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="223dd-111">Constructors</span></span>

### <a name="platformwithsettings"></a><span data-ttu-id="223dd-112">platformWithSettings</span><span class="sxs-lookup"><span data-stu-id="223dd-112">platformWithSettings</span></span>
`+ (nullable instancetype)platformWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

<span data-ttu-id="223dd-113">指定したプラットフォームの設定では、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="223dd-113">A new instance of this class with specified platform settings.</span></span>

#### <a name="parameters"></a><span data-ttu-id="223dd-114">パラメーター</span><span class="sxs-lookup"><span data-stu-id="223dd-114">Parameters</span></span> 
* `settings` 

<span data-ttu-id="223dd-115">プラットフォームのアプリの設定を格納する MCDConnectedDevicesPlatformSettings オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="223dd-115">The MCDConnectedDevicesPlatformSettings object which stores the app's settings of the platform.</span></span>

#### <a name="returns"></a><span data-ttu-id="223dd-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="223dd-116">Returns</span></span>

<span data-ttu-id="223dd-117">アプリのプラットフォームの設定を含む MCDConnectedDevicesPlatform オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="223dd-117">Returns an MCDConnectedDevicesPlatform object containing the app's platform settings.</span></span>

### <a name="initwithsettings"></a><span data-ttu-id="223dd-118">initWithSettings</span><span class="sxs-lookup"><span data-stu-id="223dd-118">initWithSettings</span></span>
`- (nullable instancetype)initWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

<span data-ttu-id="223dd-119">プラットフォームの設定では、このクラスの新しいインスタンス。</span><span class="sxs-lookup"><span data-stu-id="223dd-119">A new instance of this class with the platform settings.</span></span>

#### <a name="parameters"></a><span data-ttu-id="223dd-120">パラメーター</span><span class="sxs-lookup"><span data-stu-id="223dd-120">Parameters</span></span> 
* `settings` 

<span data-ttu-id="223dd-121">プラットフォームのアプリの設定を格納する MCDConnectedDevicesPlatformSettings オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="223dd-121">The MCDConnectedDevicesPlatformSettings object which stores the app's settings of the platform.</span></span>

#### <a name="returns"></a><span data-ttu-id="223dd-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="223dd-122">Returns</span></span>

<span data-ttu-id="223dd-123">アプリのプラットフォームの設定を使用して初期化 MCDConnectedDevicesPlatform オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="223dd-123">Returns an MCDConnectedDevicesPlatform object initialized with the app's platform settings.</span></span>

## <a name="methods"></a><span data-ttu-id="223dd-124">メソッド</span><span class="sxs-lookup"><span data-stu-id="223dd-124">Methods</span></span>

### <a name="processnotification"></a><span data-ttu-id="223dd-125">processNotification</span><span class="sxs-lookup"><span data-stu-id="223dd-125">processNotification</span></span>
`- (MCDConnectedDevicesProcessNotificationOperation* _Nonnull)processNotification:(NSDictionary* _Nonnull)notification;`

<span data-ttu-id="223dd-126">受信した APNs 通知を処理します。</span><span class="sxs-lookup"><span data-stu-id="223dd-126">Process incoming APNs notification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="223dd-127">パラメーター</span><span class="sxs-lookup"><span data-stu-id="223dd-127">Parameters</span></span> 
* `notification` 

<span data-ttu-id="223dd-128">APNs 通知処理にはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="223dd-128">Contains the APNs notification to process.</span></span>

#### <a name="returns"></a><span data-ttu-id="223dd-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="223dd-129">Returns</span></span>

<span data-ttu-id="223dd-130">MCDConnectedDevicesProcessNotificationOperation クラスのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="223dd-130">An instance of the MCDConnectedDevicesProcessNotificationOperation class.</span></span>

### <a name="start"></a><span data-ttu-id="223dd-131">スタート</span><span class="sxs-lookup"><span data-stu-id="223dd-131">start</span></span>
`- (void) start;`

<span data-ttu-id="223dd-132">プラットフォームを起動します。</span><span class="sxs-lookup"><span data-stu-id="223dd-132">Start the platform.</span></span>

### <a name="shutdownasync"></a><span data-ttu-id="223dd-133">shutdownAsync</span><span class="sxs-lookup"><span data-stu-id="223dd-133">shutdownAsync</span></span>
`- (void)shutdownAsync:(void (^_Nonnull)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="223dd-134">接続されているデバイス プラットフォームをシャット ダウンします。</span><span class="sxs-lookup"><span data-stu-id="223dd-134">Shuts down the Connected Devices Platform.</span></span>

#### <a name="parameters"></a><span data-ttu-id="223dd-135">パラメーター</span><span class="sxs-lookup"><span data-stu-id="223dd-135">Parameters</span></span> 
* `completionBlock` 

<span data-ttu-id="223dd-136">完了時に呼び出すブロックします。</span><span class="sxs-lookup"><span data-stu-id="223dd-136">The block to invoke upon completion.</span></span>