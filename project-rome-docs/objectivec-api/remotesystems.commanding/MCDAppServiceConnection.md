---
title: MCDAppServiceConnection
description: このクラスは、特定のリモート アプリ サービスへの接続を管理します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 22e253f137642ad609a22af33aa62e2ef9543503
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908544"
---
# <a name="class-mcdappserviceconnection"></a>クラス `MCDAppServiceConnection`

```
@interface MCDAppServiceConnection : NSObject
```
このクラスは、特定のリモート アプリ サービスへの接続を管理します。

## <a name="properties"></a>プロパティ

### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

ターゲット app service に接続するための詳細を提供します。

### <a name="requestreceived"></a>requestReceived 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

リモート アプリからサービス要求を受信したときのイベントです。

### <a name="serviceclosed"></a>serviceClosed 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

App service への接続を閉じたときのイベントです。

## <a name="constructors"></a>コンストラクター

### <a name="init"></a>Init
`- (nullable instancetype)init;`

作成し、このクラスの新しいインスタンスを初期化します。

#### <a name="returns"></a>戻り値
初期化された[MCDAppServiceConnection](MCDAppServiceConnection.md)成功した場合、それ以外の場合の nil します。

### <a name="initwithappserviceinfo"></a>initWithAppServiceInfo
- (null 許容 instancetype) initWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;

#### <a name="parameters"></a>パラメーター
* `appServiceInfo` アプリ サービスの説明。

#### <a name="returns"></a>戻り値
返しますが、初期化された[MCDAppServiceConnection](MCDAppServiceConnection.md)成功した場合、それ以外の場合の nil します。

### <a name="appserviceconnectionwithappserviceinfo"></a>appServiceConnectionWithAppServiceInfo
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

作成し、アプリ サービスの情報をこのクラスの新しいインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター
* `appServiceInfo` 

アプリ サービスの説明。

#### <a name="returns"></a>戻り値
返しますが、初期化された[MCDAppServiceConnection](MCDAppServiceConnection.md)成功した場合、それ以外の場合の nil します。

## <a name="methods"></a>メソッド

### <a name="openremoteasync"></a>openRemoteAsync
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

指定したリモート デバイス上でアプリケーションのアプリのサービス接続を開きます。 開き、接続に失敗した場合、例外がスローされます。

>**注:** このメソッドは、次のいずれかに該当する場合、例外がスローされました。
> * 接続が既に開いているか、開く処理です。
> * アプリ サービスの説明では、設定されていないかがクリアされました。
> * プラットフォームが初期化されていません。
> * アプリは、メソッド、接続の「要求を受信しました」のイベントをサブスクライブしているもののが指定されていない、 **MCDNotificationProvider**プラットフォームを初期化するときにします。 すべてのホスティング シナリオが必要です、 **MCDNotificationProvider**します。

#### <a name="parameters"></a>パラメーター
* `connectionRequest` 

どのリモート システムまたはターゲットへのリモート アプリを示す接続要求。

### <a name="sendmessageasync"></a>sendMessageAsync
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

リモート アプリ サービスにメッセージを送信し、応答のリッスンを開始します。  このメソッドは、1 つのメッセージと応答を実行し、永続的な接続を確立できません。  また、接続が正常に開かれた後にのみ呼び出す必要があります。

#### <a name="parameters"></a>パラメーター
* `message` 

App service に送信されるデータのキーと値のセット。

### <a name="close"></a>close
`- (void)close;`

リモートの app service への接続を閉じます。 閉じているか、ユーザーまたはシステムによって停止されるたびに、クライアント アプリはこのメソッドを呼び出す必要があります。

### <a name="sendstatelessmessageasync"></a>sendStatelessMessageAsync
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

指定したリモート アプリ サービスにメッセージを送信し、応答のリッスンを開始します。

#### <a name="parameters"></a>パラメーター
* `message` App service に送信されるデータのキーと値のセット。
* `appServiceInfo` ターゲット app service のわかりやすい情報です。
* `connectionRequest` 接続するため、app service を指定する接続要求。
* `completion` 完了時の非同期コールバック。