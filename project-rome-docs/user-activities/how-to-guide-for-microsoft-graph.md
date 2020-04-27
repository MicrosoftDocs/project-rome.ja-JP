---
title: Microsoft Graph のユーザー アクティビティ REST API の使用
ms.openlocfilehash: efb5b591ca4c1f3024e1fb19dceee783dc75dc8c
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "75207901"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a>Microsoft Graph のユーザー アクティビティ REST API の使用

Microsoft Graph での REST API 呼び出しによってユーザー アクティビティ機能を実装できます。 詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities)を参照してください。

これにより、HTTP 要求を実行できる任意のデバイスから、Windows スタイルのユーザー アクティビティの作成、発行、更新、読み取りができます。 Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。