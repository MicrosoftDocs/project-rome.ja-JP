---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: b03420e0229bed45fba5a079b955d62165a6b642
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907604"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="6c336-103">プッシュ通知の準備段階のセットアップ</span><span class="sxs-lookup"><span data-stu-id="6c336-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="6c336-104">プッシュ通知のためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="6c336-104">Register your app for push notifications</span></span>

<span data-ttu-id="6c336-105">[Apple Push Notification](https://developer.apple.com/notifications/) のサポートのためにアプリケーションを Apple に登録します。</span><span class="sxs-lookup"><span data-stu-id="6c336-105">Register your application with Apple for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="6c336-106">受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。</span><span class="sxs-lookup"><span data-stu-id="6c336-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

<span data-ttu-id="6c336-107">登録したら、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c336-107">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="6c336-108">Microsoft Windows デベロッパー センターでクロスデバイス エクスペリエンスのためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="6c336-108">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>
<span data-ttu-id="6c336-109">iOS デバイスとの通信が必要な場合、Microsoft Windows デベロッパー センターで登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c336-109">If you require communication to your iOS device, you'll need to register with the Microsoft Windows Dev Center.</span></span>  <span data-ttu-id="6c336-110">次に、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c336-110">Next, you need to register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="6c336-111">これは、上記の MSA および AAD アプリ登録とは異なる手順です。</span><span class="sxs-lookup"><span data-stu-id="6c336-111">This is a different procedure from MSA and AAD app registration above.</span></span> <span data-ttu-id="6c336-112">このプロセスの主な目的は、プラットフォーム固有のアプリ ID を、Connected Devices Platform によって認識されるクロスプラットフォームのアプリ ID にマップすること、またそれと同時に、プラットフォームにおいて、各モバイル プラットフォームに対応したネイティブのプッシュ通知サービスを使用して通知を送信するのを認可することです。</span><span class="sxs-lookup"><span data-stu-id="6c336-112">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform, and at the same time authorizes the Platform to send notifications using the native push notification services corresponding to each mobile platform.</span></span> <span data-ttu-id="6c336-113">この場合、それによって、APNs (Apple Push Notification Service) 経由で iOS アプリのエンドポイントと通信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6c336-113">In this case, it enables communication to iOS app endpoints via APNs – Apple Push Notification Service.</span></span> <span data-ttu-id="6c336-114">デベロッパー センターのダッシュボードに移動し、左側のナビゲーション ウィンドウから [Cross-Device Experiences] (クロスデバイス エクスペリエンス) に移動して、[configuring a new cross-device app] (新しいクロスデバイス アプリの構成) を選択します。</span><span class="sxs-lookup"><span data-stu-id="6c336-114">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app.</span></span>
<span data-ttu-id="6c336-115">![デベロッパー センター ダッシュボード – クロスデバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="6c336-115">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="6c336-116">デベロッパー センターのオンボーディング プロセスでは、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="6c336-116">The Dev Center on-boarding process require the following steps:</span></span>
* <span data-ttu-id="6c336-117">サポートされているプラットフォームの選択 – アプリがプレゼンスを持ち、クロスデバイス エクスペリエンスが有効化されるプラットフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="6c336-117">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="6c336-118">Windows、Android、iOS から選択できます。</span><span class="sxs-lookup"><span data-stu-id="6c336-118">You can select from Windows, Android, and/or iOS.</span></span>
<span data-ttu-id="6c336-119">![クロスデバイス エクスペリエンス – サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span><span class="sxs-lookup"><span data-stu-id="6c336-119">![Cross-Device Experiences – Supported Platforms](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span></span>

* <span data-ttu-id="6c336-120">アプリ ID の指定 – アプリがプレゼンスを持っているプラットフォームごとにアプリ ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c336-120">Provide app IDs – provide app IDs for each of the platform where your app has a presence.</span></span>
<span data-ttu-id="6c336-121">![クロスデバイス エクスペリエンス – アプリ ID](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span><span class="sxs-lookup"><span data-stu-id="6c336-121">![Cross-Device Experiences – App IDs](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span></span>
> [!NOTE]
> <span data-ttu-id="6c336-122">プラットフォームごとに (最大 10 個の) 異なる ID を追加できます。これは、同じアプリの複数のバージョン、または複数の異なるアプリがあり、同じユーザーをターゲットにしてアプリ サーバーから送信された同じ通知をこれらのアプリで受信できるようにしたい場合です。</span><span class="sxs-lookup"><span data-stu-id="6c336-122">You may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> 
> [!TIP] 
> <span data-ttu-id="6c336-123">iOS アプリの場合、これはプロジェクト作成時にアプリに割り当てたパッケージ名です。</span><span class="sxs-lookup"><span data-stu-id="6c336-123">For iOS apps, this is the Package Name you assigned to your app when you created the project.</span></span> 

* <span data-ttu-id="6c336-124">MSA/AAD アプリ登録のアプリ ID を指定または選択します。</span><span class="sxs-lookup"><span data-stu-id="6c336-124">Provide or select the app IDs from MSA and/or AAD app registrations.</span></span> <span data-ttu-id="6c336-125">MSA または AAD アプリ登録に対応するこれらのクライアント ID は、前述した以前の MSA/AAD アプリ登録手順で取得しました。</span><span class="sxs-lookup"><span data-stu-id="6c336-125">These client IDs corresponding to MSA or AAD app registration were obtained in the previous MSA/AAD app registration steps from above.</span></span>
<span data-ttu-id="6c336-126">![クロスデバイス エクスペリエンス – MSA および AAD アプリ登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span><span class="sxs-lookup"><span data-stu-id="6c336-126">![Cross-Device Experiences – MSA and AAD App Registrations](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span></span>
* <span data-ttu-id="6c336-127">Connected Devices Platform の機能は、主要プラットフォームの各ネイティブ通知プラットフォーム、具体的には WNS (Windows UWP)、GCM (Android)、および APNs (iOS) を利用してアプリ クライアント エンドポイントに通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="6c336-127">Connected Devices Platform capabilities leverages each of the native notification platforms on major platforms to send notifications down to the app client endpoints, namely, WNS (for Windows UWP), GCM (for Android) and APNs (for iOS).</span></span> <span data-ttu-id="6c336-128">ユーザーをターゲットにした通知を発行したときにプラットフォームがアプリ サーバーの通知を配信できるよう、これらの通知プラットフォームの資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c336-128">Provide your credentials for these notification platforms to enable the Platform to deliver the notifications for your app server, when you publish user-targeted notifications.</span></span> 
<span data-ttu-id="6c336-129">![クロスデバイス エクスペリエンス – プッシュ資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span><span class="sxs-lookup"><span data-stu-id="6c336-129">![Cross-Device Experiences – Push Credentials](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span></span>
> [!NOTE] 
> <span data-ttu-id="6c336-130">iOS の場合、APNs の有効化は iOS デバイスと通信するための前提条件です。</span><span class="sxs-lookup"><span data-stu-id="6c336-130">For iOS, enabling APNs is a prerequisite to communication to an iOS device.</span></span> <span data-ttu-id="6c336-131">詳細については、[APNs の概要](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c336-131">See [APNs Overview](https://developer.apple.com/library/archive/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW1) for more details.</span></span> <span data-ttu-id="6c336-132">オンボーディングが完了したら、Windows デベロッパー センターから Connected Device Platform にプッシュ資格情報を提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6c336-132">Once you complete the onboarding, you can then provide the push credentials via Windows Dev Center to the Connected Device Platform.</span></span> 
* <span data-ttu-id="6c336-133">最後の手順では、クロスデバイス アプリ ドメインを検証します。これには、登録したアプリのクロスデバイス アプリ ID のように機能するこのドメインの所有権をアプリが持っていることを証明する検証プロセスとしての役割があります。</span><span class="sxs-lookup"><span data-stu-id="6c336-133">The last step is to verify your cross-device app domain, which serves as a verification process to prove that your app has the ownership of this domain which acts like a cross-device app identity for the app you registered.</span></span>
<span data-ttu-id="6c336-134">![クロスデバイス エクスペリエンス – ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span><span class="sxs-lookup"><span data-stu-id="6c336-134">![Cross-Device Experiences – Domain Verification](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span></span>

### <a name="process-notifications-as-they-are-received-by-the-app"></a><span data-ttu-id="6c336-135">アプリで受信した通知の処理</span><span class="sxs-lookup"><span data-stu-id="6c336-135">Process notifications as they are received by the app</span></span>

<span data-ttu-id="6c336-136">Microsoft Windows デベロッパー センター内でクロスデバイス エクスペリエンスが検証されたら、通知を受信したときにアプリがそれを処理できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="6c336-136">Once the Cross-Device experience within the Microsoft Windows Dev Center has been validated, make sure your app can process the notifications as they come in.</span></span> 

```ObjectiveC
`MCDConnectedDevicesProcessNotificationOperation* processOperation = [_platformManager.platform processNotification:notificationInfo];`
```