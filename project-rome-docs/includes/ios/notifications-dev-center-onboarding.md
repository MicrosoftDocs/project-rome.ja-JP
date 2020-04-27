---
title: インクルード ファイル
description: インクルード ファイル
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "58909294"
---
### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="7f7c3-103">プッシュ通知のためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="7f7c3-103">Register your app for push notifications</span></span>

<span data-ttu-id="7f7c3-104">[Apple Push Notification](https://developer.apple.com/notifications/) のサポートのためにアプリケーションを Apple に登録します。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-104">Register your application with Apple for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="7f7c3-105">受け取った送信者 ID とサーバー キーは、後で必要になるので必ずメモしておいてください。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-105">Be sure to make note of the sender ID and server key that you receive as you'll need them later.</span></span>

<span data-ttu-id="7f7c3-106">登録したら、アプリ内で、プッシュ通知機能を Connected Devices Platform に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-106">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="7f7c3-107">Microsoft Windows デベロッパー センターでクロスデバイス エクスペリエンスのためにアプリを登録する</span><span class="sxs-lookup"><span data-stu-id="7f7c3-107">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>

> [!WARNING]
> <span data-ttu-id="7f7c3-108">この手順は、Project Rome の機能を使用して非 Windows デバイスからデータにアクセスする、またはそのデバイスの要求を実行する場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-108">This step is only required if you want to use Project Rome features to access data from or make requests of non-Windows devices.</span></span> <span data-ttu-id="7f7c3-109">Windows デバイスのみをターゲットにする場合、この手順を完了する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-109">If you only target Windows devices, you do not need to complete this step.</span></span>

<span data-ttu-id="7f7c3-110">[Microsoft デベロッパー ダッシュボードのクロスデバイス エクスペリエンス機能](https://developer.microsoft.com/dashboard/crossplatform/web)用にアプリを登録します。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-110">Register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="7f7c3-111">これは、上記の MSA および AAD アプリ登録とは異なる手順です。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-111">This is a different procedure from MSA and AAD app registration above.</span></span> <span data-ttu-id="7f7c3-112">このプロセスの主な目的は、プラットフォーム固有のアプリ ID を、Connected Devices Platform によって認識されるクロスプラットフォームのアプリ ID にマップすることです。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-112">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform.</span></span> <span data-ttu-id="7f7c3-113">この手順により、アプリで利用するモバイル プラットフォームに対応するネイティブのプッシュ通知サービスを使用した通知の送信も有効化されます。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-113">This step will also enable sending notifications using the native push notification services corresponding to the mobile platform(s) your app utilizes.</span></span> <span data-ttu-id="7f7c3-114">iOS の場合、それによって、APNS (Apple Push Notification Service) 経由で iOS アプリのエンドポイントに通知を送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-114">For iOS, it enables notifications to be sent to iOS app endpoints via APNS – Apple Push Notification Service.</span></span>

<span data-ttu-id="7f7c3-115">デベロッパー センターのダッシュボードに移動し、左側のナビゲーション ウィンドウから [Cross-Device Experiences] (クロスデバイス エクスペリエンス) に移動して、[configuring a new cross-device app] (新しいクロスデバイス アプリの構成) を選択します。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-115">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app.</span></span>
<span data-ttu-id="7f7c3-116">![デベロッパー センター ダッシュボード – クロスデバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="7f7c3-116">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="7f7c3-117">デベロッパー センターのオンボーディング プロセスでは、次の手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-117">The Dev Center on-boarding process require the following steps:</span></span>

* <span data-ttu-id="7f7c3-118">サポートされているプラットフォームの選択 – アプリがプレゼンスを持ち、クロスデバイス エクスペリエンスが有効化されるプラットフォームを選択します。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-118">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="7f7c3-119">Graph 通知との統合の場合、使用しているプラットフォームに応じて Windows、Android、iOS から選択できます。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-119">In the case of Graph Notifications integration, you can select from Windows, Android, and/or iOS, depending on what platforms you are using.</span></span> ![クロスデバイス エクスペリエンス – サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* <span data-ttu-id="7f7c3-121">アプリ ID の指定 – 使用しているプラットフォームごとにアプリ ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-121">Provide app IDs – provide app IDs for each platform you are using.</span></span> <span data-ttu-id="7f7c3-122">iOS アプリの場合、これはプロジェクト作成時にアプリに割り当てたパッケージ名です。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-122">For iOS apps, this is the package name you assigned to your app when you created the project.</span></span> <span data-ttu-id="7f7c3-123">プラットフォームごとに (最大 10 個の) 異なる ID を追加できることに注意してください。これは、同じアプリの複数のバージョン、または複数の異なるアプリがあり、同じユーザーをターゲットにしてアプリ サーバーから送信された同じ通知をこれらのアプリで受信できるようにしたい場合です。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-123">Note that you may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> ![クロスデバイス エクスペリエンス – アプリ ID](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* <span data-ttu-id="7f7c3-125">前述した以前の MSA/AAD アプリ登録手順で取得した、MSA/AAD アプリ登録のアプリ ID を指定または選択します。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-125">Provide or select the app IDs from MSA and/or AAD app registrations obtained in the previous MSA/AAD app registration steps above.</span></span> ![クロスデバイス エクスペリエンス – MSA および AAD アプリ登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* <span data-ttu-id="7f7c3-127">ユーザーをターゲットにした通知を発行したときにアプリ サーバーから通知が配信されるよう、アプリで使用するネイティブ通知プラットフォーム (Windows の WNS、Android の FCM、iOS の APNS) の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-127">Provide your credentials for the native notification platforms relevant to your app (i.e. WNS for Windows, FCM for Android, and/or APNS for iOS) to enable delivery of notifications from your app server when you publish user-targeted notifications.</span></span> ![クロスデバイス エクスペリエンス – プッシュ資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* <span data-ttu-id="7f7c3-129">最後に、クロスデバイス アプリ ドメインを検証して、アプリがドメインの所有権を持っていること、また、それをアプリのクロスデバイス ID として使用できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7f7c3-129">Finally, verify your cross-device app domain to make sure your app has the ownership of the domain and can use it as a cross-device identity for your app.</span></span> ![クロスデバイス エクスペリエンス – ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
