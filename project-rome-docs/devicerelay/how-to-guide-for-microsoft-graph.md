---
ms.openlocfilehash: 1d32d509e7c76507626cf0271a28f876f4749ab1
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800284"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="d69fd-101">Microsoft Graph のデバイスの Relay REST Api を使用しました。</span><span class="sxs-lookup"><span data-stu-id="d69fd-101">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="d69fd-102">デバイスのリレー機能は、Microsoft Graph を使用して REST API 呼び出しを介して実装できます。</span><span class="sxs-lookup"><span data-stu-id="d69fd-102">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="d69fd-103">詳細情報と API のリファレンス ドキュメントを確認できます、[の Microsoft Graph の docs プロジェクト ローマ セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices)します。</span><span class="sxs-lookup"><span data-stu-id="d69fd-103">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span></span>

<span data-ttu-id="d69fd-104">Microsoft Graph を使用して実装すると、アプリを起動し、HTTP 要求機能を持つ任意のデバイスからアプリ サービスとの対話、デバイスを検出することができます。</span><span class="sxs-lookup"><span data-stu-id="d69fd-104">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="d69fd-105">Microsoft Graph は、これらのシナリオをネイティブ プラットフォーム Sdk でよりも実装する方が簡単ですが、すべての機能のプロジェクト ローマ機能をサポートしたり、ネイティブ オブジェクト モデルを提供しません。</span><span class="sxs-lookup"><span data-stu-id="d69fd-105">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>