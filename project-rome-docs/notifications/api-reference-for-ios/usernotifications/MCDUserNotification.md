---
title: MCDUserNotification
description: このクラスは、アプリケーションサーバーによって Graph 通知を使用して発行され、アプリクライアントによって受信されるユーザー通知を表します。
keywords: microsoft、ios、graph 通知、操作方法 ios、操作方法 iphone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907894"
---
# <a name="class-mcdusernotification"></a>講義`MCDUserNotification`

```
@interface MCDUserNotification : NSObject
```


このクラスは、1つのユーザー通知インスタンスを表します。 ユーザー通知は、ユーザーを対象としたアプリサーバーによって作成および発行され、同じログインユーザーのすべてのデバイスエンドポイントに配布されます。
ユーザー通知は、アプリクライアントによって受信されると、対応するプラットフォームのローカル通知 Api を使用して視覚的通知バナーを生成して表示するなどのエクスペリエンスになります。

## <a name="properties"></a>Properties

### <a name="notificationid"></a>notificationId
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`このユーザー通知に対して指定された一意の id を取得します。

### <a name="groupid"></a>groupId
`@property(nonatomic, readonly, nonnull) NSString* groupId;`このユーザー通知の開発者が指定したグループ id を取得します。

### <a name="expirationtime"></a>expirationTime
`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;`このユーザー通知の有効期限を取得します。

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDUserNotificationStatus status;`ユーザー通知の状態を取得します。

### <a name="changetime"></a>changeTime
`@property(nonatomic, readonly, nonnull) NSDate* changeTime;`変更が行われた時刻を取得します。

### <a name="priority"></a>priority
`@property(nonatomic, readonly) MCDUserNotificationPriority priority;`このユーザー通知に対して指定された開発者の優先順位を取得します。

### <a name="content"></a>content
`@property(nonatomic, readonly, nonnull) NSString* content;`この通知のコンテンツペイロードを取得します。これは、開発者が任意のデータを定義したものです。

###  <a name="readstate"></a>readState
`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;`通知が開封されたか未読であることを示す、このユーザー通知の読み取り状態の値を取得します。

### <a name="useractionstate"></a>userActionState
`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;`通知が対話、破棄、アクティブ化、または再通知されていないかどうかを判断するユーザー通知のユーザー操作状態の値を取得します。 

## <a name="methods"></a>メソッド

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

これは、ユーザー通知の変更を発行するときに呼び出す必要があります。 アプリケーションが UserNotification の更新可能なプロパティを変更するたびに、このメソッドを呼び出す必要があります。

#### <a name="parameters"></a>パラメーター
* `completion`完了時に実行するコードブロック。
