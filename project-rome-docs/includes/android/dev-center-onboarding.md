---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: d8e94884c742015b08d87e83a9384cbb577695c4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907924"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="cd6db-103">プッシュ通知の暫定的なセットアップ</span><span class="sxs-lookup"><span data-stu-id="cd6db-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="cd6db-104">プッシュ通知をアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-104">Register your app for push notifications</span></span>

<span data-ttu-id="cd6db-105">Google にアプリケーションを登録[Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client)をサポートします。</span><span class="sxs-lookup"><span data-stu-id="cd6db-105">Register your application with Google for [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) support.</span></span> <span data-ttu-id="cd6db-106">送信者は受信した ID とサーバーのキーをメモしてください。後で必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd6db-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

<span data-ttu-id="cd6db-107">登録されると、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd6db-107">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="cd6db-108">Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスのアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-108">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>
<span data-ttu-id="cd6db-109">Android デバイスへの通信を必要とする場合のアプリを登録する必要があります、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-109">If you require communication to your Android device, you need to register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="cd6db-110">これは、上記 MSA と AAD のアプリ登録から別のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="cd6db-110">This is a different procedure from MSA and AAD app registration above.</span></span>  <span data-ttu-id="cd6db-111">このプロセスの主な目的は、接続されているデバイス プラットフォームによって認識され、同時に、ネイティブのプッシュ通知を使用して通知を送信するプラットフォームを承認するクロス プラットフォーム アプリの id によるプラットフォームの特定のアプリ id にマップするには各モバイル プラットフォームに対応するサービス。</span><span class="sxs-lookup"><span data-stu-id="cd6db-111">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform, and at the same time authorizes the Platform to send notifications using the native push notification services corresponding to each mobile platform.</span></span> <span data-ttu-id="cd6db-112">この場合、その、Firebase Cloud Messaging を使用して iOS アプリのエンドポイントへの通信を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="cd6db-112">In this case, it enables it enables communication to iOS app endpoints via Firebase Cloud Messaging.</span></span>

<span data-ttu-id="cd6db-113">Dev Center のダッシュ ボードに移動して、左側にあるナビゲーション ウィンドウで、クロス デバイス エクスペリエンスに移動して次のように示すように、新しいクロス デバイス アプリの構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-113">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app, shown as below.</span></span>
<span data-ttu-id="cd6db-114">![デベロッパー センター ダッシュ ボード-クロス デバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="cd6db-114">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="cd6db-115">デベロッパー センターで、オンボード プロセスには、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="cd6db-115">The Dev Center on-boarding process requires the following steps:</span></span>
* <span data-ttu-id="cd6db-116">サポートされているプラットフォームを選択します: アプリが存在する必要があり、クロス デバイス エクスペリエンスを有効にするプラットフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-116">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="cd6db-117">Windows、Android、および iOS から選択できます。</span><span class="sxs-lookup"><span data-stu-id="cd6db-117">You can select from Windows, Android, and/or iOS.</span></span>
<span data-ttu-id="cd6db-118">![クロス デバイス エクスペリエンス: サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span><span class="sxs-lookup"><span data-stu-id="cd6db-118">![Cross-Device Experiences – Supported Platforms](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span></span>

* <span data-ttu-id="cd6db-119">アプリ Id を提供: 各アプリが、プレゼンスがプラットフォームにアプリ Id を提供します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-119">Provide app IDs – provide app IDs for each of the platform where your app has a presence.</span></span> 
<span data-ttu-id="cd6db-120">![クロス デバイス エクスペリエンス: アプリ Id](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span><span class="sxs-lookup"><span data-stu-id="cd6db-120">![Cross-Device Experiences – App IDs](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span></span>
> [!NOTE]
> <span data-ttu-id="cd6db-121">プラットフォームごと (最大 10 個) の異なる Id を追加することがあります-これは、同じアプリ、または異なる場合でも、同じユーザーを対象としたアプリケーション サーバーによって送信された同じ通知を受信できるようにアプリの複数のバージョンがある場合、します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-121">You may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> 
> [!TIP] 
> <span data-ttu-id="cd6db-122">Android アプリは、これは、プロジェクトを作成したときに、アプリに割り当てたパッケージ名です。</span><span class="sxs-lookup"><span data-stu-id="cd6db-122">For Android apps, this is the Package Name you assigned to your app when you created the project.</span></span> <span data-ttu-id="cd6db-123">プロジェクトの概要の下、Firebase コンソールで、パッケージ名が見つかりません] [全般]-> [です。</span><span class="sxs-lookup"><span data-stu-id="cd6db-123">The Package Name can be found in your Firebase console under Project Overview -> General.</span></span>
<span data-ttu-id="cd6db-124">![Firebase コンソール – プロジェクトの概要](../../notifications/media/dev_center_portal/firebase_overview.png)</span><span class="sxs-lookup"><span data-stu-id="cd6db-124">![Firebase Console – Project Overview](../../notifications/media/dev_center_portal/firebase_overview.png)</span></span>

* <span data-ttu-id="cd6db-125">指定するか、MSA または AAD アプリの登録からアプリ Id を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-125">Provide or select the app IDs from MSA and/or AAD app registrations.</span></span> <span data-ttu-id="cd6db-126">MSA または AAD アプリの登録に対応するこれらのクライアント Id は、上記の前の MSA/AAD アプリ登録の手順で取得されました。</span><span class="sxs-lookup"><span data-stu-id="cd6db-126">These client IDs corresponding to MSA or AAD app registration were obtained in the previous MSA/AAD app registration steps from above.</span></span> 
<span data-ttu-id="cd6db-127">![クロス デバイス エクスペリエンス: MSA と AAD アプリの登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span><span class="sxs-lookup"><span data-stu-id="cd6db-127">![Cross-Device Experiences – MSA and AAD App Registrations](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span></span>

* <span data-ttu-id="cd6db-128">デバイス プラットフォームの機能を活用してそれぞれのエンドポイント、つまり、アプリのクライアントに通知を送信する WNS (Windows UWP) 用、GCM (Android) 用、および APNS (iOS) 用の主要なプラットフォームでネイティブ通知プラットフォームを接続します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-128">Connected Devices Platform capabilities leverage each of the native notification platforms on major platforms to send notifications down to the app client endpoints, namely, WNS (for Windows UWP), GCM (for Android) and APNS (for iOS).</span></span> <span data-ttu-id="cd6db-129">ユーザーを対象とした通知を発行するときに、アプリ サーバーの通知を配信するプラットフォームを有効にするには、これらの通知プラットフォーム用の資格情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-129">Provide your credentials for these notification platforms to enable the Platform to deliver the notifications for your app server, when you publish user-targeted notifications.</span></span>
<span data-ttu-id="cd6db-130">![クロス デバイス エクスペリエンス: プッシュの資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span><span class="sxs-lookup"><span data-stu-id="cd6db-130">![Cross-Device Experiences – Push Credentials](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span></span>
> [!NOTE] 
> <span data-ttu-id="cd6db-131">Android では、Android のデバイスと通信する前提条件は、クラウド メッセージング サービスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="cd6db-131">For Android, enabling Cloud Messaging service is a prerequisite to communicate with an Android device.</span></span> <span data-ttu-id="cd6db-132">参照してください[設定を Firebase Cloud Messaging クライアント Android でのアプリ](https://firebase.google.com/docs/cloud-messaging/android/client)の詳細。</span><span class="sxs-lookup"><span data-stu-id="cd6db-132">See [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client) for more details.</span></span> <span data-ttu-id="cd6db-133">オンボードを完了すると接続されているデバイス プラットフォームに Windows デベロッパー センターを使用してプッシュの資格情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="cd6db-133">Once you complete the onboarding, you can then provide the push credentials via Windows Dev Center to the Connected Device Platform.</span></span> 
> [!TIP] 
> <span data-ttu-id="cd6db-134">Firebase クラウド メッセージング Sender ID に対応する必須の送信者 ID と API キーがレガシ サーバー キーに対応します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-134">The required Sender ID is corresponding to Firebase Cloud Messaging Sender ID, and the API key is corresponding to Legacy Server Key.</span></span> <span data-ttu-id="cd6db-135">Firebase コンソールで見つかります両方プロジェクト->-> 設定 の Cloud Messaging タブで、スクリーン ショットに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="cd6db-135">Both can be found in Firebase Console -> Project -> Settings, under the Cloud Messaging tab, as shown in the screenshot.</span></span>
<span data-ttu-id="cd6db-136">![Firebase コンソール – Android のプッシュの資格情報](../../notifications/media/dev_center_portal/firebase_push_creds.png)</span><span class="sxs-lookup"><span data-stu-id="cd6db-136">![Firebase Console – Android Push Credentials](../../notifications/media/dev_center_portal/firebase_push_creds.png)</span></span>

* <span data-ttu-id="cd6db-137">最後の手順では、アプリではこのドメインの所有権に登録されているアプリのクロス デバイス アプリ id のように機能することを証明する検証プロセスとして機能するクロス デバイス アプリ ドメインを確認します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-137">The last step is to verify your cross-device app domain, which serves as a verification process to prove that your app has the ownership of this domain which acts like a cross-device app identity for the app you registered.</span></span>
<span data-ttu-id="cd6db-138">![クロス デバイス エクスペリエンス: ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span><span class="sxs-lookup"><span data-stu-id="cd6db-138">![Cross-Device Experiences – Domain Verification](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span></span>

### <a name="process-notifications-as-they-are-received-by-the-app"></a><span data-ttu-id="cd6db-139">アプリで受信した通知を処理します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-139">Process notifications as they are received by the app</span></span>

<span data-ttu-id="cd6db-140">Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスが検証されるでやり取りされるようにアプリが通知を処理できますを確認します。</span><span class="sxs-lookup"><span data-stu-id="cd6db-140">Once the Cross-Device experience within the Microsoft Windows Dev Center has been validated, make sure your app can process the notifications as they come in.</span></span> 

```Java
    ensurePlatformInitialized().thenAccept((ConnectedDevicesPlatform platform) -> {
            ConnectedDevicesProcessNotificationOperation operation = platform.processNotification(data);
        });
```
