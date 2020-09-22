---
title: Microsoft Graph のデバイス リレー REST API を使用する
description: Microsoft Graph のデバイス リレー REST API を使用して、デバイスの検出、アプリの起動、アプリ サービスとの対話を行う方法について説明します。
ms.openlocfilehash: a2433e5a16f36edb9e8283d885f9ebf3d05b64d1
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760806"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a>Microsoft Graph のデバイス リレー REST API を使用する

Microsoft Graph での REST API 呼び出しによってデバイス リレー機能を実装できます。 詳細および API リファレンス ドキュメントについては、[Microsoft Graph ドキュメントの Project Rome セクション](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices)を参照してください。

Microsoft Graph と共に実装することで、HTTP 要求を実行できる任意のデバイスから、デバイスの検出、アプリの起動、アプリ サービスとの対話ができるようになります。 Microsoft Graph によってこれらのシナリオの実装がネイティブ プラットフォーム SDK よりも簡単になりますが、Project Rome のすべての機能がサポートされるわけではなく、ネイティブ オブジェクト モデルも提供されません。