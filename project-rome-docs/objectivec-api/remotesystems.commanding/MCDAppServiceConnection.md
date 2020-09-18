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
# <a name="class-mcdappserviceconnection"></a><span data-ttu-id="28542-105">講義 `MCDAppServiceConnection`</span><span class="sxs-lookup"><span data-stu-id="28542-105">class `MCDAppServiceConnection`</span></span>

```
@interface MCDAppServiceConnection : NSObject
```
<span data-ttu-id="28542-106">このクラスは、特定のリモートアプリサービスへの接続を管理します。</span><span class="sxs-lookup"><span data-stu-id="28542-106">This class manages a connection to a particular remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="28542-107">Properties</span><span class="sxs-lookup"><span data-stu-id="28542-107">Properties</span></span>

### <a name="appserviceinfo"></a><span data-ttu-id="28542-108">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="28542-108">appServiceInfo</span></span>
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="28542-109">接続先の app service に関する詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="28542-109">Provides details about the target app service to connect to.</span></span>

### <a name="requestreceived"></a><span data-ttu-id="28542-110">requestReceived</span><span class="sxs-lookup"><span data-stu-id="28542-110">requestReceived</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

<span data-ttu-id="28542-111">リモートアプリからサービス要求を受信したときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="28542-111">Event for when a service request is received from a remote app.</span></span>

### <a name="serviceclosed"></a><span data-ttu-id="28542-112">serviceClosed</span><span class="sxs-lookup"><span data-stu-id="28542-112">serviceClosed</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

<span data-ttu-id="28542-113">App service への接続が終了したときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="28542-113">Event for when connection to the app service closes.</span></span>

## <a name="constructors"></a><span data-ttu-id="28542-114">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="28542-114">Constructors</span></span>

### <a name="init"></a><span data-ttu-id="28542-115">Init</span><span class="sxs-lookup"><span data-stu-id="28542-115">init</span></span>
`- (nullable instancetype)init;`

<span data-ttu-id="28542-116">このクラスの新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="28542-116">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="28542-117">戻り値</span><span class="sxs-lookup"><span data-stu-id="28542-117">Returns</span></span>
<span data-ttu-id="28542-118">成功した場合は初期化された [MCDAppServiceConnection](MCDAppServiceConnection.md) 。それ以外の場合は nil。</span><span class="sxs-lookup"><span data-stu-id="28542-118">The initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="initwithappserviceinfo"></a><span data-ttu-id="28542-119">initWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="28542-119">initWithAppServiceInfo</span></span>
- <span data-ttu-id="28542-120">(nullable instancetype) initWithAppServiceInfo: (null 以外の MCDAppServiceInfo \*) appServiceInfo;</span><span class="sxs-lookup"><span data-stu-id="28542-120">(nullable instancetype)initWithAppServiceInfo:(nonnull MCDAppServiceInfo\*) appServiceInfo;</span></span>

#### <a name="parameters"></a><span data-ttu-id="28542-121">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28542-121">Parameters</span></span>
* <span data-ttu-id="28542-122">`appServiceInfo` App service の説明。</span><span class="sxs-lookup"><span data-stu-id="28542-122">`appServiceInfo` The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="28542-123">戻り値</span><span class="sxs-lookup"><span data-stu-id="28542-123">Returns</span></span>
<span data-ttu-id="28542-124">成功した場合は初期化された [MCDAppServiceConnection](MCDAppServiceConnection.md) を返し、それ以外の場合は nil を返します。</span><span class="sxs-lookup"><span data-stu-id="28542-124">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="appserviceconnectionwithappserviceinfo"></a><span data-ttu-id="28542-125">appServiceConnectionWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="28542-125">appServiceConnectionWithAppServiceInfo</span></span>
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

<span data-ttu-id="28542-126">App service 情報を使用して、このクラスの新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="28542-126">Creates and initializes a new instance of this class with app service information.</span></span>

#### <a name="parameters"></a><span data-ttu-id="28542-127">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28542-127">Parameters</span></span>
* `appServiceInfo` 

<span data-ttu-id="28542-128">App service の説明。</span><span class="sxs-lookup"><span data-stu-id="28542-128">The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="28542-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="28542-129">Returns</span></span>
<span data-ttu-id="28542-130">成功した場合は初期化された [MCDAppServiceConnection](MCDAppServiceConnection.md) を返し、それ以外の場合は nil を返します。</span><span class="sxs-lookup"><span data-stu-id="28542-130">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

## <a name="methods"></a><span data-ttu-id="28542-131">メソッド</span><span class="sxs-lookup"><span data-stu-id="28542-131">Methods</span></span>

### <a name="openremoteasync"></a><span data-ttu-id="28542-132">openRemoteAsync</span><span class="sxs-lookup"><span data-stu-id="28542-132">openRemoteAsync</span></span>
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

<span data-ttu-id="28542-133">指定したリモートデバイスまたはアプリケーションで、app service 接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="28542-133">Opens the app service connection on the specified remote device or application.</span></span> <span data-ttu-id="28542-134">接続が開けなかった場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="28542-134">If the connection fails to open, an exception is thrown.</span></span>

><span data-ttu-id="28542-135">**注:** 次のいずれかに該当する場合、このメソッドは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="28542-135">**Note:** This method will thrown an exception if any of the following are true:</span></span>
> * <span data-ttu-id="28542-136">接続は既に開いているか、開いています。</span><span class="sxs-lookup"><span data-stu-id="28542-136">The connection is already open or is in the process of opening.</span></span>
> * <span data-ttu-id="28542-137">App service の説明が設定されていないか、消去されています。</span><span class="sxs-lookup"><span data-stu-id="28542-137">The app service description has not been set or has been cleared.</span></span>
> * <span data-ttu-id="28542-138">プラットフォームが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="28542-138">The platform has not been initialized.</span></span>
> * <span data-ttu-id="28542-139">アプリは、接続の "request received" イベントに対してメソッドをサブスクライブしましたが、プラットフォームの初期化時に **MCDNotificationProvider** が提供されていません。</span><span class="sxs-lookup"><span data-stu-id="28542-139">The app has subscribed a method to the connection's "request received" event but has not provided a **MCDNotificationProvider** when initializing the platform.</span></span> <span data-ttu-id="28542-140">すべてのホスティングシナリオには **MCDNotificationProvider**が必要です。</span><span class="sxs-lookup"><span data-stu-id="28542-140">All hosting scenarios require a **MCDNotificationProvider**.</span></span>

#### <a name="parameters"></a><span data-ttu-id="28542-141">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28542-141">Parameters</span></span>
* `connectionRequest` 

<span data-ttu-id="28542-142">対象とするリモートシステムまたはリモートアプリを示す接続要求。</span><span class="sxs-lookup"><span data-stu-id="28542-142">The connection request indicating which remote system or remote app to target.</span></span>

### <a name="sendmessageasync"></a><span data-ttu-id="28542-143">sendMessageAsync</span><span class="sxs-lookup"><span data-stu-id="28542-143">sendMessageAsync</span></span>
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

<span data-ttu-id="28542-144">リモートの app service にメッセージを送信し、応答のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="28542-144">Sends a message to the remote app service and begins listening for a response.</span></span>  <span data-ttu-id="28542-145">このメソッドは、1つのメッセージ/応答を実行し、永続的な接続を確立しません。</span><span class="sxs-lookup"><span data-stu-id="28542-145">This method performs a single message/response and does not establish a persistent connection.</span></span>  <span data-ttu-id="28542-146">接続が正常に開かれた後にのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="28542-146">It should only be called after the connection was opened successfully.</span></span>

#### <a name="parameters"></a><span data-ttu-id="28542-147">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28542-147">Parameters</span></span>
* `message` 

<span data-ttu-id="28542-148">App service に送信されるデータのキーと値のセット。</span><span class="sxs-lookup"><span data-stu-id="28542-148">The key-value set of data to be sent to the app service.</span></span>

### <a name="close"></a><span data-ttu-id="28542-149">閉じる</span><span class="sxs-lookup"><span data-stu-id="28542-149">close</span></span>
`- (void)close;`

<span data-ttu-id="28542-150">リモートの app service への接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="28542-150">Closes the connection to the remote app service.</span></span> <span data-ttu-id="28542-151">クライアントアプリは、ユーザーまたはシステムによって閉じられるか停止されるたびに、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="28542-151">The client app should call this method whenever it is closed or stopped by the user or system.</span></span>

### <a name="sendstatelessmessageasync"></a><span data-ttu-id="28542-152">sendStatelessMessageAsync</span><span class="sxs-lookup"><span data-stu-id="28542-152">sendStatelessMessageAsync</span></span>
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

<span data-ttu-id="28542-153">指定されたリモートアプリサービスにメッセージを送信し、応答のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="28542-153">Sends a message to a specified remote app service and begins listening for a response.</span></span>

#### <a name="parameters"></a><span data-ttu-id="28542-154">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28542-154">Parameters</span></span>
* <span data-ttu-id="28542-155">`message` App service に送信されるデータのキーと値のセット。</span><span class="sxs-lookup"><span data-stu-id="28542-155">`message` The key-value set of data to be sent to the app service.</span></span>
* <span data-ttu-id="28542-156">`appServiceInfo` ターゲット app service の説明情報。</span><span class="sxs-lookup"><span data-stu-id="28542-156">`appServiceInfo` The descriptive info for the target app service.</span></span>
* <span data-ttu-id="28542-157">`connectionRequest` 接続先の app service を指定する接続要求です。</span><span class="sxs-lookup"><span data-stu-id="28542-157">`connectionRequest` The connection request specifying the app service to connect to.</span></span>
* <span data-ttu-id="28542-158">`completion` 非同期完了コールバック。</span><span class="sxs-lookup"><span data-stu-id="28542-158">`completion` The async completion callback.</span></span>