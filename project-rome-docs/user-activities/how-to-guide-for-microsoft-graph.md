---
title: Microsoft Graph のユーザー アクティビティ REST API の使用
description: Microsoft Graph のユーザーアクティビティ REST API を使用して、Windows スタイルのユーザー アクティビティの作成、公開、更新、読み取りができます。
ms.openlocfilehash: 7ec7a2f285ed0b1875bf8d945534b8b89de566f3
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760076"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="283d7-103">Microsoft Graph のユーザー アクティビティ REST API の使用</span><span class="sxs-lookup"><span data-stu-id="283d7-103">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="283d7-104">Microsoft Graph での REST API 呼び出しによってユーザー アクティビティ機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="283d7-104">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="283d7-105">詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="283d7-105">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span></span>

<span data-ttu-id="283d7-106">これにより、HTTP 要求を実行できる任意のデバイスから、Windows スタイルのユーザー アクティビティの作成、発行、更新、読み取りができます。</span><span class="sxs-lookup"><span data-stu-id="283d7-106">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="283d7-107">Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。</span><span class="sxs-lookup"><span data-stu-id="283d7-107">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>