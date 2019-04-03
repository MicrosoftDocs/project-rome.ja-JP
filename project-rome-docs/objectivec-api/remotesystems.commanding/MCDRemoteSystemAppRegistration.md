---
title: MCDRemoteSystemAppRegistration
description: このクラスは、接続しているデバイス プラットフォームを登録することであるアプリケーションを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 2c931d3eeacd4aa48e1ef22d573bf0325eb5b98b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909914"
---
# <a name="class-mcdremotesystemappregistration"></a><span data-ttu-id="1c60a-104">クラス `MCDRemoteSystemAppRegistration`</span><span class="sxs-lookup"><span data-stu-id="1c60a-104">class `MCDRemoteSystemAppRegistration`</span></span> 

```
@interface MCDRemoteSystemAppRegistration : NSObject
```  

<span data-ttu-id="1c60a-105">このクラスでは、別の検出可能性がありますを使用してこのアプリに関する情報がすべて含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c60a-105">This class contains all of the information about this app that another could discover and use.</span></span>

> [!NOTE] 
> <span data-ttu-id="1c60a-106">別のアプリに任意の通信の発信をする可能性がありますする前に、MCDRemoteSystemAppRegistration 情報を公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c60a-106">MCDRemoteSystemAppRegistration information must be published before any outgoing communication to another app is possble.</span></span> <span data-ttu-id="1c60a-107">これは、その他のアプリケーションが知ることができるようにする通信に応答する方法。</span><span class="sxs-lookup"><span data-stu-id="1c60a-107">This is so that the other application can know how to respond to that communication.</span></span>

## <a name="properties"></a><span data-ttu-id="1c60a-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1c60a-108">Properties</span></span>

### <a name="account"></a><span data-ttu-id="1c60a-109">アカウント</span><span class="sxs-lookup"><span data-stu-id="1c60a-109">account</span></span>
`@property(nonatomic, readonly, nullable) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="1c60a-110">この登録が属しているアカウント。</span><span class="sxs-lookup"><span data-stu-id="1c60a-110">Account that this registration belongs to.</span></span>

### <a name="attributes"></a><span data-ttu-id="1c60a-111">属性</span><span class="sxs-lookup"><span data-stu-id="1c60a-111">attributes</span></span>
`@property(nonatomic, copy, nullable) NSDictionary<NSString*, NSString*>* attributes;`

 <span data-ttu-id="1c60a-112">このアプリの属性を記述する文字列のディクショナリ。</span><span class="sxs-lookup"><span data-stu-id="1c60a-112">Dictionary of strings that describe the attributes of this app.</span></span>

### <a name="appserviceproviders"></a><span data-ttu-id="1c60a-113">appServiceProviders</span><span class="sxs-lookup"><span data-stu-id="1c60a-113">appServiceProviders</span></span>
`@property(nonatomic, copy, nullable) NSArray<id<MCDAppServiceProvider>>* appServiceProviders;`

<span data-ttu-id="1c60a-114">このアプリをサポートする AppServiceProviders の配列。</span><span class="sxs-lookup"><span data-stu-id="1c60a-114">Array of AppServiceProviders that this app supports.</span></span>

> [!NOTE] 
> <span data-ttu-id="1c60a-115">アプリのサービス プロバイダーは、着信接続を受信するためにこの配列に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c60a-115">An app service provider must be present in this array in order to receive incoming connections.</span></span>  <span data-ttu-id="1c60a-116">MCDRemoteSystemAppRegistration.publishAsync() は、要求を受信するアプリのサービス プロバイダーに呼び出される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1c60a-116">MCDRemoteSystemAppRegistration.publishAsync() does not need to be called for the app service provider to receive requests.</span></span>  

### <a name="launchuriprovider"></a><span data-ttu-id="1c60a-117">launchUriProvider</span><span class="sxs-lookup"><span data-stu-id="1c60a-117">launchUriProvider</span></span>
`@property(nonatomic, readwrite, nullable) id<MCDLaunchUriProvider> launchUriProvider;`

<span data-ttu-id="1c60a-118">このアプリの Uri のプロバイダーを起動します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-118">Launch Uri provider for this app.</span></span>

> [!NOTE] 
> <span data-ttu-id="1c60a-119">起動 uri のプロバイダーは、受信要求を受信するために、このプロパティに格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c60a-119">A launch uri provider must be stored in this property in order to receive incoming requests.</span></span>  <span data-ttu-id="1c60a-120">MCDRemoteSystemAppRegistration.publishAsync() は、要求を受信するアプリのサービス プロバイダーに呼び出される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1c60a-120">MCDRemoteSystemAppRegistration.publishAsync() does not need to be called for the app service provider to receive requests.</span></span>  

## <a name="constructors"></a><span data-ttu-id="1c60a-121">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="1c60a-121">Constructors</span></span>

### <a name="getforaccount"></a><span data-ttu-id="1c60a-122">getForAccount</span><span class="sxs-lookup"><span data-stu-id="1c60a-122">getForAccount</span></span>
`+(nullable instancetype) getForAccount:(MCDConnectedDevicesAccount* _Nonnull) account
                              platform:(MCDConnectedDevicesPlatform* _Nonnull) platform;`

<span data-ttu-id="1c60a-123">アカウントの現在のリモート システムのアプリの登録を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-123">Gets the current remote system app registration for the account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1c60a-124">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c60a-124">Parameters</span></span>
* `account` 

<span data-ttu-id="1c60a-125">アカウントの登録を取得します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-125">Account to retrieve the registration for.</span></span>

* `platform` 

<span data-ttu-id="1c60a-126">登録を取得するプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="1c60a-126">Platform to get registration from.</span></span>

#### <a name="returns"></a><span data-ttu-id="1c60a-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="1c60a-127">Returns</span></span>
<span data-ttu-id="1c60a-128">指定したアカウントの MCDRemoteSystemAppRegistration オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-128">Returns an MCDRemoteSystemAppRegistration object for the provided Account.</span></span>

## <a name="methods"></a><span data-ttu-id="1c60a-129">メソッド</span><span class="sxs-lookup"><span data-stu-id="1c60a-129">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="1c60a-130">saveAsync</span><span class="sxs-lookup"><span data-stu-id="1c60a-130">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(BOOL, NSError* _Nullable))callback  __attribute__((deprecated("Use publishAsync instead")));`

<span data-ttu-id="1c60a-131">他のアプリケーションが検出できるように、RemoteSystemAppRegistration に格納されている情報を保存します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-131">Saves the information currently stored in the RemoteSystemAppRegistration such that other applications can discover it.</span></span>

> [!NOTE] 
> <span data-ttu-id="1c60a-132">この呼び出しが成功するには、MCDConnectedDevicesNotificationRegistration を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c60a-132">MCDConnectedDevicesNotificationRegistration must be registered for this call to succeed.</span></span>

> [!WARNING] 
> <span data-ttu-id="1c60a-133">使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1c60a-133">Deprecated.</span></span> <span data-ttu-id="1c60a-134">PublishAsync を代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-134">Use publishAsync instead.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1c60a-135">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c60a-135">Parameters</span></span>

* `callback`

<span data-ttu-id="1c60a-136">コールバックでは、情報の保存の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-136">The callback indicates the result of saving the information.</span></span>

### <a name="publishasync"></a><span data-ttu-id="1c60a-137">publishAsync</span><span class="sxs-lookup"><span data-stu-id="1c60a-137">publishAsync</span></span>
`- (void)publishAsync:(nonnull void (^)(MCDRemoteSystemAppRegistrationPublishResult* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="1c60a-138">他のアプリケーションが検出できるように、MCDRemoteSystemAppRegistration に格納されている情報を公開します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-138">Publishes the information currently stored in the MCDRemoteSystemAppRegistration such that other applications can discover it.</span></span>

> [!NOTE] 
> <span data-ttu-id="1c60a-139">この呼び出しが成功するには、MCDConnectedDevicesNotificationRegistration を登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c60a-139">MCDConnectedDevicesNotificationRegistration must be registered for this call to succeed.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1c60a-140">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c60a-140">Parameters</span></span>

* `callback`

<span data-ttu-id="1c60a-141">コールバックでは、情報の保存の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="1c60a-141">The callback indicates the result of saving the information.</span></span>
