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
# <a name="project-rome"></a>Project Rome

[Project Rome](https://developer.microsoft.com/windows/project-rome) は、Microsoft が提供するアプリのクロスデバイス エクスペリエンス プラットフォームです。 

このサイトには、Project Rome の開発者向けドキュメント、およびその他の有用なリソースへのリンクが含まれています。

Project Rome に関するニュース、ブログ記事、ビデオについては、[Project Rome のランディング ページ](https://developer.microsoft.com/windows/project-rome)をご覧ください。

Project Rome を使用するサンプル アプリケーションについては、下記の SDK の表を確認するか、[Project Rome のサンプル リポジトリ](https://github.com/Microsoft/project-rome)にアクセスしてください。

## <a name="about-project-rome"></a>Project Rome について

Project Rome を使用する開発者は、複数のデバイスで実行可能で、かつデバイスを切り替える際にユーザーと一緒に切り替え先のデバイスに移動できるアプリを作成できます。

Project Rome には、Microsoft Graph およびプラットフォーム固有のネイティブ SDK を介して公開される機能が含まれています。 これらの機能により、複数のクロスデバイス機能とコネクテッド デバイス機能が有効になり、ログインしたユーザー ID を軸としてアプリを一元管理できます。 Project Rome に関連付けられた機能には、ユーザーのアクティビティ、通知、デバイス リレー、近距離共有などがありますが、これらに限定されるものではありません。

## <a name="choosing-between-native-apis-and-graph-apis"></a>ネイティブ API と Graph API の使い分け

シナリオによっては、ネイティブ プラットフォームの SDK と Microsoft Graph を介した REST API の*両方*から利用可能です。 一般に、REST API を使用すると Project Rome の機能を素早く簡単に実装できます。 ただし、プラットフォーム固有の実装を使用することで、次のような利点が得られます。

* プラットフォーム SDK は、サーバー側の情報が変更されたときにアプリを更新するために、ネイティブ言語のオブジェクト モデル、ローカル記憶域、および発行-サブスクライブ パターンを提供します。
* アプリが Windows (UWP または Win32 アプリ) で実行されている場合、ユーザーの既定のアカウントを使用する機能や、ユーザーのエンゲージメントを自動的に追跡する機能など、プラットフォーム SDK の多数の追加機能を使用できます。
* プラットフォーム SDK を介してしか使用できない他の Project Rome 機能を使用する予定の場合は、それぞれの機能を同じ方法で実装することをお勧めします。

シナリオによっては、Microsoft Graph API とクライアント SDK を組み合わせて使用することで有効になるものもあります。 通知がその例になります。 この場合、MS Graph API を使用してアプリ サーバー側からの通知を公開し、ネイティブ プラットフォームのクライアント SDK を使用して各クライアント側のネイティブ アプリで通知を受信および管理します。

## <a name="sdk"></a>SDK

Project Rome は現在、以下のプラットフォームに対して実装されています。 サンプルと SDK のダウンロードについては、各リンク先をご覧ください。

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



|   プラットフォーム                        | 機能                                                         |           SDK パッケージ                          |   サンプル                                       |
| :-------------------------------- | :--------------------------------------------------------------- |:---------------------------------------------- | :---------------------------------------------- |
| **Windows SDK**                   | デバイス リレー、アクティビティ/タイムライン                                | [![SDK][windows-sdk-badge]][windows-sdk]       | [Windows デバイス リレー用 Project Rome サンプル][windows-drsample] <br> [Windows アクティビティ用 Project Rome サンプル][windows-afsample]
| **Windows (プレビュー)**             |                                    Microsoft Graph 通知 | [![Nuget][winredist-sdk-badge]][winredist-sdk] | [Windows 用 Graph 通知サンプル][winredist-sample] 
| **Android**             | デバイス リレー、アクティビティ/タイムライン、Microsoft Graph 通知 (プレビュー) | [![Maven][android-sdk-badge]][android-sdk]     | [Android 用 Project Rome サンプル][android-sample]
| **iOS**                 | デバイス リレー、アクティビティ/タイムライン、Microsoft Graph 通知 (プレビュー) | [![CocoaPod][ios-sdk-badge]][ios-sdk]          | [iOS 用 Project Rome サンプル][ios-sample]
| **Android 用 Xamarin (プレビュー)** | デバイス リレー                                                     | [![Nuget][xamarin-sdk-badge]][xamarin-sdk]     | [Android 用 Xamarin サンプル][xamarin-sample]
| **MSGraph**                       | デバイス リレー、アクティビティ/タイムライン、Microsoft Graph 通知 | [![REST][graph-relay-badge]][graph-relay]<br> [![REST][graph-activities-badge]][graph-activities]<br>[![REST][graph-notification-badge]][graph-notification]          | [デバイス リレー][graph-relay-sample]<br>[アクティビティ/タイムライン][graph-activities-sample]<br>[Graph 通知][graph-notification-sample]

## <a name="project-rome-blog-posts"></a>Project Rome のブログ記事
* [Android および iOS 向けの Project Rome SDK バージョン 1.0 を発表します。](https://blogs.windows.com/windowsdeveloper/2019/01/29/announcing-project-rome-sdk-for-android-and-ios-version-1-0/)

* [Project Rome によるクロスデバイスのエクスペリエンス](https://blogs.windows.com/buildingapps/2016/10/11/cross-device-experience-with-project-rome/#iQTseFlAMJRopU9k.97)

* [ソーシャル化:Project Rome、マップ、およびソーシャル ネットワークの統合 (英語)](https://blogs.windows.com/buildingapps/2016/10/27/going-social-project-rome-maps-social-network-integration-app-dev-on-xbox-series/#SCfoEZ1q8c1yBMei.97)

* [Project Rome Android SDK の発表](https://blogs.windows.com/buildingapps/2017/02/08/announcing-project-rome-android-sdk/#obDkvwkXOGa3tcTx.97)

* [Android 用 Project Rome の更新:アプリ サービスのサポートが開始 (英語)](https://blogs.windows.com/buildingapps/2017/03/23/project-rome-android-update-now-app-services-support/#DBm1Ic4JX8vXv2h0.97)

* [Project Rome による Android 用リモート制御コンパニオン アプリの構築](https://devblogs.microsoft.com/xamarin/building-remote-control-companion-app-android-project-rome/)

* [Windows 10 Creators Update の新しい共有エクスペリエンス (英語)](https://blogs.windows.com/buildingapps/2017/04/06/new-share-experience-windows-10-creators-update/#OGskrWcLLlrCTCSH.97)

* [AppUriHandlers を使用した Web とアプリのリンク](https://blogs.windows.com/buildingapps/2016/10/14/web-to-app-linking-with-appurihandlers/#fIh7USaxBYS8JqfT.97)

* [Project Rome:デバイス、アプリ、プラットフォームの垣根を越えたユーザー エンゲージメントの促進](https://blogs.windows.com/windowsdeveloper/2017/05/16/project-rome-driving-user-engagement-across-devices-apps-platforms/#jsUX3bEM6c8SpkIF.97)

* [UWP と Project Rome を使って接続アプリを構築する](https://docs.microsoft.com/archive/msdn-magazine/2018/may/universal-windows-platform-building-connected-apps-with-uwp-and-project-rome)

* [Project Rome: デバイス、アプリ、プラットフォームの垣根を越えたユーザー エンゲージメントの促進 (英語)](https://blogs.windows.com/windowsdeveloper/2017/05/16/project-rome-driving-user-engagement-across-devices-apps-platforms/#hZYfcfYVCFfBv0pS.97)

* [Microsoft Graph 通知を使用した、ヒューマン セントリックな通知エクスペリエンスの有効化](https://docs.microsoft.com/graph/notifications-concept-overview)

## <a name="podcasts-and-recordings"></a>ポッドキャストと録音/録画

* [Project Rome を Microsoft //Build 2018 で体験](https://channel9.msdn.com/Events/Build/2018/BRK2417)

* [Build 2017: Channel 9 ライブ: Project Rome の Q&A (英語)](https://channel9.msdn.com/Events/Build/2017/C9R11)

* [Build 2017: MS Dev Show: Project Rome (英語)](https://channel9.msdn.com/Shows/msdevshow/Episode-153-Project-Rome-with-Vikas-Bhatia-and-Shawn-Henry)

* [MS Dev Show ポッドキャスト: Shawn Henry が語る Project Rome (2016 年 11 月 8 日) (英語)](https://msdevshow.com/2016/11/project-rome-with-shawn-henry/)

* [Web とアプリのリンク](https://docs.microsoft.com/windows/uwp/launch-resume/web-to-app-linking)

* [Build 2016: 接続されたアプリとデバイスによるユーザー エンゲージメントの促進 (英語)](https://channel9.msdn.com/Events/Build/2016/B831)

* [One Dev Minute: Project Rome でクロスデバイス アプリの作成](https://www.youtube.com/watch?v=7jn-kooKE8U)

* [Microsoft Graph と通知の概要](https://www.youtube.com/watch?v=cmpPFhrS8ZA)

## <a name="give-feedback"></a>フィードバックを送る

|[フィードバック Hub](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)|[お問い合わせ](mailto:projectrometeam@microsoft.com)|
|-----|-----|

