---
title: Microsoft Graph のデバイス リレー REST API を使用する
ms.openlocfilehash: 887ebff8788ac4300036512761df80c6b8e5e97f
ms.sourcegitcommit: 5670ff536ea9bfcd678cfde54f262a1ec5c8add4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207821"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a>Microsoft Graph のデバイス リレー REST API を使用する

Microsoft Graph での REST API 呼び出しによってデバイス リレー機能を実装できます。 詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices)を参照してください。

Microsoft Graph と共に実装することで、HTTP 要求を実行できる任意のデバイスから、デバイスの検出、アプリの起動、アプリ サービスとの対話ができるようになります。 Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。