---
title: Microsoft Graph のデバイス リレー REST API を使用する
ms.openlocfilehash: 887ebff8788ac4300036512761df80c6b8e5e97f
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "75207821"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="39ab5-102">Microsoft Graph のデバイス リレー REST API を使用する</span><span class="sxs-lookup"><span data-stu-id="39ab5-102">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="39ab5-103">Microsoft Graph での REST API 呼び出しによってデバイス リレー機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="39ab5-103">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="39ab5-104">詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39ab5-104">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span></span>

<span data-ttu-id="39ab5-105">Microsoft Graph と共に実装することで、HTTP 要求を実行できる任意のデバイスから、デバイスの検出、アプリの起動、アプリ サービスとの対話ができるようになります。</span><span class="sxs-lookup"><span data-stu-id="39ab5-105">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="39ab5-106">Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。</span><span class="sxs-lookup"><span data-stu-id="39ab5-106">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>