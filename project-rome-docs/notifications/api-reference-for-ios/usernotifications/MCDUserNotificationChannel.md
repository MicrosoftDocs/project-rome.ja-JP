---
title: MCDUserNotificationChannel
description: MCDUserNotificationChannel クラスについて説明します。 このクラスは、ユーザー通知のライフサイクルを管理します。
keywords: microsoft、windows、device relay、how to iOS、how to iPhone
ms.openlocfilehash: dc7e451494014cdcdebd056b00e57cfdf5f0757f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760876"
---
# <a name="class-mcdusernotificationchannel"></a>講義 `MCDUserNotificationChannel`

```
@interface MCDUserNotificationChannel : NSObject
```

このクラスは、アプリケーションのユーザー通知の受信と管理を処理する通知変更リーダーを提供します。 

## <a name="properties"></a>Properties

### <a name="syncscope"></a>syncScope
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

UserNotifications がフィードに含まれることを保証するために使用される SyncScope。

## <a name="constructors"></a>コンストラクター

### <a name="channelwithuserdatafeed"></a>channelWithUserDataFeed
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a>パラメーター

### <a name="userdatafeed"></a>userDataFeed
このクラスを初期化するために使用される MCDUserDataFeed。

### <a name="initwithuserdatafeed"></a>initWithUserDataFeed
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a>userDataFeed
このクラスを初期化するために使用される MCDUserDataFeed。

## <a name="methods"></a>メソッド

### <a name="createreader"></a>createReader
`- (MCDUserNotificationReader* _Nullable)createReader`

アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。

### <a name="createreaderwithoptions"></a>createReaderWithOptions
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

オプションを使用してユーザー通知リーダーを作成します。

### <a name="createreaderwithstate"></a>createReaderWithState
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。 リーダーは、指定された追跡状態から開始されます。  

### <a name="getusernotificationasync"></a>getUserNotificationAsync
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

Id に基づいてユーザーの通知を受け取ります。

### <a name="deleteusernotificationasync"></a>deleteUserNotificationAsync
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

Id に基づいてユーザー通知を削除します。 