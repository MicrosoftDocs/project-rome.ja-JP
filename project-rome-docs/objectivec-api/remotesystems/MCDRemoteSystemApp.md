---
title: MCDRemoteSystemApp
description: 接続に使用されるリモート システム上のアプリケーションを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 28ec3fbe03150cb45c0a554a0499f1a6b657e50d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801584"
---
# <a name="class-mcdremotesystemapp"></a>クラス `MCDRemoteSystemApp` 

```
@interface MCDRemoteSystemApp : NSObject
```  

接続に使用されるリモート システム上のアプリケーションを表します。

## <a name="properties"></a>プロパティ

### <a name="appid"></a>AppId
`@property(nonatomic, readonly, nonnull) NSString* appId;`

このアプリケーションの一意の識別子。

### <a name="displayname"></a>displayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

このアプリケーションのわかりやすい表示名。 Bluetooth の識別については、デバイスで使用される名前です。 これが設定されていないか、デバイスが Bluetooth をサポートされていません、このフィールドは空になります。

### <a name="availablebyproximity"></a>availableByProximity
`@property(nonatomic, readonly, getter=isAvailableByProximity) BOOL availableByProximity;`

このアプリケーションが位の接続で現在使用できるかどうかを示します。

### <a name="availablebyspatialproximity"></a>availableBySpatialProximity
`@property(nonatomic, readonly, getter=isAvailableBySpatialProximity) BOOL availableBySpatialProximity;`

このアプリケーションは、空間の共有接続で現在使用できるかどうかを示します。

### <a name="attributes"></a>属性
`@property(nonatomic, readonly, nonnull) NSDictionary<NSString*, NSString*>* attributes;`

このアプリケーションの属性を定義するキー/値ペアのディクショナリ。

### <a name="appservices"></a>appServices
`@property(nonatomic, readonly, nullable) NSArray<MCDAppServiceDescription*>* appServices;`

このアプリケーションがリモート接続用に提供するアプリ サービスを記述する MCDAppServiceDescription インスタンスの配列。

### <a name="accounts"></a>アカウント
`@property(nonatomic, readonly, nullable) NSArray<MCDConnectedDevicesAccount*>* accounts;`

アクセス許可について知っておく必要のある MCDRemoteSystemApp に関連付けられているアカウント。 MCDRemoteSystemWatcher が開始されると、MCDConnectedDevicesAccountManager で、MCDConnectedDevicesAccount が存在するかどうかは、アクセス許可が決まります。