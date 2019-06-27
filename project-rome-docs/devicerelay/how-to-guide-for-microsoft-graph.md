---
ms.openlocfilehash: 1d32d509e7c76507626cf0271a28f876f4749ab1
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59800284"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="a606d-101">Microsoft Graph のデバイス リレー REST API を使用する</span><span class="sxs-lookup"><span data-stu-id="a606d-101">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="a606d-102">Microsoft Graph での REST API 呼び出しによってデバイス リレー機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="a606d-102">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="a606d-103">詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a606d-103">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span></span>

<span data-ttu-id="a606d-104">Microsoft Graph と共に実装することで、HTTP 要求を実行できる任意のデバイスから、デバイスの検出、アプリの起動、アプリ サービスとの対話ができるようになります。</span><span class="sxs-lookup"><span data-stu-id="a606d-104">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="a606d-105">Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。</span><span class="sxs-lookup"><span data-stu-id="a606d-105">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>