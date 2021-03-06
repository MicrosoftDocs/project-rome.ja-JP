---
title: UserNotification
description: このクラスは、アプリケーションサーバーによって Graph 通知を使用して発行され、アプリクライアントによって受信されるユーザー通知を表します。
keywords: microsoft、windows、graph 通知、操作方法ウィンドウ
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801594"
---
# <a name="class-usernotification"></a>講義`UserNotification`

```C#
public sealed class UserNotification : IUserNotification
```

このクラスは、1つのユーザー通知インスタンスを表します。 ユーザー通知は、ユーザーを対象としたアプリサーバーによって作成および発行され、同じログインユーザーのすべてのデバイスエンドポイントに配布されます。
ユーザー通知は、アプリクライアントによって受信されると、対応するプラットフォームのローカル通知 Api を使用して視覚的通知バナーを生成して表示するなどのエクスペリエンスになります。

## <a name="properties"></a>Properties

|名前 | 説明 |
|:-- |:-- |
|Id |このユーザー通知に対して指定された一意の id を取得します。|
|   GroupId |このユーザー通知の開発者が指定したグループ id を取得します。| 
|   ExpirationTime |このユーザー通知の有効期限を取得します。| 
|   [Priority]|このユーザー通知に対して指定された開発者の優先順位を取得します。| 
|   Content|この通知のコンテンツペイロードを取得します。これは、開発者が任意のデータを定義したものです。| 
|   ReadState|通知が開封されたか未読であることを示す、このユーザー通知の読み取り状態の値を取得します。| 
|   UserActionState|通知が対話、破棄、アクティブ化、または再通知されていないかどうかを判断するユーザー通知のユーザー操作状態の値を取得します。| 


## <a name="methods"></a>メソッド

### <a name="saveasync"></a>SaveAsync () 
これは、ユーザー通知の変更を発行するときに呼び出す必要があります。 アプリケーションが UserNotification の更新可能なプロパティを変更するたびに、このメソッドを呼び出す必要があります。
```C#
public IAsyncOperation SaveAsync()
```

