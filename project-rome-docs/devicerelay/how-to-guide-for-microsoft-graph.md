---
title: Microsoft Graph のデバイス リレー REST API を使用する
description: Microsoft Graph のデバイス リレー REST API を使用して、デバイスの検出、アプリの起動、アプリ サービスとの対話を行う方法について説明します。
ms.openlocfilehash: e72bf1c4bc52bddfe84fd09a7588c664aca2d709
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901440"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="70c63-103">Microsoft Graph のデバイス リレー REST API を使用する</span><span class="sxs-lookup"><span data-stu-id="70c63-103">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="70c63-104">Microsoft Graph での REST API 呼び出しによってデバイス リレー機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="70c63-104">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="70c63-105">詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](/graph/api/resources/project-rome-overview#devices)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70c63-105">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](/graph/api/resources/project-rome-overview#devices).</span></span>

<span data-ttu-id="70c63-106">Microsoft Graph と共に実装することで、HTTP 要求を実行できる任意のデバイスから、デバイスの検出、アプリの起動、アプリ サービスとの対話ができるようになります。</span><span class="sxs-lookup"><span data-stu-id="70c63-106">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="70c63-107">Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。</span><span class="sxs-lookup"><span data-stu-id="70c63-107">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>