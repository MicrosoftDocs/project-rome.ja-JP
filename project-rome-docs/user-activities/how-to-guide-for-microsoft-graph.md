---
title: Microsoft Graph のユーザー アクティビティ REST API の使用
description: Microsoft Graph のユーザーアクティビティ REST API を使用して、Windows スタイルのユーザー アクティビティの作成、公開、更新、読み取りができます。
ms.openlocfilehash: 3bd2a5258c11936ceb3adbcbd102e7f546cac1ab
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901660"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="97ef2-103">Microsoft Graph のユーザー アクティビティ REST API の使用</span><span class="sxs-lookup"><span data-stu-id="97ef2-103">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="97ef2-104">Microsoft Graph での REST API 呼び出しによってユーザー アクティビティ機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="97ef2-104">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="97ef2-105">詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](/graph/api/resources/project-rome-overview#activities)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97ef2-105">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](/graph/api/resources/project-rome-overview#activities).</span></span>

<span data-ttu-id="97ef2-106">これにより、HTTP 要求を実行できる任意のデバイスから、Windows スタイルのユーザー アクティビティの作成、発行、更新、読み取りができます。</span><span class="sxs-lookup"><span data-stu-id="97ef2-106">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="97ef2-107">Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。</span><span class="sxs-lookup"><span data-stu-id="97ef2-107">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>