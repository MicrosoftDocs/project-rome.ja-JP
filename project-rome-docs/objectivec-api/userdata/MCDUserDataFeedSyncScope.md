---
title: MCDUserDataFeedSyncScope
description: このクラスは、アプリがユーザー固有接続されたデバイスの特定の機能を使用する場合に接続されているデバイス プラットフォームのバックエンドと同期されるユーザー データを表します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 941381a61c9b17c837c25b089f7c7073d581c4a8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907174"
---
# <a name="class-mcduserdatafeedsyncscope"></a>クラス `MCDUserDataFeedSyncScope`

```
@interface MCDUserDataFeedSyncScope : NSObject
```
 このインターフェイスは、アプリがユーザーのアクティビティなど、特定のユーザー固有接続しているデバイス機能を使用する場合に接続されているデバイス プラットフォームのバックエンドと同期されるユーザー データを表します。 インスタンスは、このような機能を管理するクラスから静的に取得されます (例: **MCDUserActivityChannel**)、ありの作成に使用されます**MCDUserDataFeed**します。

## <a name="properties"></a>プロパティ

### <a name="platform"></a>プラットフォーム
`@property (nonatomic, readwrite, nullable, copy) NSString* platform;`

**ConnectedDevicesPlatform**がこのアプリの接続されたデバイスの機能用に初期化されたインスタンス。

### <a name="syncscopeflags"></a>syncScopeFlags
`@property (nonatomic, readwrite, nullable, copy) NSArray<NSString*>* syncScopeFlags;`

受信アクティビティをフィルター処理するためのオプションのフラグを設定します。

### <a name="notificationtype"></a>notificationType
`@property (nonatomic, readwrite, nullable, copy) NSString* notificationType;`

ユーザー同期スコープのデータ フィードを受信する通知の種類の変更の種類を設定します。

```