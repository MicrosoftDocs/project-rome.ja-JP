---
title: MCDConnectedDevicesNotificationType
description: 通知の種類 (サービス) を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: eb537450a9e8a970bd07652fe201e94071211d92
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909484"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a>列挙型 `MCDConnectedDevicesNotificationType`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
通知の種類 (サービス) を記述する値が含まれています。

## <a name="fields"></a>フィールド

| 名前                              |   値     | 説明 |
|:----------------------------------|:------|:-------------------------------|
| MCDNotificationTypeUnknown | 0 | ConnectedDevicesNotificationType が不明です。 |
| MCDNotificationTypeWNS | 1 | Windows プッシュ通知サービス。 |
| MCDNotificationTypeGCM | 2 | Google のクラウド メッセージングします。 |
| MCDNotificationTypeFCM | 3 | Firebase クラウド メッセージングのします。|
| MCDNotificationTypeAPN | 4 | Apple Push Notification Service。 |
| MCDNotificationTypePolling | 5 | クラウド通知サービス。受信応答の代わりにポーリングします。 |
