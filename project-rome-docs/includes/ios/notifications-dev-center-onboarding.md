---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58909294"
---
### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="3728c-103">プッシュ通知をアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="3728c-103">Register your app for push notifications</span></span>

<span data-ttu-id="3728c-104">アプリケーションを Apple の登録[Apple Push Notification](https://developer.apple.com/notifications/)をサポートします。</span><span class="sxs-lookup"><span data-stu-id="3728c-104">Register your application with Apple for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="3728c-105">送信側を必要に応じて、後で受信した ID とサーバーのキーをメモしてください。</span><span class="sxs-lookup"><span data-stu-id="3728c-105">Be sure to make note of the sender ID and server key that you receive as you'll need them later.</span></span>

<span data-ttu-id="3728c-106">登録されると、接続されているデバイス プラットフォームと、アプリでプッシュ通知機能を関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="3728c-106">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="3728c-107">Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスのアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="3728c-107">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>

> [!WARNING]
> <span data-ttu-id="3728c-108">この手順はのみからデータにアクセスしたり、非 Windows デバイスの要求を作成するプロジェクト ローマ機能を使用するかどうかに必要です。</span><span class="sxs-lookup"><span data-stu-id="3728c-108">This step is only required if you want to use Project Rome features to access data from or make requests of non-Windows devices.</span></span> <span data-ttu-id="3728c-109">Windows デバイスのみを対象に場合、この手順を完了する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3728c-109">If you only target Windows devices, you do not need to complete this step.</span></span>

<span data-ttu-id="3728c-110">アプリケーションを登録、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。</span><span class="sxs-lookup"><span data-stu-id="3728c-110">Register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="3728c-111">これは、上記 MSA と AAD のアプリ登録から別のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="3728c-111">This is a different procedure from MSA and AAD app registration above.</span></span> <span data-ttu-id="3728c-112">このプロセスの主な目的は、接続されているデバイス プラットフォームによって認識されるクロス プラットフォーム アプリの id によるプラットフォームの特定のアプリ id にマップします。</span><span class="sxs-lookup"><span data-stu-id="3728c-112">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform.</span></span> <span data-ttu-id="3728c-113">この手順は、アプリを利用するモバイル プラットフォームに対応するネイティブのプッシュ通知サービスを使用して通知の送信も有効になります。</span><span class="sxs-lookup"><span data-stu-id="3728c-113">This step will also enable sending notifications using the native push notification services corresponding to the mobile platform(s) your app utilizes.</span></span> <span data-ttu-id="3728c-114">Ios の APNS – Apple Push Notification Service を使用して iOS アプリのエンドポイントに送信される通知できます。</span><span class="sxs-lookup"><span data-stu-id="3728c-114">For iOS, it enables notifications to be sent to iOS app endpoints via APNS – Apple Push Notification Service.</span></span>

<span data-ttu-id="3728c-115">Dev Center のダッシュ ボードに移動して、左側にあるナビゲーション ウィンドウで、クロス デバイス エクスペリエンスに移動して新しいクロス デバイス アプリの構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="3728c-115">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app.</span></span>
<span data-ttu-id="3728c-116">![デベロッパー センター ダッシュ ボード-クロス デバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="3728c-116">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="3728c-117">デベロッパー センターで、オンボード プロセスには、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="3728c-117">The Dev Center on-boarding process require the following steps:</span></span>

* <span data-ttu-id="3728c-118">サポートされているプラットフォームを選択します: アプリが存在する必要があり、クロス デバイス エクスペリエンスを有効にするプラットフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="3728c-118">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="3728c-119">グラフの通知の統合の場合は、Windows、Android、iOS、お使いのプラットフォームに応じてから選択できます。</span><span class="sxs-lookup"><span data-stu-id="3728c-119">In the case of Graph Notifications integration, you can select from Windows, Android, and/or iOS, depending on what platforms you are using.</span></span> ![クロス デバイス エクスペリエンス: サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* <span data-ttu-id="3728c-121">アプリ Id を提供: を使用する各プラットフォームのアプリ Id を提供します。</span><span class="sxs-lookup"><span data-stu-id="3728c-121">Provide app IDs – provide app IDs for each platform you are using.</span></span> <span data-ttu-id="3728c-122">IOS アプリの場合は、これは、プロジェクトを作成したときに、アプリに割り当てたパッケージ名です。</span><span class="sxs-lookup"><span data-stu-id="3728c-122">For iOS apps, this is the package name you assigned to your app when you created the project.</span></span> <span data-ttu-id="3728c-123">プラットフォームごと (最大 10 個) の異なる Id を追加することに注意してください: これは、同じアプリ、または異なる場合でも、同じユーザーを対象としたアプリケーション サーバーによって送信された同じ通知を受信できるようにアプリの複数のバージョンがある場合。</span><span class="sxs-lookup"><span data-stu-id="3728c-123">Note that you may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> ![クロス デバイス エクスペリエンス: アプリ Id](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* <span data-ttu-id="3728c-125">指定するか、前 MSA/AAD アプリ登録の手順で取得した MSA または AAD アプリの登録からのアプリ Id を選択します。</span><span class="sxs-lookup"><span data-stu-id="3728c-125">Provide or select the app IDs from MSA and/or AAD app registrations obtained in the previous MSA/AAD app registration steps above.</span></span> ![クロス デバイス エクスペリエンス: MSA と AAD アプリの登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* <span data-ttu-id="3728c-127">ユーザーを対象とした通知を発行するときに、アプリ サーバーからの通知の配信を有効にするアプリ (WNS の Windows、android では、FCM や iOS の APNS) に関連するネイティブ通知プラットフォームの資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="3728c-127">Provide your credentials for the native notification platforms relevant to your app (i.e. WNS for Windows, FCM for Android, and/or APNS for iOS) to enable delivery of notifications from your app server when you publish user-targeted notifications.</span></span> ![クロス デバイス エクスペリエンス: プッシュの資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* <span data-ttu-id="3728c-129">最後に、アプリがドメインの所有権ととして使用できますが、クロス デバイス id、アプリのことを確認するためのクロス デバイス アプリ ドメインを確認します。</span><span class="sxs-lookup"><span data-stu-id="3728c-129">Finally, verify your cross-device app domain to make sure your app has the ownership of the domain and can use it as a cross-device identity for your app.</span></span> ![クロス デバイス エクスペリエンス: ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
