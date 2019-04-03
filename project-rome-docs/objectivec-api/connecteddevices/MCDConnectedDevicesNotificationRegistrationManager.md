---
title: MCDConnectedDevicesNotificationRegistrationManager
description: すべてのアカウント ローマ クラウド通知の登録を管理します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: d4f5f7963514795e3e296d9bdb42b1811af4f7cc
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909904"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="91c4b-104">クラス `MCDConnectedDevicesNotificationRegistrationManager`</span><span class="sxs-lookup"><span data-stu-id="91c4b-104">class `MCDConnectedDevicesNotificationRegistrationManager`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationManager : NSObject
```  
<span data-ttu-id="91c4b-105">すべてのアカウントには、接続しているデバイス プラットフォーム クラウド通知の登録を管理します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-105">Manages the registration for the Connected Devices platform cloud notification for all accounts.</span></span>

<span data-ttu-id="91c4b-106">MCDConnectedDevicesNotificationRegistrationManager では、各アカウント用に登録通知情報を管理します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-106">MCDConnectedDevicesNotificationRegistrationManager manages the notification information registered for each account.</span></span> <span data-ttu-id="91c4b-107">いつでも、アプリの通知情報を変更 (たとえば、APNS では、そのトークンが変更されます) 場合、または、通知情報が期限切れにならない場合に、アプリの情報を再登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91c4b-107">Any time an app's notification information changes (for example, when APNS changes its token), or when the notification information is expiring, an app should re-register its information.</span></span> <span data-ttu-id="91c4b-108">アプリケーションがのみの通信を送信する応答を関心がある場合は、ポーリング登録を使用できます。</span><span class="sxs-lookup"><span data-stu-id="91c4b-108">If an application only cares about responses to outgoing communication, a Polling registration may be used.</span></span>

> [!NOTE] 
> <span data-ttu-id="91c4b-109">ConnectedDevices シナリオの多くは正常に機能する前に、通知情報を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91c4b-109">Notification information must be registered before many ConnectedDevices scenarios will work successfully.</span></span> 

## <a name="properties"></a><span data-ttu-id="91c4b-110">プロパティ</span><span class="sxs-lookup"><span data-stu-id="91c4b-110">Properties</span></span>

### <a name="registrationstatechanged"></a><span data-ttu-id="91c4b-111">registrationStateChanged</span><span class="sxs-lookup"><span data-stu-id="91c4b-111">registrationStateChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesNotificationRegistrationManager*, MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs*>* registrationStateChanged;`

<span data-ttu-id="91c4b-112">イベントは、アプリがアカウントの通知の登録状態が変更されたとき。</span><span class="sxs-lookup"><span data-stu-id="91c4b-112">Event to let the app know when notification registration state changes for an account.</span></span> 

## <a name="methods"></a><span data-ttu-id="91c4b-113">メソッド</span><span class="sxs-lookup"><span data-stu-id="91c4b-113">Methods</span></span>

### <a name="registerforaccountasync"></a><span data-ttu-id="91c4b-114">registerForAccountAsync</span><span class="sxs-lookup"><span data-stu-id="91c4b-114">registerForAccountAsync</span></span>
`- (void) registerForAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration callback:(nonnull void (^)(BOOL, NSError* _Nullable))callback __attribute__((deprecated("Use registerAsync instead")));`

<span data-ttu-id="91c4b-115">特定の通知の登録情報を指定されたアカウントを登録します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-115">Register the given account with the given notification registration information.</span></span> <span data-ttu-id="91c4b-116">これにより、このアプリケーションはこのアカウントの新しい情報を接続しているデバイスについて通知できるように、通知チャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-116">This creates a notification channel so that this application can be notified about new Connected Devices information for this account.</span></span> <span data-ttu-id="91c4b-117">他のアプリケーションが MCDRemoteSystemAppRegistration 情報が公開されるまで、この通知チャネルを使用してこのアプリと通信できるしないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c4b-117">Note that other applications can not communicate with this app using this notification channel until the MCDRemoteSystemAppRegistration information is published.</span></span>

> [!WARNING]
> <span data-ttu-id="91c4b-118">この関数が非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="91c4b-118">This function is deprecated.</span></span> <span data-ttu-id="91c4b-119">RegisterAsync を使用してください。</span><span class="sxs-lookup"><span data-stu-id="91c4b-119">Please use registerAsync instead.</span></span>

#### <a name="parameters"></a><span data-ttu-id="91c4b-120">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c4b-120">Parameters</span></span> 
* `account` 

<span data-ttu-id="91c4b-121">通知情報を登録するアカウント。</span><span class="sxs-lookup"><span data-stu-id="91c4b-121">Account for which to register notification information.</span></span>

* `notificationRegistration` 

<span data-ttu-id="91c4b-122">通知情報を登録します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-122">Notification information to register.</span></span>

* `callback` 

<span data-ttu-id="91c4b-123">コールバックでは、正常に完了した登録場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-123">The callback result for if the registration completed successfully.</span></span>

### <a name="registerasync"></a><span data-ttu-id="91c4b-124">registerAsync</span><span class="sxs-lookup"><span data-stu-id="91c4b-124">registerAsync</span></span>
`- (void) registerAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration completion:(nonnull void (^)(MCDConnectedDevicesNotificationRegistrationResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="91c4b-125">特定の通知の登録情報を指定されたアカウントを登録します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-125">Register the given account with the given notification registration information.</span></span> <span data-ttu-id="91c4b-126">これにより、このアプリケーションはこのアカウントの新しい情報を接続しているデバイスについて通知できるように、通知チャネルを作成します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-126">This creates a notification channel so that this application can be notified about new Connected Devices information for this account.</span></span> <span data-ttu-id="91c4b-127">他のアプリケーションが MCDRemoteSystemAppRegistration 情報が公開されるまで、この通知チャネルを使用してこのアプリと通信できるしないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91c4b-127">Note that other applications can not communicate with this app using this notification channel until the MCDRemoteSystemAppRegistration information is published.</span></span>

#### <a name="parameters"></a><span data-ttu-id="91c4b-128">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c4b-128">Parameters</span></span> 
* `account` 

<span data-ttu-id="91c4b-129">通知情報を登録するアカウント。</span><span class="sxs-lookup"><span data-stu-id="91c4b-129">Account for which to register notification information.</span></span>

* `notificationRegistration` 

<span data-ttu-id="91c4b-130">通知情報を登録します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-130">Notification information to register.</span></span>

* `callback` 

<span data-ttu-id="91c4b-131">コールバックでは、正常に完了した登録場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-131">The callback result for if the registration completed successfully.</span></span>

### <a name="getnotificationregistrationstateforaccount"></a><span data-ttu-id="91c4b-132">getNotificationRegistrationStateForAccount</span><span class="sxs-lookup"><span data-stu-id="91c4b-132">getNotificationRegistrationStateForAccount</span></span>
`- (MCDConnectedDevicesNotificationRegistrationState) getNotificationRegistrationStateForAccount:(MCDConnectedDevicesAccount* _Nonnull)account;`

<span data-ttu-id="91c4b-133">指定されたアカウントの現在の通知の登録状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="91c4b-133">Retrieve the current notification registration state for the given account.</span></span> <span data-ttu-id="91c4b-134">登録されている通知については、最終的に期限切れになります (アプリがアンインストールされるか、非常に長い時間で実行されない場合に便利です)。</span><span class="sxs-lookup"><span data-stu-id="91c4b-134">The notification information that is registered will eventually expire (useful if the app is uninstalled or not run in a very long time).</span></span> <span data-ttu-id="91c4b-135">登録が期限切れ/期限切れになったときに、アプリは、通知情報を再登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91c4b-135">An app should re-register its notification information when the registration is expiring / expired.</span></span> 

#### <a name="parameters"></a><span data-ttu-id="91c4b-136">パラメーター</span><span class="sxs-lookup"><span data-stu-id="91c4b-136">Parameters</span></span> 
* `account`

<span data-ttu-id="91c4b-137">登録の状態を取得する対象のアカウント。</span><span class="sxs-lookup"><span data-stu-id="91c4b-137">Account for which to get registration state.</span></span>

#### <a name="returns"></a><span data-ttu-id="91c4b-138">戻り値</span><span class="sxs-lookup"><span data-stu-id="91c4b-138">Returns</span></span>

<span data-ttu-id="91c4b-139">通知登録の状態。</span><span class="sxs-lookup"><span data-stu-id="91c4b-139">State of the notification registration.</span></span>
