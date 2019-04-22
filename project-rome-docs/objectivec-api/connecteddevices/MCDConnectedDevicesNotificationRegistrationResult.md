---
title: MCDConnectedDevicesNotificationRegistrationResult
description: アカウントの通知情報を登録するための非同期の結果を通信します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 9ee253ff1c07f498b42ccf0cd0edeb9937f31f59
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801354"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationresult"></a>クラス `MCDConnectedDevicesNotificationRegistrationResult` 

```
@interface MCDConnectedDevicesNotificationRegistrationResult : NSObject
```  
MCDConnectedDevicesNotificationRegistrationResult では、アカウントの通知情報を登録するための非同期の結果を通信します。 利用できないネットワークなどの特定の一時的な問題が発生した場合、登録を再試行するアプリによってを通じて、この結果、エラー状態を使用する必要があります。

## <a name="properties"></a>プロパティ

### <a name="status"></a>status

`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationStatus status;`

登録操作のステータスの列挙型。