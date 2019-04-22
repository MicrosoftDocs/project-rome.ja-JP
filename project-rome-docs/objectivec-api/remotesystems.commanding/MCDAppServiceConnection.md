---
title: MCDAppServiceConnection
description: このクラスは、特定のリモート アプリ サービスへの接続を管理します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 22e253f137642ad609a22af33aa62e2ef9543503
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58908544"
---
# <a name="class-mcdappserviceconnection"></a><span data-ttu-id="ebe39-104">クラス `MCDAppServiceConnection`</span><span class="sxs-lookup"><span data-stu-id="ebe39-104">class `MCDAppServiceConnection`</span></span>

```
@interface MCDAppServiceConnection : NSObject
```
<span data-ttu-id="ebe39-105">このクラスは、特定のリモート アプリ サービスへの接続を管理します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-105">This class manages a connection to a particular remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="ebe39-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ebe39-106">Properties</span></span>

### <a name="appserviceinfo"></a><span data-ttu-id="ebe39-107">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="ebe39-107">appServiceInfo</span></span>
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="ebe39-108">ターゲット app service に接続するための詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-108">Provides details about the target app service to connect to.</span></span>

### <a name="requestreceived"></a><span data-ttu-id="ebe39-109">requestReceived</span><span class="sxs-lookup"><span data-stu-id="ebe39-109">requestReceived</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

<span data-ttu-id="ebe39-110">リモート アプリからサービス要求を受信したときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="ebe39-110">Event for when a service request is received from a remote app.</span></span>

### <a name="serviceclosed"></a><span data-ttu-id="ebe39-111">serviceClosed</span><span class="sxs-lookup"><span data-stu-id="ebe39-111">serviceClosed</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

<span data-ttu-id="ebe39-112">App service への接続を閉じたときのイベントです。</span><span class="sxs-lookup"><span data-stu-id="ebe39-112">Event for when connection to the app service closes.</span></span>

## <a name="constructors"></a><span data-ttu-id="ebe39-113">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ebe39-113">Constructors</span></span>

### <a name="init"></a><span data-ttu-id="ebe39-114">Init</span><span class="sxs-lookup"><span data-stu-id="ebe39-114">init</span></span>
`- (nullable instancetype)init;`

<span data-ttu-id="ebe39-115">作成し、このクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="ebe39-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="ebe39-116">Returns</span></span>
<span data-ttu-id="ebe39-117">初期化された[MCDAppServiceConnection](MCDAppServiceConnection.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-117">The initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="initwithappserviceinfo"></a><span data-ttu-id="ebe39-118">initWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="ebe39-118">initWithAppServiceInfo</span></span>
- <span data-ttu-id="ebe39-119">(null 許容 instancetype) initWithAppServiceInfo:(nonnull MCDAppServiceInfo\*) appServiceInfo;</span><span class="sxs-lookup"><span data-stu-id="ebe39-119">(nullable instancetype)initWithAppServiceInfo:(nonnull MCDAppServiceInfo\*) appServiceInfo;</span></span>

#### <a name="parameters"></a><span data-ttu-id="ebe39-120">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebe39-120">Parameters</span></span>
* <span data-ttu-id="ebe39-121">`appServiceInfo` アプリ サービスの説明。</span><span class="sxs-lookup"><span data-stu-id="ebe39-121">`appServiceInfo` The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="ebe39-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="ebe39-122">Returns</span></span>
<span data-ttu-id="ebe39-123">返しますが、初期化された[MCDAppServiceConnection](MCDAppServiceConnection.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-123">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="appserviceconnectionwithappserviceinfo"></a><span data-ttu-id="ebe39-124">appServiceConnectionWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="ebe39-124">appServiceConnectionWithAppServiceInfo</span></span>
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

<span data-ttu-id="ebe39-125">作成し、アプリ サービスの情報をこのクラスの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-125">Creates and initializes a new instance of this class with app service information.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ebe39-126">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebe39-126">Parameters</span></span>
* `appServiceInfo` 

<span data-ttu-id="ebe39-127">アプリ サービスの説明。</span><span class="sxs-lookup"><span data-stu-id="ebe39-127">The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="ebe39-128">戻り値</span><span class="sxs-lookup"><span data-stu-id="ebe39-128">Returns</span></span>
<span data-ttu-id="ebe39-129">返しますが、初期化された[MCDAppServiceConnection](MCDAppServiceConnection.md)成功した場合、それ以外の場合の nil します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-129">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

## <a name="methods"></a><span data-ttu-id="ebe39-130">メソッド</span><span class="sxs-lookup"><span data-stu-id="ebe39-130">Methods</span></span>

### <a name="openremoteasync"></a><span data-ttu-id="ebe39-131">openRemoteAsync</span><span class="sxs-lookup"><span data-stu-id="ebe39-131">openRemoteAsync</span></span>
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

<span data-ttu-id="ebe39-132">指定したリモート デバイス上でアプリケーションのアプリのサービス接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="ebe39-132">Opens the app service connection on the specified remote device or application.</span></span> <span data-ttu-id="ebe39-133">開き、接続に失敗した場合、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ebe39-133">If the connection fails to open, an exception is thrown.</span></span>

><span data-ttu-id="ebe39-134">**注:** このメソッドは、次のいずれかに該当する場合、例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="ebe39-134">**Note:** This method will thrown an exception if any of the following are true:</span></span>
> * <span data-ttu-id="ebe39-135">接続が既に開いているか、開く処理です。</span><span class="sxs-lookup"><span data-stu-id="ebe39-135">The connection is already open or is in the process of opening.</span></span>
> * <span data-ttu-id="ebe39-136">アプリ サービスの説明では、設定されていないかがクリアされました。</span><span class="sxs-lookup"><span data-stu-id="ebe39-136">The app service description has not been set or has been cleared.</span></span>
> * <span data-ttu-id="ebe39-137">プラットフォームが初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="ebe39-137">The platform has not been initialized.</span></span>
> * <span data-ttu-id="ebe39-138">アプリは、メソッド、接続の「要求を受信しました」のイベントをサブスクライブしているもののが指定されていない、 **MCDNotificationProvider**プラットフォームを初期化するときにします。</span><span class="sxs-lookup"><span data-stu-id="ebe39-138">The app has subscribed a method to the connection's "request received" event but has not provided a **MCDNotificationProvider** when initializing the platform.</span></span> <span data-ttu-id="ebe39-139">すべてのホスティング シナリオが必要です、 **MCDNotificationProvider**します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-139">All hosting scenarios require a **MCDNotificationProvider**.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ebe39-140">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebe39-140">Parameters</span></span>
* `connectionRequest` 

<span data-ttu-id="ebe39-141">どのリモート システムまたはターゲットへのリモート アプリを示す接続要求。</span><span class="sxs-lookup"><span data-stu-id="ebe39-141">The connection request indicating which remote system or remote app to target.</span></span>

### <a name="sendmessageasync"></a><span data-ttu-id="ebe39-142">sendMessageAsync</span><span class="sxs-lookup"><span data-stu-id="ebe39-142">sendMessageAsync</span></span>
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

<span data-ttu-id="ebe39-143">リモート アプリ サービスにメッセージを送信し、応答のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-143">Sends a message to the remote app service and begins listening for a response.</span></span>  <span data-ttu-id="ebe39-144">このメソッドは、1 つのメッセージと応答を実行し、永続的な接続を確立できません。</span><span class="sxs-lookup"><span data-stu-id="ebe39-144">This method performs a single message/response and does not establish a persistent connection.</span></span>  <span data-ttu-id="ebe39-145">また、接続が正常に開かれた後にのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebe39-145">It should only be called after the connection was opened successfully.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ebe39-146">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebe39-146">Parameters</span></span>
* `message` 

<span data-ttu-id="ebe39-147">App service に送信されるデータのキーと値のセット。</span><span class="sxs-lookup"><span data-stu-id="ebe39-147">The key-value set of data to be sent to the app service.</span></span>

### <a name="close"></a><span data-ttu-id="ebe39-148">close</span><span class="sxs-lookup"><span data-stu-id="ebe39-148">close</span></span>
`- (void)close;`

<span data-ttu-id="ebe39-149">リモートの app service への接続を閉じます。</span><span class="sxs-lookup"><span data-stu-id="ebe39-149">Closes the connection to the remote app service.</span></span> <span data-ttu-id="ebe39-150">閉じているか、ユーザーまたはシステムによって停止されるたびに、クライアント アプリはこのメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebe39-150">The client app should call this method whenever it is closed or stopped by the user or system.</span></span>

### <a name="sendstatelessmessageasync"></a><span data-ttu-id="ebe39-151">sendStatelessMessageAsync</span><span class="sxs-lookup"><span data-stu-id="ebe39-151">sendStatelessMessageAsync</span></span>
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

<span data-ttu-id="ebe39-152">指定したリモート アプリ サービスにメッセージを送信し、応答のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="ebe39-152">Sends a message to a specified remote app service and begins listening for a response.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ebe39-153">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ebe39-153">Parameters</span></span>
* <span data-ttu-id="ebe39-154">`message` App service に送信されるデータのキーと値のセット。</span><span class="sxs-lookup"><span data-stu-id="ebe39-154">`message` The key-value set of data to be sent to the app service.</span></span>
* <span data-ttu-id="ebe39-155">`appServiceInfo` ターゲット app service のわかりやすい情報です。</span><span class="sxs-lookup"><span data-stu-id="ebe39-155">`appServiceInfo` The descriptive info for the target app service.</span></span>
* <span data-ttu-id="ebe39-156">`connectionRequest` 接続するため、app service を指定する接続要求。</span><span class="sxs-lookup"><span data-stu-id="ebe39-156">`connectionRequest` The connection request specifying the app service to connect to.</span></span>
* <span data-ttu-id="ebe39-157">`completion` 完了時の非同期コールバック。</span><span class="sxs-lookup"><span data-stu-id="ebe39-157">`completion` The async completion callback.</span></span>