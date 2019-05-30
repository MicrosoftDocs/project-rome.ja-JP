---
ms.openlocfilehash: 8fd5cb9176bbde99598a95b51c1f2bba513ae187
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801114"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="30f00-101">Microsoft Graph のユーザー アクティビティの REST Api を使用してください。</span><span class="sxs-lookup"><span data-stu-id="30f00-101">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="30f00-102">Microsoft Graph を使用して REST API 呼び出しを介して、ユーザー アクティビティの機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="30f00-102">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="30f00-103">詳細情報と API のリファレンス ドキュメントを確認できます、[の Microsoft Graph の docs プロジェクト ローマ セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities)します。</span><span class="sxs-lookup"><span data-stu-id="30f00-103">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span></span>

<span data-ttu-id="30f00-104">これにより、作成、発行、更新、および HTTP 要求機能を持つ任意のデバイスからの Windows スタイルのユーザー アクティビティの読み取りをすることができます。</span><span class="sxs-lookup"><span data-stu-id="30f00-104">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="30f00-105">Microsoft Graph は、これらのシナリオをネイティブ プラットフォーム Sdk でよりも実装する方が簡単ですが、すべてのプロジェクト ローマ機能をサポートしたり、ネイティブ オブジェクト モデルを提供しません。</span><span class="sxs-lookup"><span data-stu-id="30f00-105">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>