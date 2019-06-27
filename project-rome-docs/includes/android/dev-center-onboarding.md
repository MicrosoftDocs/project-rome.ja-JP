---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: d8e94884c742015b08d87e83a9384cbb577695c4
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907924"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="34763-103">プッシュ通知の準備段階のセットアップ</span><span class="sxs-lookup"><span data-stu-id="34763-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="34763-104">プッシュ通知のためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="34763-104">Register your app for push notifications</span></span>

<span data-ttu-id="34763-105">[Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) のサポートのために、アプリケーションを Google に登録します。</span><span class="sxs-lookup"><span data-stu-id="34763-105">Register your application with Google for [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) support.</span></span> <span data-ttu-id="34763-106">受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。</span><span class="sxs-lookup"><span data-stu-id="34763-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

<span data-ttu-id="34763-107">登録したら、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="34763-107">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

```Java
notificationRegistration = new ConnectedDevicesNotificationRegistration();
notificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
notificationRegistration.setToken(token);
notificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
notificationRegistration.setAppDisplayName("SampleApp");

mConnectedDevicesPlatform.getNotificationRegistrationManager().registerForAccountAsync(mConnectedDevicesAccount).whenComplete(() -> {
  // Now that notifications are registered, this account can receive replies to commands and incoming commands.
});
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="34763-108">Microsoft Windows デベロッパー センターでクロスデバイス エクスペリエンスのためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="34763-108">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>
<span data-ttu-id="34763-109">Android デバイスとの通信が必要な場合、[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34763-109">If you require communication to your Android device, you need to register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="34763-110">これは、上記の MSA および AAD アプリ登録とは異なる手順です。</span><span class="sxs-lookup"><span data-stu-id="34763-110">This is a different procedure from MSA and AAD app registration above.</span></span>  <span data-ttu-id="34763-111">このプロセスの主な目的は、プラットフォーム固有のアプリ ID を、Connected Devices Platform によって認識されるクロスプラットフォームのアプリ ID にマップすること、またそれと同時に、プラットフォームにおいて、各モバイル プラットフォームに対応したネイティブのプッシュ通知サービスを使用して通知を送信するのを認可することです。</span><span class="sxs-lookup"><span data-stu-id="34763-111">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform, and at the same time authorizes the Platform to send notifications using the native push notification services corresponding to each mobile platform.</span></span> <span data-ttu-id="34763-112">この場合、それによって、Firebase Cloud Messaging 経由で iOS アプリのエンドポイントと通信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="34763-112">In this case, it enables it enables communication to iOS app endpoints via Firebase Cloud Messaging.</span></span>

<span data-ttu-id="34763-113">次に示すように、デベロッパー センターのダッシュボードに移動し、左側のナビゲーション ウィンドウから [Cross-Device Experiences] (クロスデバイス エクスペリエンス) に移動して、[configuring a new cross-device app] (新しいクロスデバイス アプリの構成) を選択します。</span><span class="sxs-lookup"><span data-stu-id="34763-113">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app, shown as below.</span></span>
<span data-ttu-id="34763-114">![デベロッパー センター ダッシュボード – クロスデバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="34763-114">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="34763-115">デベロッパー センターのオンボーディング プロセスでは、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="34763-115">The Dev Center on-boarding process requires the following steps:</span></span>
* <span data-ttu-id="34763-116">サポートされているプラットフォームの選択 – アプリがプレゼンスを持ち、クロスデバイス エクスペリエンスが有効化されるプラットフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="34763-116">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="34763-117">Windows、Android、iOS から選択できます。</span><span class="sxs-lookup"><span data-stu-id="34763-117">You can select from Windows, Android, and/or iOS.</span></span>
<span data-ttu-id="34763-118">![クロスデバイス エクスペリエンス – サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span><span class="sxs-lookup"><span data-stu-id="34763-118">![Cross-Device Experiences – Supported Platforms](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span></span>

* <span data-ttu-id="34763-119">アプリ ID の指定 – アプリがプレゼンスを持っているプラットフォームごとにアプリ ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="34763-119">Provide app IDs – provide app IDs for each of the platform where your app has a presence.</span></span> 
<span data-ttu-id="34763-120">![クロスデバイス エクスペリエンス – アプリ ID](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span><span class="sxs-lookup"><span data-stu-id="34763-120">![Cross-Device Experiences – App IDs](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span></span>
> [!NOTE]
> <span data-ttu-id="34763-121">プラットフォームごとに (最大 10 個の) 異なる ID を追加できます。これは、同じアプリの複数のバージョン、または複数の異なるアプリがあり、同じユーザーをターゲットにしてアプリ サーバーから送信された同じ通知をこれらのアプリで受信できるようにしたい場合です。</span><span class="sxs-lookup"><span data-stu-id="34763-121">You may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> 
> [!TIP] 
> <span data-ttu-id="34763-122">Android アプリの場合、これはプロジェクト作成時にアプリに割り当てたパッケージ名です。</span><span class="sxs-lookup"><span data-stu-id="34763-122">For Android apps, this is the Package Name you assigned to your app when you created the project.</span></span> <span data-ttu-id="34763-123">パッケージ名は、Firebase コンソールで [Project Overview] (プロジェクトの概要) -> [General] (全般) から確認できます。</span><span class="sxs-lookup"><span data-stu-id="34763-123">The Package Name can be found in your Firebase console under Project Overview -> General.</span></span>
<span data-ttu-id="34763-124">![Firebase コンソール – プロジェクトの概要](../../notifications/media/dev_center_portal/firebase_overview.png)</span><span class="sxs-lookup"><span data-stu-id="34763-124">![Firebase Console – Project Overview](../../notifications/media/dev_center_portal/firebase_overview.png)</span></span>

* <span data-ttu-id="34763-125">MSA/AAD アプリ登録のアプリ ID を指定または選択します。</span><span class="sxs-lookup"><span data-stu-id="34763-125">Provide or select the app IDs from MSA and/or AAD app registrations.</span></span> <span data-ttu-id="34763-126">MSA または AAD アプリ登録に対応するこれらのクライアント ID は、前述した以前の MSA/AAD アプリ登録手順で取得しました。</span><span class="sxs-lookup"><span data-stu-id="34763-126">These client IDs corresponding to MSA or AAD app registration were obtained in the previous MSA/AAD app registration steps from above.</span></span> 
<span data-ttu-id="34763-127">![クロスデバイス エクスペリエンス – MSA および AAD アプリ登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span><span class="sxs-lookup"><span data-stu-id="34763-127">![Cross-Device Experiences – MSA and AAD App Registrations](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span></span>

* <span data-ttu-id="34763-128">Connected Devices Platform の機能は、主要プラットフォームの各ネイティブ通知プラットフォーム、具体的には WNS (Windows UWP)、GCM (Android)、および APNS (iOS) を利用してアプリ クライアント エンドポイントに通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="34763-128">Connected Devices Platform capabilities leverage each of the native notification platforms on major platforms to send notifications down to the app client endpoints, namely, WNS (for Windows UWP), GCM (for Android) and APNS (for iOS).</span></span> <span data-ttu-id="34763-129">ユーザーをターゲットにした通知を発行したときにプラットフォームがアプリ サーバーの通知を配信できるよう、これらの通知プラットフォームの資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="34763-129">Provide your credentials for these notification platforms to enable the Platform to deliver the notifications for your app server, when you publish user-targeted notifications.</span></span>
<span data-ttu-id="34763-130">![クロスデバイス エクスペリエンス – プッシュ資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span><span class="sxs-lookup"><span data-stu-id="34763-130">![Cross-Device Experiences – Push Credentials](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span></span>
> [!NOTE] 
> <span data-ttu-id="34763-131">Android の場合、Cloud Messaging サービスの有効化は、Android デバイスと通信するための前提条件です。</span><span class="sxs-lookup"><span data-stu-id="34763-131">For Android, enabling Cloud Messaging service is a prerequisite to communicate with an Android device.</span></span> <span data-ttu-id="34763-132">詳細については、[Android での Firebase Cloud Messaging クライアント アプリの設定](https://firebase.google.com/docs/cloud-messaging/android/client)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="34763-132">See [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client) for more details.</span></span> <span data-ttu-id="34763-133">オンボーディングが完了したら、Windows デベロッパー センターから Connected Device Platform にプッシュ資格情報を提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="34763-133">Once you complete the onboarding, you can then provide the push credentials via Windows Dev Center to the Connected Device Platform.</span></span> 
> [!TIP] 
> <span data-ttu-id="34763-134">必要な送信者 ID は Firebase Cloud Messaging の Sender ID に対応し、API キーは Legacy Server Key (従来のサーバー キー) に対応します。</span><span class="sxs-lookup"><span data-stu-id="34763-134">The required Sender ID is corresponding to Firebase Cloud Messaging Sender ID, and the API key is corresponding to Legacy Server Key.</span></span> <span data-ttu-id="34763-135">スクリーンショットに示すように、どちらも Firebase コンソールの [Project] (プロジェクト) -> [Settings] (設定) の [Cloud Messaging] タブにあります。</span><span class="sxs-lookup"><span data-stu-id="34763-135">Both can be found in Firebase Console -> Project -> Settings, under the Cloud Messaging tab, as shown in the screenshot.</span></span>
<span data-ttu-id="34763-136">![Firebase コンソール – Android プッシュ資格情報](../../notifications/media/dev_center_portal/firebase_push_creds.png)</span><span class="sxs-lookup"><span data-stu-id="34763-136">![Firebase Console – Android Push Credentials](../../notifications/media/dev_center_portal/firebase_push_creds.png)</span></span>

* <span data-ttu-id="34763-137">最後の手順では、クロスデバイス アプリ ドメインを検証します。これには、登録したアプリのクロスデバイス アプリ ID のように機能するこのドメインの所有権をアプリが持っていることを証明する検証プロセスとしての役割があります。</span><span class="sxs-lookup"><span data-stu-id="34763-137">The last step is to verify your cross-device app domain, which serves as a verification process to prove that your app has the ownership of this domain which acts like a cross-device app identity for the app you registered.</span></span>
<span data-ttu-id="34763-138">![クロスデバイス エクスペリエンス – ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span><span class="sxs-lookup"><span data-stu-id="34763-138">![Cross-Device Experiences – Domain Verification](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span></span>

### <a name="process-notifications-as-they-are-received-by-the-app"></a><span data-ttu-id="34763-139">アプリで受信した通知の処理</span><span class="sxs-lookup"><span data-stu-id="34763-139">Process notifications as they are received by the app</span></span>

<span data-ttu-id="34763-140">Microsoft Windows デベロッパー センター内でクロスデバイス エクスペリエンスが検証されたら、通知を受信したときにアプリがそれを処理できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="34763-140">Once the Cross-Device experience within the Microsoft Windows Dev Center has been validated, make sure your app can process the notifications as they come in.</span></span> 

```Java
    ensurePlatformInitialized().thenAccept((ConnectedDevicesPlatform platform) -> {
            ConnectedDevicesProcessNotificationOperation operation = platform.processNotification(data);
        });
```
