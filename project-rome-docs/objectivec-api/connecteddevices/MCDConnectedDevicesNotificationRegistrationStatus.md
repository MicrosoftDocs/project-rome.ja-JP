---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: クラウドの登録の状態を通信するために使用される値。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: c7d770c73479afb949a4917b5457b12e23b78698
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801364"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a>クラス `MCDConnectedDevicesNotificationRegistrationStatus` 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
登録操作の状態を示す列挙です。
エラー状態では、アプリ開発者の登録を再試行する必要のある一時的な状態を示します。

## <a name="fields"></a>フィールド

| 名前                              |   値     | 説明 |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStatusSuccess | 0 | 操作が正常に完了しました。
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork | 1 | ネットワークは使用できませんでした。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure | 2 | Web サービスが失敗しました。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber | 3 | トークン要求のサブスクライバーが応答しません。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed | 4 | トークンの要求が失敗しました。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound | 5 | 情報を登録するアカウントが見つかりませんでした。 |
| MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown | 6 | 操作には、不明なエラーが発生しました。 |