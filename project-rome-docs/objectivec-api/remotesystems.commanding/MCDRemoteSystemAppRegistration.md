---
title: MCDRemoteSystemAppRegistration
description: このクラスは、接続しているデバイス プラットフォームを登録することであるアプリケーションを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 2c931d3eeacd4aa48e1ef22d573bf0325eb5b98b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909914"
---
# <a name="class-mcdremotesystemappregistration"></a>クラス `MCDRemoteSystemAppRegistration` 

```
@interface MCDRemoteSystemAppRegistration : NSObject
```  

このクラスでは、別の検出可能性がありますを使用してこのアプリに関する情報がすべて含まれています。

> [!NOTE] 
> 別のアプリに任意の通信の発信をする可能性がありますする前に、MCDRemoteSystemAppRegistration 情報を公開する必要があります。 これは、その他のアプリケーションが知ることができるようにする通信に応答する方法。

## <a name="properties"></a>プロパティ

### <a name="account"></a>アカウント
`@property(nonatomic, readonly, nullable) MCDConnectedDevicesAccount* account;`

この登録が属しているアカウント。

### <a name="attributes"></a>属性
`@property(nonatomic, copy, nullable) NSDictionary<NSString*, NSString*>* attributes;`

 このアプリの属性を記述する文字列のディクショナリ。

### <a name="appserviceproviders"></a>appServiceProviders
`@property(nonatomic, copy, nullable) NSArray<id<MCDAppServiceProvider>>* appServiceProviders;`

このアプリをサポートする AppServiceProviders の配列。

> [!NOTE] 
> アプリのサービス プロバイダーは、着信接続を受信するためにこの配列に存在する必要があります。  MCDRemoteSystemAppRegistration.publishAsync() は、要求を受信するアプリのサービス プロバイダーに呼び出される必要はありません。  

### <a name="launchuriprovider"></a>launchUriProvider
`@property(nonatomic, readwrite, nullable) id<MCDLaunchUriProvider> launchUriProvider;`

このアプリの Uri のプロバイダーを起動します。

> [!NOTE] 
> 起動 uri のプロバイダーは、受信要求を受信するために、このプロパティに格納する必要があります。  MCDRemoteSystemAppRegistration.publishAsync() は、要求を受信するアプリのサービス プロバイダーに呼び出される必要はありません。  

## <a name="constructors"></a>コンストラクター

### <a name="getforaccount"></a>getForAccount
`+(nullable instancetype) getForAccount:(MCDConnectedDevicesAccount* _Nonnull) account
                              platform:(MCDConnectedDevicesPlatform* _Nonnull) platform;`

アカウントの現在のリモート システムのアプリの登録を取得します。

#### <a name="parameters"></a>パラメーター
* `account` 

アカウントの登録を取得します。

* `platform` 

登録を取得するプラットフォームです。

#### <a name="returns"></a>戻り値
指定したアカウントの MCDRemoteSystemAppRegistration オブジェクトを返します。

## <a name="methods"></a>メソッド

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(BOOL, NSError* _Nullable))callback  __attribute__((deprecated("Use publishAsync instead")));`

他のアプリケーションが検出できるように、RemoteSystemAppRegistration に格納されている情報を保存します。

> [!NOTE] 
> この呼び出しが成功するには、MCDConnectedDevicesNotificationRegistration を登録する必要があります。

> [!WARNING] 
> 使用しないでください。 PublishAsync を代わりに使用します。

#### <a name="parameters"></a>パラメーター

* `callback`

コールバックでは、情報の保存の結果を示します。

### <a name="publishasync"></a>publishAsync
`- (void)publishAsync:(nonnull void (^)(MCDRemoteSystemAppRegistrationPublishResult* _Nonnull, NSError* _Nullable))completionBlock;`

他のアプリケーションが検出できるように、MCDRemoteSystemAppRegistration に格納されている情報を公開します。

> [!NOTE] 
> この呼び出しが成功するには、MCDConnectedDevicesNotificationRegistration を登録する必要があります。

#### <a name="parameters"></a>パラメーター

* `callback`

コールバックでは、情報の保存の結果を示します。
