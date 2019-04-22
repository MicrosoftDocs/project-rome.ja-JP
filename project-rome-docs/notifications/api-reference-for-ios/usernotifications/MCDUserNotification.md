---
title: MCDUserNotification
description: このクラスは、グラフの通知を使用して、アプリ サーバーによって発行されたアプリのクライアントによって受信ユーザー通知を表します。
keywords: microsoft、ios、グラフの通知、ios に関する「方法」に関する「方法」の iphone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907894"
---
# <a name="class-mcdusernotification"></a>クラス `MCDUserNotification`

```
@interface MCDUserNotification : NSObject
```


このクラスは、1 人のユーザー通知のインスタンスを表します。 ユーザー通知が作成され、同じログインしているユーザーのすべてのデバイス エンドポイントに分散し、ユーザーを対象としたアプリケーション サーバーによって発行されました。
アプリのクライアントで受信した後、ユーザーに通知を生成して、対応するプラットフォームのローカル通知 Api を使用して visual 通知バナーの表示などのエクスペリエンス可能性があります。

## <a name="properties"></a>プロパティ

### <a name="notificationid"></a>notificationId
`@property(nonatomic, readonly, nonnull) NSString* notificationId;` 開発者が指定したを一意に取得このユーザー通知の id。

### <a name="groupid"></a>GroupId
`@property(nonatomic, readonly, nonnull) NSString* groupId;` 開発者が指定したを取得します。 このユーザーの通知グループ id。

### <a name="expirationtime"></a>expirationTime
`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` このユーザー通知の有効期限を取得します。

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDUserNotificationStatus status;` ユーザー通知の状態を取得します。

### <a name="changetime"></a>changeTime
`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` 変更が行われた時刻を取得します。

### <a name="priority"></a>priority
`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` 開発者が指定したを取得します。 このユーザー通知の優先順位。

### <a name="content"></a>content
`@property(nonatomic, readonly, nonnull) NSString* content;` この通知は開発者が定義されている任意のデータをコンテンツ ペイロードを取得します。

###  <a name="readstate"></a>ReadState
`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` このユーザーを示す通知が、通知は、読み取り、または未読の読み取りの状態の値を取得します。

### <a name="useractionstate"></a>userActionState
`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` かどうか、通知がない操作、消去された、アクティブ化、または再を判断するユーザー通知のユーザー アクションの状態の値を取得します。 

## <a name="methods"></a>メソッド

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

これは、ユーザー通知の変更を発行するときに呼び出す必要があります。 アプリが、UserNotification の更新可能なプロパティを変更するたびに、このメソッドを呼び出す必要があります。

#### <a name="parameters"></a>パラメーター
* `completion` 完了時に実行するコード ブロックです。
