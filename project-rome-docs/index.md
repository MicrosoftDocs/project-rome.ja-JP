---
title: クロスデバイス アプリケーションを構築する
description: Project Rome を使用した、Windows 10 アプリケーション対応のクロスデバイスおよびクロスプラットフォームの機能について説明します。
ms.topic: overview
ms.custom: seodec2018, RS5
ms.openlocfilehash: 13dcef5e158cf0cfd122afaef5f376ed06267790
ms.sourcegitcommit: 5bf261d8d6ebe89d6d075d851f9255c806f5a649
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91716695"
---
# <a name="project-rome"></a><span data-ttu-id="a5032-103">Project Rome</span><span class="sxs-lookup"><span data-stu-id="a5032-103">Project Rome</span></span>

<span data-ttu-id="a5032-104">[Project Rome](https://developer.microsoft.com/windows/project-rome) は、Microsoft が提供するアプリのクロスデバイス エクスペリエンス プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="a5032-104">[Project Rome](https://developer.microsoft.com/windows/project-rome) is Microsoft's cross-device experiences platform for apps.</span></span> 

<span data-ttu-id="a5032-105">このサイトには、Project Rome の開発者向けドキュメント、およびその他の有用なリソースへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a5032-105">On this site you will find developer documentation for Project Rome and links to other useful resources.</span></span>

<span data-ttu-id="a5032-106">Project Rome に関するニュース、ブログ記事、ビデオについては、[Project Rome のランディング ページ](https://developer.microsoft.com/windows/project-rome)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a5032-106">For news, blog posts, and videos about Project Rome, visit the [Project Rome landing page](https://developer.microsoft.com/windows/project-rome).</span></span>

<span data-ttu-id="a5032-107">Project Rome を使用するサンプル アプリケーションについては、下記の SDK の表を確認するか、[Project Rome のサンプル リポジトリ](https://github.com/Microsoft/project-rome)にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="a5032-107">For sample applications using Project Rome, check out the SDK table below, or visit the [Project Rome samples repo](https://github.com/Microsoft/project-rome).</span></span>

## <a name="about-project-rome"></a><span data-ttu-id="a5032-108">Project Rome について</span><span class="sxs-lookup"><span data-stu-id="a5032-108">About Project Rome</span></span>

<span data-ttu-id="a5032-109">Project Rome を使用する開発者は、複数のデバイスで実行可能で、かつデバイスを切り替える際にユーザーと一緒に切り替え先のデバイスに移動できるアプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a5032-109">Project Rome allows developers to write apps that can run on multiple devices and travel with the user as they switch between devices.</span></span>

<span data-ttu-id="a5032-110">Project Rome には、Microsoft Graph およびプラットフォーム固有のネイティブ SDK を介して公開される機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a5032-110">Project Rome includes features exposed via Microsoft Graph and platform-specific native SDKs.</span></span> <span data-ttu-id="a5032-111">これらの機能により、複数のクロスデバイス機能とコネクテッド デバイス機能が有効になり、ログインしたユーザー ID を軸としてアプリを一元管理できます。</span><span class="sxs-lookup"><span data-stu-id="a5032-111">These features enable multiple cross-device and connected-device capabilities, allowing your apps to be centralized around a logged-in user identity.</span></span> <span data-ttu-id="a5032-112">Project Rome に関連付けられた機能には、ユーザーのアクティビティ、通知、デバイス リレー、近距離共有などがありますが、これらに限定されるものではありません。</span><span class="sxs-lookup"><span data-stu-id="a5032-112">Features associated with Project Rome include but are not limited to user activities, notifications, device relay, and nearby share.</span></span>

## <a name="choosing-between-native-apis-and-graph-apis"></a><span data-ttu-id="a5032-113">ネイティブ API と Graph API の使い分け</span><span class="sxs-lookup"><span data-stu-id="a5032-113">Choosing between native APIs and Graph APIs</span></span>

<span data-ttu-id="a5032-114">シナリオによっては、ネイティブ プラットフォームの SDK と Microsoft Graph を介した REST API の*両方*から利用可能です。</span><span class="sxs-lookup"><span data-stu-id="a5032-114">Some scenarios are available through *both* the native platform SDKs and REST APIs via Microsoft Graph.</span></span> <span data-ttu-id="a5032-115">一般に、REST API を使用すると Project Rome の機能を素早く簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="a5032-115">In general, the REST APIs enable quick and simple implementation of the Project Rome features.</span></span> <span data-ttu-id="a5032-116">ただし、プラットフォーム固有の実装を使用することで、次のような利点が得られます。</span><span class="sxs-lookup"><span data-stu-id="a5032-116">However, there are some advantages to using platform-specific implementations:</span></span>

* <span data-ttu-id="a5032-117">プラットフォーム SDK は、サーバー側の情報が変更されたときにアプリを更新するために、ネイティブ言語のオブジェクト モデル、ローカル記憶域、および発行-サブスクライブ パターンを提供します。</span><span class="sxs-lookup"><span data-stu-id="a5032-117">The platform SDKs provide an object model in the native language, local storage, and a publish-subscribe pattern to update the app when server-side information changes.</span></span>
* <span data-ttu-id="a5032-118">アプリが Windows (UWP または Win32 アプリ) で実行されている場合、ユーザーの既定のアカウントを使用する機能や、ユーザーのエンゲージメントを自動的に追跡する機能など、プラットフォーム SDK の多数の追加機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="a5032-118">If your app runs on Windows (UWP or Win32 apps), the platform SDK provides a number of additional features, such as using the users' default account and automatically tracking user engagement.</span></span>
* <span data-ttu-id="a5032-119">プラットフォーム SDK を介してしか使用できない他の Project Rome 機能を使用する予定の場合は、それぞれの機能を同じ方法で実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a5032-119">If you plan to use other Project Rome features that are only available through the platform SDKs, you may wish to implement each of the features in the same way.</span></span>

<span data-ttu-id="a5032-120">シナリオによっては、Microsoft Graph API とクライアント SDK を組み合わせて使用することで有効になるものもあります。</span><span class="sxs-lookup"><span data-stu-id="a5032-120">Some other scenarios are enabled by using a combination of Microsoft Graph APIs and client SDKs.</span></span> <span data-ttu-id="a5032-121">通知がその例になります。</span><span class="sxs-lookup"><span data-stu-id="a5032-121">An example of this is Notifications.</span></span> <span data-ttu-id="a5032-122">この場合、MS Graph API を使用してアプリ サーバー側からの通知を公開し、ネイティブ プラットフォームのクライアント SDK を使用して各クライアント側のネイティブ アプリで通知を受信および管理します。</span><span class="sxs-lookup"><span data-stu-id="a5032-122">In this case, MS Graph API is used to publish notifications from app server side, and the native-platform client SDKs are utilized to receive and manage notifications in each client-side native apps.</span></span>

## <a name="sdk"></a><span data-ttu-id="a5032-123">SDK</span><span class="sxs-lookup"><span data-stu-id="a5032-123">SDK</span></span>

<span data-ttu-id="a5032-124">Project Rome は現在、以下のプラットフォームに対して実装されています。</span><span class="sxs-lookup"><span data-stu-id="a5032-124">Project Rome is currently implemented for the below platforms.</span></span> <span data-ttu-id="a5032-125">サンプルと SDK のダウンロードについては、各リンク先をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a5032-125">Follow the links for samples and SDK downloads.</span></span>

[windows-sdk]:             https://developer.microsoft.com/windows/downloads
[windows-sdk-badge]:       https://img.shields.io/badge/sdk-April%202018%20Update-brightgreen.svg
[windows-drsample]:        https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/RemoteSystems
[windows-afsample]:        https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/UserActivity 

[winredist-sdk]:           https://www.nuget.org/packages/Microsoft.ConnectedDevices.UserNotifications
[winredist-sdk-badge]:     https://img.shields.io/nuget/v/Microsoft.ConnectedDevices.UserNotifications.svg
[winredist-sample]:        https://github.com/microsoft/project-rome/tree/master/Windows/samples

[xamarin-sdk]:             https://www.nuget.org/packages/Microsoft.ConnectedDevices.Xamarin.Droid
[xamarin-sdk-badge]:       https://img.shields.io/nuget/v/Microsoft.ConnectedDevices.Xamarin.Droid.svg
[xamarin-sample]:          https://github.com/Microsoft/project-rome/tree/0.8.1/Xamarin/samples

[ios-sdk]:                 https://cocoapods.org/pods/ProjectRomeSdk
[ios-sdk-badge]:           https://img.shields.io/cocoapods/v/ProjectRomeSdk.svg
[ios-sample]:              https://github.com/microsoft/project-rome/tree/master/iOS/samples

[android-sdk]:             https://bintray.com/connecteddevices/maven/com.microsoft.connecteddevices%3Aconnecteddevices-sdk/_latestVersion
[android-sdk-badge]:       https://api.bintray.com/packages/connecteddevices/maven/com.microsoft.connecteddevices%3Aconnecteddevices-sdk/images/download.svg
[android-sample]:          https://github.com/microsoft/project-rome/tree/master/Android/samples

[graph-relay]:             https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview
[graph-activities]:        https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/activity-feed-api-overview
[graph-notification]:      https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview

[graph-relay-badge]:       https://img.shields.io/badge/Device_Relay-Beta-orange.svg
[graph-activities-badge]:  https://img.shields.io/badge/Activities-1.0-brightgreen.svg
[graph-notification-badge]:https://img.shields.io/badge/Graph_Notifications-Beta-orange.svg

[graph-relay-sample]:        https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview
[graph-activities-sample]:   https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/activity-feed-api-overview
[graph-notification-sample]: https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview



|   <span data-ttu-id="a5032-126">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="a5032-126">Platform</span></span>                        | <span data-ttu-id="a5032-127">機能</span><span class="sxs-lookup"><span data-stu-id="a5032-127">Features</span></span>                                                         |           <span data-ttu-id="a5032-128">SDK パッケージ</span><span class="sxs-lookup"><span data-stu-id="a5032-128">SDK Package</span></span>                          |   <span data-ttu-id="a5032-129">サンプル</span><span class="sxs-lookup"><span data-stu-id="a5032-129">Samples</span></span>                                       |
| :-------------------------------- | :--------------------------------------------------------------- |:---------------------------------------------- | :---------------------------------------------- |
| <span data-ttu-id="a5032-130">**Windows SDK**</span><span class="sxs-lookup"><span data-stu-id="a5032-130">**Windows SDK**</span></span>                   | <span data-ttu-id="a5032-131">デバイス リレー、アクティビティ/タイムライン</span><span class="sxs-lookup"><span data-stu-id="a5032-131">Device Relay, Activities/Timeline</span></span>                                | <span data-ttu-id="a5032-132">[![SDK][windows-sdk-badge]][windows-sdk]</span><span class="sxs-lookup"><span data-stu-id="a5032-132">[![SDK][windows-sdk-badge]][windows-sdk]</span></span>       | <span data-ttu-id="a5032-133">[Windows デバイス リレー用 Project Rome サンプル][windows-drsample]</span><span class="sxs-lookup"><span data-stu-id="a5032-133">[Project Rome for Device Relay Windows sample][windows-drsample]</span></span> <br> <span data-ttu-id="a5032-134">[Windows アクティビティ用 Project Rome サンプル][windows-afsample]</span><span class="sxs-lookup"><span data-stu-id="a5032-134">[Project Rome for Activities Windows sample][windows-afsample]</span></span>
| <span data-ttu-id="a5032-135">**Windows (プレビュー)**</span><span class="sxs-lookup"><span data-stu-id="a5032-135">**Windows (Preview)**</span></span>             |                                    <span data-ttu-id="a5032-136">Microsoft Graph 通知</span><span class="sxs-lookup"><span data-stu-id="a5032-136">Microsoft Graph Notifications</span></span> | <span data-ttu-id="a5032-137">[![Nuget][winredist-sdk-badge]][winredist-sdk]</span><span class="sxs-lookup"><span data-stu-id="a5032-137">[![Nuget][winredist-sdk-badge]][winredist-sdk]</span></span> | <span data-ttu-id="a5032-138">[Windows 用 Graph 通知サンプル][winredist-sample]</span><span class="sxs-lookup"><span data-stu-id="a5032-138">[Graph Notifications for Windows sample][winredist-sample]</span></span> 
| <span data-ttu-id="a5032-139">**Android**</span><span class="sxs-lookup"><span data-stu-id="a5032-139">**Android**</span></span>             | <span data-ttu-id="a5032-140">デバイス リレー、アクティビティ/タイムライン、Microsoft Graph 通知 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="a5032-140">Device Relay, Activities/Timeline, Microsoft Graph Notifications (Preview)</span></span> | <span data-ttu-id="a5032-141">[![Maven][android-sdk-badge]][android-sdk]</span><span class="sxs-lookup"><span data-stu-id="a5032-141">[![Maven][android-sdk-badge]][android-sdk]</span></span>     | <span data-ttu-id="a5032-142">[Android 用 Project Rome サンプル][android-sample]</span><span class="sxs-lookup"><span data-stu-id="a5032-142">[Project Rome for Android sample][android-sample]</span></span>
| <span data-ttu-id="a5032-143">**iOS**</span><span class="sxs-lookup"><span data-stu-id="a5032-143">**iOS**</span></span>                 | <span data-ttu-id="a5032-144">デバイス リレー、アクティビティ/タイムライン、Microsoft Graph 通知 (プレビュー)</span><span class="sxs-lookup"><span data-stu-id="a5032-144">Device Relay, Activities/Timeline, Microsoft Graph Notifications (Preview)</span></span> | <span data-ttu-id="a5032-145">[![CocoaPod][ios-sdk-badge]][ios-sdk]</span><span class="sxs-lookup"><span data-stu-id="a5032-145">[![CocoaPod][ios-sdk-badge]][ios-sdk]</span></span>          | <span data-ttu-id="a5032-146">[iOS 用 Project Rome サンプル][ios-sample]</span><span class="sxs-lookup"><span data-stu-id="a5032-146">[Project Rome for iOS sample][ios-sample]</span></span>
| <span data-ttu-id="a5032-147">**Android 用 Xamarin (プレビュー)**</span><span class="sxs-lookup"><span data-stu-id="a5032-147">**Xamarin for Android (Preview)**</span></span> | <span data-ttu-id="a5032-148">デバイス リレー</span><span class="sxs-lookup"><span data-stu-id="a5032-148">Device Relay</span></span>                                                     | <span data-ttu-id="a5032-149">[![Nuget][xamarin-sdk-badge]][xamarin-sdk]</span><span class="sxs-lookup"><span data-stu-id="a5032-149">[![Nuget][xamarin-sdk-badge]][xamarin-sdk]</span></span>     | <span data-ttu-id="a5032-150">[Android 用 Xamarin サンプル][xamarin-sample]</span><span class="sxs-lookup"><span data-stu-id="a5032-150">[Xamarin for Android sample][xamarin-sample]</span></span>
| <span data-ttu-id="a5032-151">**MSGraph**</span><span class="sxs-lookup"><span data-stu-id="a5032-151">**MSGraph**</span></span>                       | <span data-ttu-id="a5032-152">デバイス リレー、アクティビティ/タイムライン、Microsoft Graph 通知</span><span class="sxs-lookup"><span data-stu-id="a5032-152">Device Relay, Activities/Timeline, Microsoft Graph Notifications</span></span> | <span data-ttu-id="a5032-153">[![REST][graph-relay-badge]][graph-relay]</span><span class="sxs-lookup"><span data-stu-id="a5032-153">[![REST][graph-relay-badge]][graph-relay]</span></span><br> <span data-ttu-id="a5032-154">[![REST][graph-activities-badge]][graph-activities]</span><span class="sxs-lookup"><span data-stu-id="a5032-154">[![REST][graph-activities-badge]][graph-activities]</span></span><br><span data-ttu-id="a5032-155">[![REST][graph-notification-badge]][graph-notification]</span><span class="sxs-lookup"><span data-stu-id="a5032-155">[![REST][graph-notification-badge]][graph-notification]</span></span>          | <span data-ttu-id="a5032-156">[デバイス リレー][graph-relay-sample]</span><span class="sxs-lookup"><span data-stu-id="a5032-156">[Device Relay][graph-relay-sample]</span></span><br><span data-ttu-id="a5032-157">[アクティビティ/タイムライン][graph-activities-sample]</span><span class="sxs-lookup"><span data-stu-id="a5032-157">[Activities/Timeline][graph-activities-sample]</span></span><br><span data-ttu-id="a5032-158">[Graph 通知][graph-notification-sample]</span><span class="sxs-lookup"><span data-stu-id="a5032-158">[Graph Notifications][graph-notification-sample]</span></span>

## <a name="project-rome-blog-posts"></a><span data-ttu-id="a5032-159">Project Rome のブログ記事</span><span class="sxs-lookup"><span data-stu-id="a5032-159">Project Rome blog posts</span></span>
* [<span data-ttu-id="a5032-160">Android および iOS 向けの Project Rome SDK バージョン 1.0 を発表します。</span><span class="sxs-lookup"><span data-stu-id="a5032-160">Announcing Project Rome SDK for Android and iOS version 1.0!</span></span>](https://blogs.windows.com/windowsdeveloper/2019/01/29/announcing-project-rome-sdk-for-android-and-ios-version-1-0/)

* [<span data-ttu-id="a5032-161">Project Rome によるクロスデバイスのエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="a5032-161">Cross-device experiences with Project Rome</span></span>](https://blogs.windows.com/buildingapps/2016/10/11/cross-device-experience-with-project-rome/#iQTseFlAMJRopU9k.97)

* [<span data-ttu-id="a5032-162">ソーシャル化:Project Rome、マップ、およびソーシャル ネットワークの統合 (英語)</span><span class="sxs-lookup"><span data-stu-id="a5032-162">Going social: Project Rome, Maps, & Social Network Integration</span></span>](https://blogs.windows.com/buildingapps/2016/10/27/going-social-project-rome-maps-social-network-integration-app-dev-on-xbox-series/#SCfoEZ1q8c1yBMei.97)

* [<span data-ttu-id="a5032-163">Project Rome Android SDK の発表</span><span class="sxs-lookup"><span data-stu-id="a5032-163">Announcing Project Rome Android SDK</span></span>](https://blogs.windows.com/buildingapps/2017/02/08/announcing-project-rome-android-sdk/#obDkvwkXOGa3tcTx.97)

* [<span data-ttu-id="a5032-164">Android 用 Project Rome の更新:アプリ サービスのサポートが開始 (英語)</span><span class="sxs-lookup"><span data-stu-id="a5032-164">Project Rome for Android Update: Now with App Services Support</span></span>](https://blogs.windows.com/buildingapps/2017/03/23/project-rome-android-update-now-app-services-support/#DBm1Ic4JX8vXv2h0.97)

* [<span data-ttu-id="a5032-165">Project Rome による Android 用リモート制御コンパニオン アプリの構築</span><span class="sxs-lookup"><span data-stu-id="a5032-165">Building a Remote Control Companion App for Android with Project Rome</span></span>](https://devblogs.microsoft.com/xamarin/building-remote-control-companion-app-android-project-rome/)

* [<span data-ttu-id="a5032-166">Windows 10 Creators Update の新しい共有エクスペリエンス (英語)</span><span class="sxs-lookup"><span data-stu-id="a5032-166">New Share Experience in Windows 10 Creators Update</span></span>](https://blogs.windows.com/buildingapps/2017/04/06/new-share-experience-windows-10-creators-update/#OGskrWcLLlrCTCSH.97)

* [<span data-ttu-id="a5032-167">AppUriHandlers を使用した Web とアプリのリンク</span><span class="sxs-lookup"><span data-stu-id="a5032-167">Web-to-App Linking with AppUriHandlers</span></span>](https://blogs.windows.com/buildingapps/2016/10/14/web-to-app-linking-with-appurihandlers/#fIh7USaxBYS8JqfT.97)

* [<span data-ttu-id="a5032-168">Project Rome:デバイス、アプリ、プラットフォームの垣根を越えたユーザー エンゲージメントの促進</span><span class="sxs-lookup"><span data-stu-id="a5032-168">Project Rome: Driving user engagement across devices, apps and platforms</span></span>](https://blogs.windows.com/windowsdeveloper/2017/05/16/project-rome-driving-user-engagement-across-devices-apps-platforms/#jsUX3bEM6c8SpkIF.97)

* [<span data-ttu-id="a5032-169">UWP と Project Rome を使って接続アプリを構築する</span><span class="sxs-lookup"><span data-stu-id="a5032-169">Building connected apps with UWP and Project Rome</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2018/may/universal-windows-platform-building-connected-apps-with-uwp-and-project-rome)

* [<span data-ttu-id="a5032-170">Project Rome: デバイス、アプリ、プラットフォームの垣根を越えたユーザー エンゲージメントの促進 (英語)</span><span class="sxs-lookup"><span data-stu-id="a5032-170">Project Rome: Driving User Engagement Across Devices, Apps, and Platforms</span></span>](https://blogs.windows.com/windowsdeveloper/2017/05/16/project-rome-driving-user-engagement-across-devices-apps-platforms/#hZYfcfYVCFfBv0pS.97)

* [<span data-ttu-id="a5032-171">Microsoft Graph 通知を使用した、ヒューマン セントリックな通知エクスペリエンスの有効化</span><span class="sxs-lookup"><span data-stu-id="a5032-171">Enabling human-centric notification experiences using Microsoft Graph notifications</span></span>](https://docs.microsoft.com/graph/notifications-concept-overview)

## <a name="podcasts-and-recordings"></a><span data-ttu-id="a5032-172">ポッドキャストと録音/録画</span><span class="sxs-lookup"><span data-stu-id="a5032-172">Podcasts and recordings</span></span>

* [<span data-ttu-id="a5032-173">Project Rome を Microsoft //Build 2018 で体験</span><span class="sxs-lookup"><span data-stu-id="a5032-173">Project Rome at Microsoft //Build 2018</span></span>](https://channel9.msdn.com/Events/Build/2018/BRK2417)

* [<span data-ttu-id="a5032-174">Build 2017: Channel 9 ライブ: Project Rome の Q&A (英語)</span><span class="sxs-lookup"><span data-stu-id="a5032-174">Build 2017: Channel 9 live: Project Rome Q&A</span></span>](https://channel9.msdn.com/Events/Build/2017/C9R11)

* [<span data-ttu-id="a5032-175">Build 2017: MS Dev Show: Project Rome (英語)</span><span class="sxs-lookup"><span data-stu-id="a5032-175">Build 2017: MS Dev Show: Project Rome</span></span>](https://channel9.msdn.com/Shows/msdevshow/Episode-153-Project-Rome-with-Vikas-Bhatia-and-Shawn-Henry)

* [<span data-ttu-id="a5032-176">MS Dev Show ポッドキャスト: Shawn Henry が語る Project Rome (2016 年 11 月 8 日) (英語)</span><span class="sxs-lookup"><span data-stu-id="a5032-176">MS Dev Show podcast: Project Rome with Shawn Henry (Nov 8, 2016)</span></span>](https://msdevshow.com/2016/11/project-rome-with-shawn-henry/)

* [<span data-ttu-id="a5032-177">Web とアプリのリンク</span><span class="sxs-lookup"><span data-stu-id="a5032-177">Web-to-app linking</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/web-to-app-linking)

* [<span data-ttu-id="a5032-178">Build 2016: 接続されたアプリとデバイスによるユーザー エンゲージメントの促進 (英語)</span><span class="sxs-lookup"><span data-stu-id="a5032-178">Build 2016: Driving User Engagement with Connected Apps and Devices</span></span>](https://channel9.msdn.com/Events/Build/2016/B831)

* [<span data-ttu-id="a5032-179">One Dev Minute: Project Rome でクロスデバイス アプリの作成</span><span class="sxs-lookup"><span data-stu-id="a5032-179">One Dev Minute: Create cross-device apps with Project Rome</span></span>](https://www.youtube.com/watch?v=7jn-kooKE8U)

* [<span data-ttu-id="a5032-180">Microsoft Graph と通知の概要</span><span class="sxs-lookup"><span data-stu-id="a5032-180">Getting Started with Microsoft Graph and Notifications</span></span>](https://www.youtube.com/watch?v=cmpPFhrS8ZA)

## <a name="give-feedback"></a><span data-ttu-id="a5032-181">フィードバックを送る</span><span class="sxs-lookup"><span data-stu-id="a5032-181">Give feedback</span></span>

|[<span data-ttu-id="a5032-182">フィードバック Hub</span><span class="sxs-lookup"><span data-stu-id="a5032-182">Feedback Hub</span></span>](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)|[<span data-ttu-id="a5032-183">お問い合わせ</span><span class="sxs-lookup"><span data-stu-id="a5032-183">Contact Us</span></span>](mailto:projectrometeam@microsoft.com)|
|-----|-----|

