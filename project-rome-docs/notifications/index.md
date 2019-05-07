---
title: Microsoft Graph 通知
description: アプリケーションに Microsoft Graph 通知を含めて、人中心の方法でユーザーと再びやり取りします。
ms.localizationpriority: medium
ms.topic: overview
ms.custom: seodec2018
ms.openlocfilehash: 23aefb0e9f75721977e3ab9f1002bebf264a5b09
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58906764"
---
# <a name="microsoft-graph-notifications"></a>Microsoft Graph 通知
通知は、ユーザーと再びやり取りするのに最も効果的な方法です。 それによってユーザーの注意を引き、ユーザーをアプリに戻すことができます。 マルチデバイス時代のユーザーは、アプリが存在するプラットフォームやデバイスが何であろうと、どこからでもアプリやサービスにアクセスできます。
通知のシナリオは、ユーザーがどこにいても通知を受け取れるようにすることを第一の目的とする、「人中心」の形で設計する必要があります。 主要なプラットフォームで提供されている既存の通知ソリューションは、デバイスを対象とするのに優れています。 Microsoft Graph 通知は、ユーザーを対象にできるようにすることでこれを改善します。 ユーザーとエンドポイント間のマッピング、ユーザーのさまざまなエンドポイント全体での通知状態の同期などといった面倒な作業は、Microsoft Graph 通知に任せることができます。

## <a name="why-integrate-with-microsoft-graph-notifications"></a>Microsoft Graph 通知と統合する理由

### <a name="deliver-notifications-to-a-user-across-different-endpoints"></a>さまざまなエンドポイントでユーザーに通知を配信する
Microsoft Graph に含まれる通知 API を使用すると、Microsoft アカウントや職場または学校の (Azure Active Directory) アカウントを対象に通知を配信できます。 この通知はプラットフォームにより、Windows UWP、Android、iOS を含む、すべてのユーザーのエンドポイントに配信されます。

### <a name="manage-notifications-across-endpoints"></a>エンドポイント全体にわたって通知を管理する
Microsoft Graph の通知 API を使用すると、通知の状態を更新し、更新後の状態をすべてのエンドポイントで同期できます。 たとえば、ユーザーがあるデバイスで通知に対して操作を行った場合、この通知の状態を更新できます (開封済みまたは破棄済みとしてマークするなど)。それによって、同じ状態変更が他のすべてのエンドポイントに伝播されます。 Microsoft Graph の通知 API は、一元管理された方法でユーザーの通知の状態を追跡します。したがって簡単かつ確実に、1 回処理された通知をすべての場所で更新または破棄することができます。

### <a name="retrieve-notification-history"></a>通知履歴を取得する
通知 API を使用して、ユーザー定義の有効期限 (最大 30 日間) に基づく通知履歴を取得できます。 開封済みまたは破棄済みとしてマークされた通知でも、履歴から取得して通知履歴やその他のシナリオをアプリ内で表示できます。

## <a name="integrating-with-microsoft-graph-notifications"></a>Microsoft Graph 通知と統合する

### <a name="onboarding"></a>オンボード
アプリやサービスのモバイル プッシュ通知ソリューションとして Graph 通知を使用する方法に関するステップ バイ ステップ ガイドについては、各プラットフォームノード (Windows、Android、iOS) のハウツー ガイドをご覧ください。 ここでのハウツー ガイドは通知の受信に重点を置いていることに注意してください。 通知の送信については、[MS Graph API を使用した通知の送信](sending-notifications.md)に関するページをご覧ください。

このガイドには、Graph 通知を使用するための具体的な手順 (クロスプラットフォームのアプリ ID とモバイル プッシュの資格情報の登録など) が含まれています。 Microsoft Graph を初めて使用するユーザーのために、Microsoft アカウント (MSA) (一般ユーザー向けアプリケーション用)、または職場や学校のアカウント用の Azure Active Directory (AAD) に対してアプリを登録する手順が含まれています。 MSA と AAD は、Microsoft Graph のワークロードを通知以外にも利用してより豊富なビジネス シナリオを実現できるようにするためのユーザー ID です。 

### <a name="microsoft-graph-apis"></a>Microsoft Graph API
Graph 通知を使用する場合、通知を送信するためにアプリ サーバーが Microsoft Graph API (ベータ版) を使用することが期待されています。 アプリ サーバー側の統合について詳しくは、API の使用法に関する [API リファレンス ドキュメント](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview)を参照してください。 

### <a name="client-side-sdk"></a>クライアント側 SDK
クライアント側の Graph 通知統合を開始し、ネイティブ SDK を使用して通知の受信と管理を開始するには、左側のナビゲーション ウィンドウで任意の開発プラットフォームを選択してください。 

* [MS Graph API を使用して通知を送信する](sending-notifications.md)
* [Project Rome SDK を使用して通知を受信する](receiving-notifications.md)
