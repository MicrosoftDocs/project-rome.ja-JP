---
title: Microsoft Graph のデバイス リレー REST API を使用する
description: Microsoft Graph のデバイス リレー REST API を使用して、デバイスの検出、アプリの起動、アプリ サービスとの対話を行う方法について説明します。
ms.openlocfilehash: e72bf1c4bc52bddfe84fd09a7588c664aca2d709
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901440"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a>Microsoft Graph のデバイス リレー REST API を使用する

Microsoft Graph での REST API 呼び出しによってデバイス リレー機能を実装できます。 詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](/graph/api/resources/project-rome-overview#devices)を参照してください。

Microsoft Graph と共に実装することで、HTTP 要求を実行できる任意のデバイスから、デバイスの検出、アプリの起動、アプリ サービスとの対話ができるようになります。 Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。