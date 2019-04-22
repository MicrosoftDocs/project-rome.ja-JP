---
title: MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs
description: MCDConnectedDevicesNotificationRegistration 状態変更イベントのイベント引数クラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 83b59cc884cc0e8d59387b95388b4b7b2b5fa273
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800694"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatechangedeventargs"></a>クラス `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs` 

```
@interface MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs : NSObject
```  
MCDConnectedDevicesNotificationRegistration 状態変更イベントのイベント引数クラスです。 これは、適切な通知メカニズムを使用して新しい接続しているデバイス プラットフォームのメッセージについて、アプリケーションが通知を取得することを確認に使用されます。

## <a name="properties"></a>プロパティ

### <a name="account"></a>アカウント
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

変更が通知の登録状態のアカウント。

### <a name="registration"></a>登録
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistration* registration;`

状態が変化した登録インスタンスの情報。

### <a name="state"></a>state
`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationState state;`

新しい登録状態。