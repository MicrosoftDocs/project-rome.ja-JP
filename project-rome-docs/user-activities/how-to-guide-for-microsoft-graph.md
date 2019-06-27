---
ms.openlocfilehash: 8fd5cb9176bbde99598a95b51c1f2bba513ae187
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801114"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="b9017-101">Microsoft Graph のユーザー アクティビティ REST API の使用</span><span class="sxs-lookup"><span data-stu-id="b9017-101">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="b9017-102">Microsoft Graph での REST API 呼び出しによってユーザー アクティビティ機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="b9017-102">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="b9017-103">詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9017-103">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span></span>

<span data-ttu-id="b9017-104">これにより、HTTP 要求を実行できる任意のデバイスから、Windows スタイルのユーザー アクティビティの作成、発行、更新、読み取りができます。</span><span class="sxs-lookup"><span data-stu-id="b9017-104">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="b9017-105">Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。</span><span class="sxs-lookup"><span data-stu-id="b9017-105">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>