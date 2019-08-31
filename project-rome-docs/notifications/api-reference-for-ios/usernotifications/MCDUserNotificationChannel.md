---
title: MCDUserNotificationChannel
description: このクラスは、ユーザー通知のライフサイクルを管理します。
keywords: microsoft、windows、device relay、how to iOS、how to iPhone
ms.openlocfilehash: 234e1af807ac816918fe1de37a18dc07f73fca09
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801244"
---
# <a name="class-mcdusernotificationchannel"></a><span data-ttu-id="85e1a-104">講義`MCDUserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="85e1a-104">class `MCDUserNotificationChannel`</span></span>

```
@interface MCDUserNotificationChannel : NSObject
```

<span data-ttu-id="85e1a-105">このクラスは、アプリケーションのユーザー通知の受信と管理を処理する通知変更リーダーを提供します。</span><span class="sxs-lookup"><span data-stu-id="85e1a-105">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="properties"></a><span data-ttu-id="85e1a-106">Properties</span><span class="sxs-lookup"><span data-stu-id="85e1a-106">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="85e1a-107">syncScope</span><span class="sxs-lookup"><span data-stu-id="85e1a-107">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="85e1a-108">UserNotifications がフィードに含まれることを保証するために使用される SyncScope。</span><span class="sxs-lookup"><span data-stu-id="85e1a-108">SyncScope used to ensure UserNotifications are included in the feed.</span></span>

## <a name="constructors"></a><span data-ttu-id="85e1a-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="85e1a-109">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="85e1a-110">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="85e1a-110">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a><span data-ttu-id="85e1a-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="85e1a-111">Parameters</span></span>

### <a name="userdatafeed"></a><span data-ttu-id="85e1a-112">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="85e1a-112">userDataFeed</span></span>
<span data-ttu-id="85e1a-113">このクラスを初期化するために使用される MCDUserDataFeed。</span><span class="sxs-lookup"><span data-stu-id="85e1a-113">The MCDUserDataFeed used to initialize this class.</span></span>

### <a name="initwithuserdatafeed"></a><span data-ttu-id="85e1a-114">initWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="85e1a-114">initWithUserDataFeed</span></span>
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a><span data-ttu-id="85e1a-115">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="85e1a-115">userDataFeed</span></span>
<span data-ttu-id="85e1a-116">このクラスを初期化するために使用される MCDUserDataFeed。</span><span class="sxs-lookup"><span data-stu-id="85e1a-116">The MCDUserDataFeed used to initialize this class.</span></span>

## <a name="methods"></a><span data-ttu-id="85e1a-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="85e1a-117">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="85e1a-118">createReader</span><span class="sxs-lookup"><span data-stu-id="85e1a-118">createReader</span></span>
`- (MCDUserNotificationReader* _Nullable)createReader`

<span data-ttu-id="85e1a-119">アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="85e1a-119">Create a user notification reader to receive and manage user notifications published by app server.</span></span>

### <a name="createreaderwithoptions"></a><span data-ttu-id="85e1a-120">createReaderWithOptions</span><span class="sxs-lookup"><span data-stu-id="85e1a-120">createReaderWithOptions</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

<span data-ttu-id="85e1a-121">オプションを使用してユーザー通知リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="85e1a-121">Create a user notification reader with options.</span></span>

### <a name="createreaderwithstate"></a><span data-ttu-id="85e1a-122">createReaderWithState</span><span class="sxs-lookup"><span data-stu-id="85e1a-122">createReaderWithState</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

<span data-ttu-id="85e1a-123">アプリサーバーによって発行されたユーザー通知を受信して管理するユーザー通知リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="85e1a-123">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="85e1a-124">リーダーは、指定された追跡状態から開始されます。</span><span class="sxs-lookup"><span data-stu-id="85e1a-124">The reader will start at the provided tracking state.</span></span>  

### <a name="getusernotificationasync"></a><span data-ttu-id="85e1a-125">getUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="85e1a-125">getUserNotificationAsync</span></span>
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

<span data-ttu-id="85e1a-126">Id に基づいてユーザーの通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="85e1a-126">Get a user notification based on its id.</span></span>

### <a name="deleteusernotificationasync"></a><span data-ttu-id="85e1a-127">deleteUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="85e1a-127">deleteUserNotificationAsync</span></span>
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

<span data-ttu-id="85e1a-128">Id に基づいてユーザー通知を削除します。</span><span class="sxs-lookup"><span data-stu-id="85e1a-128">Delete a user notification based on its id.</span></span> 