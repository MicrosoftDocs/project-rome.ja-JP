---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: MCDConnectedDevicesNotificationRegistrationStatus クラスについて説明します。 これらの値は、クラウド登録の状態を伝えるために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: a7dd06a4593203f60275a540702ccfc164aa6b59
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761106"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a>講義 `MCDConnectedDevicesNotificationRegistrationStatus` 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
登録操作の状態を示す列挙です。
エラー状態は、アプリ開発者が登録を再試行する可能性がある一時的な状態を示します。

## <a name="fields"></a>フィールド

| 名前                              |   [値]     | 説明 |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStatusSuccess | 0 | 操作は正常に完了しました。
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork | 1 | ネットワークが使用できませんでした。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure | 2 | Web サービスが失敗しました。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber | 3 | トークン要求サブスクライバーが応答しませんでした。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed | 4 | トークン要求が失敗しました。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound | 5 | 情報を登録するためのアカウントが見つかりませんでした。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown | 6 | 操作で不明なエラーが発生しました。 |