---
title: MCDUserNotification
description: このクラスは、アプリケーションサーバーによって Graph 通知を使用して発行され、アプリクライアントによって受信されるユーザー通知を表します。
keywords: microsoft、ios、graph 通知、操作方法 ios、操作方法 iphone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907894"
---
# <a name="class-mcdusernotification"></a><span data-ttu-id="e961c-104">講義`MCDUserNotification`</span><span class="sxs-lookup"><span data-stu-id="e961c-104">class `MCDUserNotification`</span></span>

```
@interface MCDUserNotification : NSObject
```


<span data-ttu-id="e961c-105">このクラスは、1つのユーザー通知インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="e961c-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="e961c-106">ユーザー通知は、ユーザーを対象としたアプリサーバーによって作成および発行され、同じログインユーザーのすべてのデバイスエンドポイントに配布されます。</span><span class="sxs-lookup"><span data-stu-id="e961c-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="e961c-107">ユーザー通知は、アプリクライアントによって受信されると、対応するプラットフォームのローカル通知 Api を使用して視覚的通知バナーを生成して表示するなどのエクスペリエンスになります。</span><span class="sxs-lookup"><span data-stu-id="e961c-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="e961c-108">Properties</span><span class="sxs-lookup"><span data-stu-id="e961c-108">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="e961c-109">notificationId</span><span class="sxs-lookup"><span data-stu-id="e961c-109">notificationId</span></span>
<span data-ttu-id="e961c-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;`このユーザー通知に対して指定された一意の id を取得します。</span><span class="sxs-lookup"><span data-stu-id="e961c-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Gets the developer specified unique id for this user notification.</span></span>

### <a name="groupid"></a><span data-ttu-id="e961c-111">groupId</span><span class="sxs-lookup"><span data-stu-id="e961c-111">groupId</span></span>
<span data-ttu-id="e961c-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;`このユーザー通知の開発者が指定したグループ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="e961c-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` Gets the developer specified group id for this user notification.</span></span>

### <a name="expirationtime"></a><span data-ttu-id="e961c-113">expirationTime</span><span class="sxs-lookup"><span data-stu-id="e961c-113">expirationTime</span></span>
<span data-ttu-id="e961c-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;`このユーザー通知の有効期限を取得します。</span><span class="sxs-lookup"><span data-stu-id="e961c-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Gets the expiration time for this user notification.</span></span>

### <a name="status"></a><span data-ttu-id="e961c-115">status</span><span class="sxs-lookup"><span data-stu-id="e961c-115">status</span></span>
<span data-ttu-id="e961c-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;`ユーザー通知の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="e961c-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Gets the status of the user notification.</span></span>

### <a name="changetime"></a><span data-ttu-id="e961c-117">changeTime</span><span class="sxs-lookup"><span data-stu-id="e961c-117">changeTime</span></span>
<span data-ttu-id="e961c-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;`変更が行われた時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="e961c-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Gets the time the change was made.</span></span>

### <a name="priority"></a><span data-ttu-id="e961c-119">priority</span><span class="sxs-lookup"><span data-stu-id="e961c-119">priority</span></span>
<span data-ttu-id="e961c-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;`このユーザー通知に対して指定された開発者の優先順位を取得します。</span><span class="sxs-lookup"><span data-stu-id="e961c-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Gets the developer specified priority for this user notification.</span></span>

### <a name="content"></a><span data-ttu-id="e961c-121">content</span><span class="sxs-lookup"><span data-stu-id="e961c-121">content</span></span>
<span data-ttu-id="e961c-122">`@property(nonatomic, readonly, nonnull) NSString* content;`この通知のコンテンツペイロードを取得します。これは、開発者が任意のデータを定義したものです。</span><span class="sxs-lookup"><span data-stu-id="e961c-122">`@property(nonatomic, readonly, nonnull) NSString* content;` Gets the content payload for this notification which is developer defined arbitrary data.</span></span>

###  <a name="readstate"></a><span data-ttu-id="e961c-123">readState</span><span class="sxs-lookup"><span data-stu-id="e961c-123">readState</span></span>
<span data-ttu-id="e961c-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;`通知が開封されたか未読であることを示す、このユーザー通知の読み取り状態の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e961c-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>

### <a name="useractionstate"></a><span data-ttu-id="e961c-125">userActionState</span><span class="sxs-lookup"><span data-stu-id="e961c-125">userActionState</span></span>
<span data-ttu-id="e961c-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;`通知が対話、破棄、アクティブ化、または再通知されていないかどうかを判断するユーザー通知のユーザー操作状態の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e961c-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span> 

## <a name="methods"></a><span data-ttu-id="e961c-127">メソッド</span><span class="sxs-lookup"><span data-stu-id="e961c-127">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="e961c-128">saveAsync</span><span class="sxs-lookup"><span data-stu-id="e961c-128">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="e961c-129">これは、ユーザー通知の変更を発行するときに呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e961c-129">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="e961c-130">アプリケーションが UserNotification の更新可能なプロパティを変更するたびに、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="e961c-130">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="e961c-131">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e961c-131">Parameters</span></span>
* <span data-ttu-id="e961c-132">`completion`完了時に実行するコードブロック。</span><span class="sxs-lookup"><span data-stu-id="e961c-132">`completion` The code block to execute upon completion.</span></span>
