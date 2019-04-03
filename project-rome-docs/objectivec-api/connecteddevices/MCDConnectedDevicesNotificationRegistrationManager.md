---
title: MCDConnectedDevicesNotificationRegistrationManager
description: すべてのアカウント ローマ クラウド通知の登録を管理します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: d4f5f7963514795e3e296d9bdb42b1811af4f7cc
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909904"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationmanager"></a>クラス `MCDConnectedDevicesNotificationRegistrationManager` 

```
@interface MCDConnectedDevicesNotificationRegistrationManager : NSObject
```  
すべてのアカウントには、接続しているデバイス プラットフォーム クラウド通知の登録を管理します。

MCDConnectedDevicesNotificationRegistrationManager では、各アカウント用に登録通知情報を管理します。 いつでも、アプリの通知情報を変更 (たとえば、APNS では、そのトークンが変更されます) 場合、または、通知情報が期限切れにならない場合に、アプリの情報を再登録する必要があります。 アプリケーションがのみの通信を送信する応答を関心がある場合は、ポーリング登録を使用できます。

> [!NOTE] 
> ConnectedDevices シナリオの多くは正常に機能する前に、通知情報を登録する必要があります。 

## <a name="properties"></a>プロパティ

### <a name="registrationstatechanged"></a>registrationStateChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesNotificationRegistrationManager*, MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs*>* registrationStateChanged;`

イベントは、アプリがアカウントの通知の登録状態が変更されたとき。 

## <a name="methods"></a>メソッド

### <a name="registerforaccountasync"></a>registerForAccountAsync
`- (void) registerForAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration callback:(nonnull void (^)(BOOL, NSError* _Nullable))callback __attribute__((deprecated("Use registerAsync instead")));`

特定の通知の登録情報を指定されたアカウントを登録します。 これにより、このアプリケーションはこのアカウントの新しい情報を接続しているデバイスについて通知できるように、通知チャネルを作成します。 他のアプリケーションが MCDRemoteSystemAppRegistration 情報が公開されるまで、この通知チャネルを使用してこのアプリと通信できるしないことに注意してください。

> [!WARNING]
> この関数が非推奨とされます。 RegisterAsync を使用してください。

#### <a name="parameters"></a>パラメーター 
* `account` 

通知情報を登録するアカウント。

* `notificationRegistration` 

通知情報を登録します。

* `callback` 

コールバックでは、正常に完了した登録場合に発生します。

### <a name="registerasync"></a>registerAsync
`- (void) registerAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration completion:(nonnull void (^)(MCDConnectedDevicesNotificationRegistrationResult* _Nonnull, NSError* _Nullable))callback;`

特定の通知の登録情報を指定されたアカウントを登録します。 これにより、このアプリケーションはこのアカウントの新しい情報を接続しているデバイスについて通知できるように、通知チャネルを作成します。 他のアプリケーションが MCDRemoteSystemAppRegistration 情報が公開されるまで、この通知チャネルを使用してこのアプリと通信できるしないことに注意してください。

#### <a name="parameters"></a>パラメーター 
* `account` 

通知情報を登録するアカウント。

* `notificationRegistration` 

通知情報を登録します。

* `callback` 

コールバックでは、正常に完了した登録場合に発生します。

### <a name="getnotificationregistrationstateforaccount"></a>getNotificationRegistrationStateForAccount
`- (MCDConnectedDevicesNotificationRegistrationState) getNotificationRegistrationStateForAccount:(MCDConnectedDevicesAccount* _Nonnull)account;`

指定されたアカウントの現在の通知の登録状態を取得します。 登録されている通知については、最終的に期限切れになります (アプリがアンインストールされるか、非常に長い時間で実行されない場合に便利です)。 登録が期限切れ/期限切れになったときに、アプリは、通知情報を再登録する必要があります。 

#### <a name="parameters"></a>パラメーター 
* `account`

登録の状態を取得する対象のアカウント。

#### <a name="returns"></a>戻り値

通知登録の状態。
