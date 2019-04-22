---
title: MCDUserNotification
description: このクラスは、グラフの通知を使用して、アプリ サーバーによって発行されたアプリのクライアントによって受信ユーザー通知を表します。
keywords: microsoft、ios、グラフの通知、ios に関する「方法」に関する「方法」の iphone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907894"
---
# <a name="class-mcdusernotification"></a><span data-ttu-id="10abf-104">クラス `MCDUserNotification`</span><span class="sxs-lookup"><span data-stu-id="10abf-104">class `MCDUserNotification`</span></span>

```
@interface MCDUserNotification : NSObject
```


<span data-ttu-id="10abf-105">このクラスは、1 人のユーザー通知のインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="10abf-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="10abf-106">ユーザー通知が作成され、同じログインしているユーザーのすべてのデバイス エンドポイントに分散し、ユーザーを対象としたアプリケーション サーバーによって発行されました。</span><span class="sxs-lookup"><span data-stu-id="10abf-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="10abf-107">アプリのクライアントで受信した後、ユーザーに通知を生成して、対応するプラットフォームのローカル通知 Api を使用して visual 通知バナーの表示などのエクスペリエンス可能性があります。</span><span class="sxs-lookup"><span data-stu-id="10abf-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="10abf-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="10abf-108">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="10abf-109">notificationId</span><span class="sxs-lookup"><span data-stu-id="10abf-109">notificationId</span></span>
<span data-ttu-id="10abf-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` 開発者が指定したを一意に取得このユーザー通知の id。</span><span class="sxs-lookup"><span data-stu-id="10abf-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Gets the developer specified unique id for this user notification.</span></span>

### <a name="groupid"></a><span data-ttu-id="10abf-111">GroupId</span><span class="sxs-lookup"><span data-stu-id="10abf-111">groupId</span></span>
<span data-ttu-id="10abf-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` 開発者が指定したを取得します。 このユーザーの通知グループ id。</span><span class="sxs-lookup"><span data-stu-id="10abf-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` Gets the developer specified group id for this user notification.</span></span>

### <a name="expirationtime"></a><span data-ttu-id="10abf-113">expirationTime</span><span class="sxs-lookup"><span data-stu-id="10abf-113">expirationTime</span></span>
<span data-ttu-id="10abf-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` このユーザー通知の有効期限を取得します。</span><span class="sxs-lookup"><span data-stu-id="10abf-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Gets the expiration time for this user notification.</span></span>

### <a name="status"></a><span data-ttu-id="10abf-115">status</span><span class="sxs-lookup"><span data-stu-id="10abf-115">status</span></span>
<span data-ttu-id="10abf-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` ユーザー通知の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="10abf-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Gets the status of the user notification.</span></span>

### <a name="changetime"></a><span data-ttu-id="10abf-117">changeTime</span><span class="sxs-lookup"><span data-stu-id="10abf-117">changeTime</span></span>
<span data-ttu-id="10abf-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` 変更が行われた時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="10abf-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Gets the time the change was made.</span></span>

### <a name="priority"></a><span data-ttu-id="10abf-119">priority</span><span class="sxs-lookup"><span data-stu-id="10abf-119">priority</span></span>
<span data-ttu-id="10abf-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` 開発者が指定したを取得します。 このユーザー通知の優先順位。</span><span class="sxs-lookup"><span data-stu-id="10abf-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Gets the developer specified priority for this user notification.</span></span>

### <a name="content"></a><span data-ttu-id="10abf-121">content</span><span class="sxs-lookup"><span data-stu-id="10abf-121">content</span></span>
<span data-ttu-id="10abf-122">`@property(nonatomic, readonly, nonnull) NSString* content;` この通知は開発者が定義されている任意のデータをコンテンツ ペイロードを取得します。</span><span class="sxs-lookup"><span data-stu-id="10abf-122">`@property(nonatomic, readonly, nonnull) NSString* content;` Gets the content payload for this notification which is developer defined arbitrary data.</span></span>

###  <a name="readstate"></a><span data-ttu-id="10abf-123">ReadState</span><span class="sxs-lookup"><span data-stu-id="10abf-123">readState</span></span>
<span data-ttu-id="10abf-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` このユーザーを示す通知が、通知は、読み取り、または未読の読み取りの状態の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="10abf-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>

### <a name="useractionstate"></a><span data-ttu-id="10abf-125">userActionState</span><span class="sxs-lookup"><span data-stu-id="10abf-125">userActionState</span></span>
<span data-ttu-id="10abf-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` かどうか、通知がない操作、消去された、アクティブ化、または再を判断するユーザー通知のユーザー アクションの状態の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="10abf-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span> 

## <a name="methods"></a><span data-ttu-id="10abf-127">メソッド</span><span class="sxs-lookup"><span data-stu-id="10abf-127">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="10abf-128">saveAsync</span><span class="sxs-lookup"><span data-stu-id="10abf-128">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="10abf-129">これは、ユーザー通知の変更を発行するときに呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="10abf-129">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="10abf-130">アプリが、UserNotification の更新可能なプロパティを変更するたびに、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="10abf-130">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="10abf-131">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10abf-131">Parameters</span></span>
* <span data-ttu-id="10abf-132">`completion` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="10abf-132">`completion` The code block to execute upon completion.</span></span>
