---
title: MCDUserNotificationReader
description: このクラスは、新しいユーザー通知の受信およびユーザーへの通知は提供します。 更新します。 ユーザーが接続されているデバイスのプラットフォームで永続化の通知のコレクションへのアクセスも提供します。
keywords: microsoft、windows、リレーのデバイス、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800734"
---
# <a name="class-mcdusernotificationreader"></a>クラス `MCDUserNotificationReader`

```
@interface MCDUserNotificationReader : NSObject
```

このクラスは、新しいユーザー通知の受信およびユーザーへの通知は提供します。 更新します。 ユーザーが接続されているデバイスのプラットフォームで永続化の通知のコレクションへのアクセスも提供します。  

## <a name="properties"></a>プロパティ

### <a name="serializedstate"></a>serializedState
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

変更のリーダーの現在の状態を返します。 同じ状態から、新しいリーダーを構築するために使用します。
通知の変更 (または、初期状態を [なし] が正常に完了した場合) の最後に完了したバッチに基づいています。

### <a name="datachanged"></a>DataChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

MCDUserNotificationReader のイベント サブスクリプションを変更します。

## <a name="methods"></a>メソッド

### <a name="readbatchasyncwithmaxsize"></a>readBatchAsyncWithMaxSize
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

読み取り通知は、新しい受信の通知などを変更し、バッチ内の既存の通知を更新します。