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
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a>Microsoft Graph のユーザー アクティビティ REST API の使用

Microsoft Graph での REST API 呼び出しによってユーザー アクティビティ機能を実装できます。 詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](/graph/api/resources/project-rome-overview#activities)を参照してください。

これにより、HTTP 要求を実行できる任意のデバイスから、Windows スタイルのユーザー アクティビティの作成、発行、更新、読み取りができます。 Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。