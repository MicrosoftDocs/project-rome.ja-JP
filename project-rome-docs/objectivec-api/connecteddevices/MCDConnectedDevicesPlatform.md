---
title: MCDConnectedDevicesPlatform
description: 接続されているデバイス プラットフォームを表し、アプリの接続を管理するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 33fdb6f7dfd7d11831da1f7710215e35306d79d1
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909744"
---
# <a name="class-mcdconnecteddevicesplatform"></a>クラス `MCDConnectedDevicesPlatform` 

```
@interface MCDConnectedDevicesPlatform : NSObject
```  
このクラスが接続されているデバイス プラットフォームを表し、アプリの接続を管理するには。

## <a name="properties"></a>プロパティ

### <a name="accountmanager"></a>accountManager
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccountManager* accountManager;`

プラットフォームによって保持されている MCDConnectedDevicesAccountManager インスタンス。

### <a name="notificationregistrationmanager"></a>notificationRegistrationManager
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistrationManager* notificationRegistrationManager;`

プラットフォームによって保持されている MCDConnectedDevicesNotificationRegistrationManager インスタンス。

## <a name="constructors"></a>コンストラクター

### <a name="platformwithsettings"></a>platformWithSettings
`+ (nullable instancetype)platformWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

指定したプラットフォームの設定では、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `settings` 

プラットフォームのアプリの設定を格納する MCDConnectedDevicesPlatformSettings オブジェクト。

#### <a name="returns"></a>戻り値

アプリのプラットフォームの設定を含む MCDConnectedDevicesPlatform オブジェクトを返します。

### <a name="initwithsettings"></a>initWithSettings
`- (nullable instancetype)initWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

プラットフォームの設定では、このクラスの新しいインスタンス。

#### <a name="parameters"></a>パラメーター 
* `settings` 

プラットフォームのアプリの設定を格納する MCDConnectedDevicesPlatformSettings オブジェクト。

#### <a name="returns"></a>戻り値

アプリのプラットフォームの設定を使用して初期化 MCDConnectedDevicesPlatform オブジェクトを返します。

## <a name="methods"></a>メソッド

### <a name="processnotification"></a>processNotification
`- (MCDConnectedDevicesProcessNotificationOperation* _Nonnull)processNotification:(NSDictionary* _Nonnull)notification;`

受信した APNs 通知を処理します。

#### <a name="parameters"></a>パラメーター 
* `notification` 

APNs 通知処理にはが含まれています。

#### <a name="returns"></a>戻り値

MCDConnectedDevicesProcessNotificationOperation クラスのインスタンス。

### <a name="start"></a>スタート
`- (void) start;`

プラットフォームを起動します。

### <a name="shutdownasync"></a>shutdownAsync
`- (void)shutdownAsync:(void (^_Nonnull)(NSError* _Nullable))completionBlock;`

接続されているデバイス プラットフォームをシャット ダウンします。

#### <a name="parameters"></a>パラメーター 
* `completionBlock` 

完了時に呼び出すブロックします。