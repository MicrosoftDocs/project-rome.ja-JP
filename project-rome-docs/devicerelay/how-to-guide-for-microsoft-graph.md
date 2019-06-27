---
ms.openlocfilehash: 1d32d509e7c76507626cf0271a28f876f4749ab1
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "59800284"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a>Microsoft Graph のデバイス リレー REST API を使用する

Microsoft Graph での REST API 呼び出しによってデバイス リレー機能を実装できます。 詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices)を参照してください。

Microsoft Graph と共に実装することで、HTTP 要求を実行できる任意のデバイスから、デバイスの検出、アプリの起動、アプリ サービスとの対話ができるようになります。 Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。