---
title: MCDConnectedDevicesNotificationType
description: MCDConnectedDevicesNotificationType 列挙型について説明します。 この列挙には、通知の種類 (サービス) を説明する値が含まれます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 5daf6db553df72a14a2cf201b4e974083eb7cf80
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761096"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a>enum `MCDConnectedDevicesNotificationType`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
通知の種類 (サービス) を説明する値を格納します。

## <a name="fields"></a>フィールド

| 名前                              |   [値]     | 説明 |
|:----------------------------------|:------|:-------------------------------|
| MCDNotificationTypeUnknown | 0 | ConnectedDevicesNotificationType は不明です。 |
| MCDNotificationTypeWNS | 1 | Windows プッシュ Notification Services。 |
| MCDNotificationTypeGCM | 2 | Google Cloud Messaging。 |
| MCDNotificationTypeFCM | 3 | 焼討 base Cloud Messaging。|
| MCDNotificationTypeAPN | 4 | Apple Push Notification Service。 |
| MCDNotificationTypePolling | 5 | クラウド通知サービスがありません。代わりに、受信した応答をポーリングします。 |
