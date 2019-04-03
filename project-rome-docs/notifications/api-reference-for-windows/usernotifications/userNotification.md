---
title: UserNotification
description: このクラスは、グラフの通知を使用して、アプリ サーバーによって発行されたアプリのクライアントによって受信ユーザー通知を表します。
keywords: microsoft、windows、グラフの通知、使い方 windows
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907964"
---
# <a name="class-usernotification"></a>クラス `UserNotification`

```C#
public sealed class UserNotification : IUserNotification
```

このクラスは、1 人のユーザー通知のインスタンスを表します。 ユーザー通知が作成され、同じログインしているユーザーのすべてのデバイス エンドポイントに分散し、ユーザーを対象としたアプリケーション サーバーによって発行されました。
アプリのクライアントで受信した後、ユーザーに通知を生成して、対応するプラットフォームのローカル通知 Api を使用して visual 通知バナーの表示などのエクスペリエンス可能性があります。

## <a name="properties"></a>プロパティ

|名前 | 説明 |
|:-- |:-- |
|ID |開発者が指定したを一意に取得このユーザー通知の id。|
|   GroupId |開発者が指定したを取得します。 このユーザーの通知グループ id。| 
|   ExpirationTime |このユーザー通知の有効期限を取得します。| 
|   Priority|開発者が指定したを取得します。 このユーザー通知の優先順位。| 
|   コンテンツ|この通知は開発者が定義されている任意のデータをコンテンツ ペイロードを取得します。| 
|   ReadState|このユーザーを示す通知が、通知は、読み取り、または未読の読み取りの状態の値を取得します。| 
|   UserActionState|かどうか、通知がない操作、消去された、アクティブ化、または再を判断するユーザー通知のユーザー アクションの状態の値を取得します。| 


## <a name="methods"></a>メソッド

### <a name="saveasync"></a>SaveAsync() 
これは、ユーザー通知の変更を発行するときに呼び出す必要があります。 アプリが、UserNotification の更新可能なプロパティを変更するたびに、このメソッドを呼び出す必要があります。
```C#
public IAsyncOperation SaveAsync()
```

