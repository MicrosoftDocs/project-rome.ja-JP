---
title: MCDConnectedDevicesNotificationRegistrationState
description: クラウドの登録の状態を通信するために使用される値。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909234"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a>クラス `MCDConnectedDevicesNotificationRegistrationState` 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
クラウドの登録の状態を通信するために使用される値。

## <a name="fields"></a>フィールド

| 名前                              |   値     | 説明 |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStateUnregistered | 0 | 登録が開始されていることはありません。
| MCDConnectedDevicesNotificationRegistrationStateRegistered | 1 | 登録が完了しました。 |
| MCDConnectedDevicesNotificationRegistrationStateExpiring | 2 | 登録の有効期限が近づいてし、そのため、アプリが必要があります登録をもう一度実行します。 |
| MCDConnectedDevicesNotificationRegistrationStateExpired | 3 | 登録の有効期限が切れており、そのため、アプリが必要がありますの登録をもう一度実行します。 |