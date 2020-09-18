---
title: MCDConnectedDevicesNotificationRegistrationState
description: MCDConnectedDevicesNotificationRegistrationState クラスについて説明します。 これらの値は、クラウド登録の状態を伝えるために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 8b69443b53532280df3deeef51025f18e70fecac
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761116"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a>講義 `MCDConnectedDevicesNotificationRegistrationState` 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
クラウド登録の状態を伝えるために使用される値。

## <a name="fields"></a>フィールド

| 名前                              |   [値]     | 説明 |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStateUnregistered | 0 | 登録が開始されていません。
| MCDConnectedDevicesNotificationRegistrationStateRegistered | 1 | 登録が完了しました。 |
| MCDConnectedDevicesNotificationRegistrationStateExpiring | 2 | 登録の有効期限が間もなく切れます。アプリで登録を再度実行する必要があります。 |
| MCDConnectedDevicesNotificationRegistrationStateExpired | 3 | 登録の有効期限が切れているため、アプリで登録を再度実行する必要があります。 |