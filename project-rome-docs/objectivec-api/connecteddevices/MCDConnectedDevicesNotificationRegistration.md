---
title: MCDConnectedDevicesNotificationRegistration
description: このクラスは、(プロジェクト ローマ シナリオによっては必要に応じて) プッシュ通知サービスでのアプリの登録を表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 38cd140538d6e6dabddda39ba98f736fc708ade7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908884"
---
# <a name="class-mcdconnecteddevicesnotificationregistration"></a>クラス `MCDConnectedDevicesNotificationRegistration` 

```
@interface MCDConnectedDevicesNotificationRegistration : NSObject
```  
 このクラスは、(プロジェクト ローマ シナリオによっては必要に応じて) プッシュ通知サービスでのアプリの登録を表します。 これは、接続されているデバイス プラットフォームには、この情報を伝えます。

## <a name="properties"></a>プロパティ

### <a name="type"></a>type
`@property(nonatomic, readwrite) MCDConnectedDevicesNotificationType type;`

このセットアップでの通知の種類。

### <a name="token"></a>トークン
`@property(nonatomic, readwrite, nonnull) NSString* token;`

登録トークンです。

### <a name="appid"></a>AppId
`@property(nonatomic, readwrite, nonnull) NSString* appId;`

プッシュ通知登録のアプリ ID です。

### <a name="appdisplayname"></a>AppDisplayName
`@property(nonatomic, readwrite, nonnull) NSString* appDisplayName;`

アプリの表示名。 Microsoft デベロッパー ポータルに登録されているアプリの名前があります。