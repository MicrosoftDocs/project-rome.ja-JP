---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: b03420e0229bed45fba5a079b955d62165a6b642
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907604"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="da0b7-103">プッシュ通知の暫定的なセットアップ</span><span class="sxs-lookup"><span data-stu-id="da0b7-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="da0b7-104">プッシュ通知をアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-104">Register your app for push notifications</span></span>

<span data-ttu-id="da0b7-105">アプリケーションを Apple の登録[Apple Push Notification](https://developer.apple.com/notifications/)をサポートします。</span><span class="sxs-lookup"><span data-stu-id="da0b7-105">Register your application with Apple for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="da0b7-106">送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。</span><span class="sxs-lookup"><span data-stu-id="da0b7-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

<span data-ttu-id="da0b7-107">登録されると、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="da0b7-107">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

```ObjectiveC
self.notificationRegistration = [[MCDConnectedDevicesNotificationRegistration alloc] init];
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        self.notificationRegistration.type = MCDNotificationTypeAPN;
    }
    else
    {
        self.notificationRegistration.type = MCDNotificationTypePolling;
    }
    self.notificationRegistration.appId = [[NSBundle mainBundle] bundleIdentifier];
    self.notificationRegistration.appDisplayName = (NSString*)[[NSBundle mainBundle] objectForInfoDictionaryKey:@"CFBundleDisplayName"];
    self.notificationRegistration.token = deviceToken;
    self.isRegisteredWithToken = YES;
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="da0b7-108">Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスのアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-108">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>
<span data-ttu-id="da0b7-109">IOS デバイスへの通信が必要な場合は、Microsoft Windows デベロッパー センターに登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da0b7-109">If you require communication to your iOS device, you'll need to register with the Microsoft Windows Dev Center.</span></span>  <span data-ttu-id="da0b7-110">次に、アプリケーションを登録する必要があります、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-110">Next, you need to register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="da0b7-111">これは、上記 MSA と AAD のアプリ登録から別のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="da0b7-111">This is a different procedure from MSA and AAD app registration above.</span></span> <span data-ttu-id="da0b7-112">このプロセスの主な目的は、接続されているデバイス プラットフォームによって認識され、同時に、ネイティブのプッシュ通知を使用して通知を送信するプラットフォームを承認するクロス プラットフォーム アプリの id によるプラットフォームの特定のアプリ id にマップするには各モバイル プラットフォームに対応するサービス。</span><span class="sxs-lookup"><span data-stu-id="da0b7-112">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform, and at the same time authorizes the Platform to send notifications using the native push notification services corresponding to each mobile platform.</span></span> <span data-ttu-id="da0b7-113">この場合、APNs – Apple Push Notification Service を使用して iOS アプリのエンドポイントへの通信ができます。</span><span class="sxs-lookup"><span data-stu-id="da0b7-113">In this case, it enables communication to iOS app endpoints via APNs – Apple Push Notification Service.</span></span> <span data-ttu-id="da0b7-114">Dev Center のダッシュ ボードに移動して、左側にあるナビゲーション ウィンドウで、クロス デバイス エクスペリエンスに移動して新しいクロス デバイス アプリの構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-114">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app.</span></span>
<span data-ttu-id="da0b7-115">![デベロッパー センター ダッシュ ボード-クロス デバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="da0b7-115">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="da0b7-116">デベロッパー センターで、オンボード プロセスには、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="da0b7-116">The Dev Center on-boarding process require the following steps:</span></span>
* <span data-ttu-id="da0b7-117">サポートされているプラットフォームを選択します: アプリが存在する必要があり、クロス デバイス エクスペリエンスを有効にするプラットフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-117">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="da0b7-118">Windows、Android、および iOS から選択できます。</span><span class="sxs-lookup"><span data-stu-id="da0b7-118">You can select from Windows, Android, and/or iOS.</span></span>
<span data-ttu-id="da0b7-119">![クロス デバイス エクスペリエンス: サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span><span class="sxs-lookup"><span data-stu-id="da0b7-119">![Cross-Device Experiences – Supported Platforms](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span></span>

* <span data-ttu-id="da0b7-120">アプリ Id を提供: 各アプリが、プレゼンスがプラットフォームにアプリ Id を提供します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-120">Provide app IDs – provide app IDs for each of the platform where your app has a presence.</span></span>
<span data-ttu-id="da0b7-121">![クロス デバイス エクスペリエンス: アプリ Id](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span><span class="sxs-lookup"><span data-stu-id="da0b7-121">![Cross-Device Experiences – App IDs](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span></span>
> [!NOTE]
> <span data-ttu-id="da0b7-122">プラットフォームごと (最大 10 個) の異なる Id を追加することがあります-これは、同じアプリ、または異なる場合でも、同じユーザーを対象としたアプリケーション サーバーによって送信された同じ通知を受信できるようにアプリの複数のバージョンがある場合、します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-122">You may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> 
> [!TIP] 
> <span data-ttu-id="da0b7-123">IOS アプリの場合は、これは、プロジェクトを作成したときに、アプリに割り当てたパッケージ名です。</span><span class="sxs-lookup"><span data-stu-id="da0b7-123">For iOS apps, this is the Package Name you assigned to your app when you created the project.</span></span> 

* <span data-ttu-id="da0b7-124">指定するか、MSA または AAD アプリの登録からアプリ Id を選択します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-124">Provide or select the app IDs from MSA and/or AAD app registrations.</span></span> <span data-ttu-id="da0b7-125">MSA または AAD アプリの登録に対応するこれらのクライアント Id は、上記の前の MSA/AAD アプリ登録の手順で取得されました。</span><span class="sxs-lookup"><span data-stu-id="da0b7-125">These client IDs corresponding to MSA or AAD app registration were obtained in the previous MSA/AAD app registration steps from above.</span></span>
<span data-ttu-id="da0b7-126">![クロス デバイス エクスペリエンス: MSA と AAD アプリの登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span><span class="sxs-lookup"><span data-stu-id="da0b7-126">![Cross-Device Experiences – MSA and AAD App Registrations](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span></span>
* <span data-ttu-id="da0b7-127">デバイス プラットフォームの機能活用して各エンドポイント、つまり、WNS (Windows UWP) 用、GCM (Android) 用および APNs (iOS) のアプリのクライアントに通知を送信する主要なプラットフォームでネイティブ通知プラットフォームの接続されています。</span><span class="sxs-lookup"><span data-stu-id="da0b7-127">Connected Devices Platform capabilities leverages each of the native notification platforms on major platforms to send notifications down to the app client endpoints, namely, WNS (for Windows UWP), GCM (for Android) and APNs (for iOS).</span></span> <span data-ttu-id="da0b7-128">ユーザーを対象とした通知を発行するときに、アプリ サーバーの通知を配信するプラットフォームを有効にするには、これらの通知プラットフォーム用の資格情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-128">Provide your credentials for these notification platforms to enable the Platform to deliver the notifications for your app server, when you publish user-targeted notifications.</span></span> 
<span data-ttu-id="da0b7-129">![クロス デバイス エクスペリエンス: プッシュの資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span><span class="sxs-lookup"><span data-stu-id="da0b7-129">![Cross-Device Experiences – Push Credentials](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span></span>
> [!NOTE] 
> <span data-ttu-id="da0b7-130">IOS、APNs の有効化は iOS デバイスへの通信をするうえで必須です。</span><span class="sxs-lookup"><span data-stu-id="da0b7-130">For iOS, enabling APNs is a prerequisite to communication to an iOS device.</span></span> <span data-ttu-id="da0b7-131">参照してください[APNs の概要](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1)の詳細。</span><span class="sxs-lookup"><span data-stu-id="da0b7-131">See [APNs Overview](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) for more details.</span></span> <span data-ttu-id="da0b7-132">オンボードを完了すると接続されているデバイス プラットフォームに Windows デベロッパー センターを使用してプッシュの資格情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="da0b7-132">Once you complete the onboarding, you can then provide the push credentials via Windows Dev Center to the Connected Device Platform.</span></span> 
* <span data-ttu-id="da0b7-133">最後の手順では、アプリではこのドメインの所有権に登録されているアプリのクロス デバイス アプリ id のように機能することを証明する検証プロセスとして機能するクロス デバイス アプリ ドメインを確認します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-133">The last step is to verify your cross-device app domain, which serves as a verification process to prove that your app has the ownership of this domain which acts like a cross-device app identity for the app you registered.</span></span>
<span data-ttu-id="da0b7-134">![クロス デバイス エクスペリエンス: ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span><span class="sxs-lookup"><span data-stu-id="da0b7-134">![Cross-Device Experiences – Domain Verification](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span></span>

### <a name="process-notifications-as-they-are-received-by-the-app"></a><span data-ttu-id="da0b7-135">アプリで受信した通知を処理します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-135">Process notifications as they are received by the app</span></span>

<span data-ttu-id="da0b7-136">Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスが検証されるでやり取りされるようにアプリが通知を処理できますを確認します。</span><span class="sxs-lookup"><span data-stu-id="da0b7-136">Once the Cross-Device experience within the Microsoft Windows Dev Center has been validated, make sure your app can process the notifications as they come in.</span></span> 

```ObjectiveC
`MCDConnectedDevicesProcessNotificationOperation* processOperation = [_platformManager.platform processNotification:notificationInfo];`
```