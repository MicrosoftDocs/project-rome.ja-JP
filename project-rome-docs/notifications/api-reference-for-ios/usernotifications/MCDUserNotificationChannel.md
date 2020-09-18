---
title: MCDUserNotificationChannel
description: MCDUserNotificationChannel クラスについて説明します。 このクラスは、ユーザー通知のライフサイクルを管理します。
keywords: microsoft、windows、device relay、how to iOS、how to iPhone
ms.openlocfilehash: dc7e451494014cdcdebd056b00e57cfdf5f0757f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760876"
---
# <a name="class-mcdusernotificationchannel"></a><span data-ttu-id="41b27-105">講義 `MCDUserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="41b27-105">class `MCDUserNotificationChannel`</span></span>

```
@interface MCDUserNotificationChannel : NSObject
```

<span data-ttu-id="41b27-106">このクラスは、アプリケーションのユーザー通知の受信と管理を処理する通知変更リーダーを提供します。</span><span class="sxs-lookup"><span data-stu-id="41b27-106">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="properties"></a><span data-ttu-id="41b27-107">Properties</span><span class="sxs-lookup"><span data-stu-id="41b27-107">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="41b27-108">syncScope</span><span class="sxs-lookup"><span data-stu-id="41b27-108">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="41b27-109">UserNotifications がフィードに含まれることを保証するために使用される SyncScope。</span><span class="sxs-lookup"><span data-stu-id="41b27-109">SyncScope used to ensure UserNotifications are included in the feed.</span></span>

## <a name="constructors"></a><span data-ttu-id="41b27-110">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="41b27-110">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="41b27-111">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="41b27-111">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a><span data-ttu-id="41b27-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41b27-112">Parameters</span></span>

### <a name="userdatafeed"></a><span data-ttu-id="41b27-113">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="41b27-113">userDataFeed</span></span>
<span data-ttu-id="41b27-114">このクラスを初期化するために使用される MCDUserDataFeed。</span><span class="sxs-lookup"><span data-stu-id="41b27-114">The MCDUserDataFeed used to initialize this class.</span></span>

### <a name="initwithuserdatafeed"></a><span data-ttu-id="41b27-115">initWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="41b27-115">initWithUserDataFeed</span></span>
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a><span data-ttu-id="41b27-116">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="41b27-116">userDataFeed</span></span>
<span data-ttu-id="41b27-117">このクラスを初期化するために使用される MCDUserDataFeed。</span><span class="sxs-lookup"><span data-stu-id="41b27-117">The MCDUserDataFeed used to initialize this class.</span></span>

## <a name="methods"></a><span data-ttu-id="41b27-118">メソッド</span><span class="sxs-lookup"><span data-stu-id="41b27-118">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="41b27-119">createReader</span><span class="sxs-lookup"><span data-stu-id="41b27-119">createReader</span></span>
`- (MCDUserNotificationReader* _Nullable)createReader`

<span data-ttu-id="41b27-120">アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="41b27-120">Create a user notification reader to receive and manage user notifications published by app server.</span></span>

### <a name="createreaderwithoptions"></a><span data-ttu-id="41b27-121">createReaderWithOptions</span><span class="sxs-lookup"><span data-stu-id="41b27-121">createReaderWithOptions</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

<span data-ttu-id="41b27-122">オプションを使用してユーザー通知リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="41b27-122">Create a user notification reader with options.</span></span>

### <a name="createreaderwithstate"></a><span data-ttu-id="41b27-123">createReaderWithState</span><span class="sxs-lookup"><span data-stu-id="41b27-123">createReaderWithState</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

<span data-ttu-id="41b27-124">アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="41b27-124">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="41b27-125">リーダーは、指定された追跡状態から開始されます。</span><span class="sxs-lookup"><span data-stu-id="41b27-125">The reader will start at the provided tracking state.</span></span>  

### <a name="getusernotificationasync"></a><span data-ttu-id="41b27-126">getUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="41b27-126">getUserNotificationAsync</span></span>
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

<span data-ttu-id="41b27-127">Id に基づいてユーザーの通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="41b27-127">Get a user notification based on its id.</span></span>

### <a name="deleteusernotificationasync"></a><span data-ttu-id="41b27-128">deleteUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="41b27-128">deleteUserNotificationAsync</span></span>
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

<span data-ttu-id="41b27-129">Id に基づいてユーザー通知を削除します。</span><span class="sxs-lookup"><span data-stu-id="41b27-129">Delete a user notification based on its id.</span></span> 