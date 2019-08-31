---
title: MCDUserNotificationReader
description: このクラスは、新しい受信ユーザー通知とユーザー通知の更新を提供します。 また、接続されているデバイスプラットフォームに保持されているユーザー通知のコレクションにアクセスすることもできます。
keywords: microsoft、windows、device relay、how to iOS、how to iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800734"
---
# <a name="class-mcdusernotificationreader"></a>講義`MCDUserNotificationReader`

```
@interface MCDUserNotificationReader : NSObject
```

このクラスは、新しい受信ユーザー通知とユーザー通知の更新を提供します。 また、接続されているデバイスプラットフォームに保持されているユーザー通知のコレクションにアクセスすることもできます。  

## <a name="properties"></a>Properties

### <a name="serializedstate"></a>serializedState
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

変更リーダーの現在の状態を返します。 は、同じ状態から新しいリーダーを構築するために使用できます。
通知の変更が最後に完了したバッチに基づく (または、正常に完了しなかった場合は初期状態)。

### <a name="datachanged"></a>dataChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

MCDUserNotificationReader のイベントサブスクリプションが変更されました。

## <a name="methods"></a>メソッド

### <a name="readbatchasyncwithmaxsize"></a>readBatchAsyncWithMaxSize
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

新しい受信通知や既存の通知をバッチで更新するなど、通知の変更を読み取ります。