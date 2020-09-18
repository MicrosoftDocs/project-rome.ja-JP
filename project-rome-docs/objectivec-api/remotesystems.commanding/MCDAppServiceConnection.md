---
title: MCDAppServiceConnection
description: MCDAppServiceConnection クラスについて説明します。 このクラスは、特定のリモートアプリサービスへの接続を管理します。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 2d9153eeddb9010ac40ab37d9adb433edd11b0ca
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761056"
---
# <a name="class-mcdappserviceconnection"></a>講義 `MCDAppServiceConnection`

```
@interface MCDAppServiceConnection : NSObject
```
このクラスは、特定のリモートアプリサービスへの接続を管理します。

## <a name="properties"></a>Properties

### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

接続先の app service に関する詳細を提供します。

### <a name="requestreceived"></a>requestReceived 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

リモートアプリからサービス要求を受信したときのイベントです。

### <a name="serviceclosed"></a>serviceClosed 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

App service への接続が終了したときのイベントです。

## <a name="constructors"></a>コンストラクター

### <a name="init"></a>Init
`- (nullable instancetype)init;`

このクラスの新しいインスタンスを作成して初期化します。

#### <a name="returns"></a>戻り値
成功した場合は初期化された [MCDAppServiceConnection](MCDAppServiceConnection.md) 。それ以外の場合は nil。

### <a name="initwithappserviceinfo"></a>initWithAppServiceInfo
- (nullable instancetype) initWithAppServiceInfo: (null 以外の MCDAppServiceInfo *) appServiceInfo;

#### <a name="parameters"></a>パラメーター
* `appServiceInfo` App service の説明。

#### <a name="returns"></a>戻り値
成功した場合は初期化された [MCDAppServiceConnection](MCDAppServiceConnection.md) を返し、それ以外の場合は nil を返します。

### <a name="appserviceconnectionwithappserviceinfo"></a>appServiceConnectionWithAppServiceInfo
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

App service 情報を使用して、このクラスの新しいインスタンスを作成して初期化します。

#### <a name="parameters"></a>パラメーター
* `appServiceInfo` 

App service の説明。

#### <a name="returns"></a>戻り値
成功した場合は初期化された [MCDAppServiceConnection](MCDAppServiceConnection.md) を返し、それ以外の場合は nil を返します。

## <a name="methods"></a>メソッド

### <a name="openremoteasync"></a>openRemoteAsync
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

指定したリモートデバイスまたはアプリケーションで、app service 接続を開きます。 接続が開けなかった場合は、例外がスローされます。

>**注:** 次のいずれかに該当する場合、このメソッドは例外をスローします。
> * 接続は既に開いているか、開いています。
> * App service の説明が設定されていないか、消去されています。
> * プラットフォームが初期化されていません。
> * アプリは、接続の "request received" イベントに対してメソッドをサブスクライブしましたが、プラットフォームの初期化時に **MCDNotificationProvider** が提供されていません。 すべてのホスティングシナリオには **MCDNotificationProvider**が必要です。

#### <a name="parameters"></a>パラメーター
* `connectionRequest` 

対象とするリモートシステムまたはリモートアプリを示す接続要求。

### <a name="sendmessageasync"></a>sendMessageAsync
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

リモートの app service にメッセージを送信し、応答のリッスンを開始します。  このメソッドは、1つのメッセージ/応答を実行し、永続的な接続を確立しません。  接続が正常に開かれた後にのみ呼び出す必要があります。

#### <a name="parameters"></a>パラメーター
* `message` 

App service に送信されるデータのキーと値のセット。

### <a name="close"></a>閉じる
`- (void)close;`

リモートの app service への接続を閉じます。 クライアントアプリは、ユーザーまたはシステムによって閉じられるか停止されるたびに、このメソッドを呼び出す必要があります。

### <a name="sendstatelessmessageasync"></a>sendStatelessMessageAsync
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

指定されたリモートアプリサービスにメッセージを送信し、応答のリッスンを開始します。

#### <a name="parameters"></a>パラメーター
* `message` App service に送信されるデータのキーと値のセット。
* `appServiceInfo` ターゲット app service の説明情報。
* `connectionRequest` 接続先の app service を指定する接続要求です。
* `completion` 非同期完了コールバック。