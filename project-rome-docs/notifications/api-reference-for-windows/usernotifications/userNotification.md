---
title: UserNotification
description: このクラスは、グラフの通知を使用して、アプリ サーバーによって発行されたアプリのクライアントによって受信ユーザー通知を表します。
keywords: microsoft、windows、グラフの通知、使い方 windows
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801594"
---
# <a name="class-usernotification"></a><span data-ttu-id="3cd11-104">クラス `UserNotification`</span><span class="sxs-lookup"><span data-stu-id="3cd11-104">class `UserNotification`</span></span>

```C#
public sealed class UserNotification : IUserNotification
```

<span data-ttu-id="3cd11-105">このクラスは、1 人のユーザー通知のインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="3cd11-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="3cd11-106">ユーザー通知が作成され、同じログインしているユーザーのすべてのデバイス エンドポイントに分散し、ユーザーを対象としたアプリケーション サーバーによって発行されました。</span><span class="sxs-lookup"><span data-stu-id="3cd11-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="3cd11-107">アプリのクライアントで受信した後、ユーザーに通知を生成して、対応するプラットフォームのローカル通知 Api を使用して visual 通知バナーの表示などのエクスペリエンス可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3cd11-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="3cd11-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3cd11-108">Properties</span></span>

|<span data-ttu-id="3cd11-109">名前</span><span class="sxs-lookup"><span data-stu-id="3cd11-109">Name</span></span> | <span data-ttu-id="3cd11-110">説明</span><span class="sxs-lookup"><span data-stu-id="3cd11-110">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="3cd11-111">ID</span><span class="sxs-lookup"><span data-stu-id="3cd11-111">Id</span></span> |<span data-ttu-id="3cd11-112">開発者が指定したを一意に取得このユーザー通知の id。</span><span class="sxs-lookup"><span data-stu-id="3cd11-112">Gets the developer specified unique id for this user notification.</span></span>|
|   <span data-ttu-id="3cd11-113">GroupId</span><span class="sxs-lookup"><span data-stu-id="3cd11-113">GroupId</span></span> |<span data-ttu-id="3cd11-114">開発者が指定したを取得します。 このユーザーの通知グループ id。</span><span class="sxs-lookup"><span data-stu-id="3cd11-114">Gets the developer specified group id for this user notification.</span></span>| 
|   <span data-ttu-id="3cd11-115">ExpirationTime</span><span class="sxs-lookup"><span data-stu-id="3cd11-115">ExpirationTime</span></span> |<span data-ttu-id="3cd11-116">このユーザー通知の有効期限を取得します。</span><span class="sxs-lookup"><span data-stu-id="3cd11-116">Gets the expiration time for this user notification.</span></span>| 
|   <span data-ttu-id="3cd11-117">Priority</span><span class="sxs-lookup"><span data-stu-id="3cd11-117">Priority</span></span>|<span data-ttu-id="3cd11-118">開発者が指定したを取得します。 このユーザー通知の優先順位。</span><span class="sxs-lookup"><span data-stu-id="3cd11-118">Gets the developer specified priority for this user notification.</span></span>| 
|   <span data-ttu-id="3cd11-119">Content</span><span class="sxs-lookup"><span data-stu-id="3cd11-119">Content</span></span>|<span data-ttu-id="3cd11-120">この通知は開発者が定義されている任意のデータをコンテンツ ペイロードを取得します。</span><span class="sxs-lookup"><span data-stu-id="3cd11-120">Gets the content payload for this notification which is developer defined arbitrary data.</span></span>| 
|   <span data-ttu-id="3cd11-121">ReadState</span><span class="sxs-lookup"><span data-stu-id="3cd11-121">ReadState</span></span>|<span data-ttu-id="3cd11-122">このユーザーを示す通知が、通知は、読み取り、または未読の読み取りの状態の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3cd11-122">Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>| 
|   <span data-ttu-id="3cd11-123">UserActionState</span><span class="sxs-lookup"><span data-stu-id="3cd11-123">UserActionState</span></span>|<span data-ttu-id="3cd11-124">かどうか、通知がない操作、消去された、アクティブ化、または再を判断するユーザー通知のユーザー アクションの状態の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3cd11-124">Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span>| 


## <a name="methods"></a><span data-ttu-id="3cd11-125">メソッド</span><span class="sxs-lookup"><span data-stu-id="3cd11-125">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="3cd11-126">SaveAsync()</span><span class="sxs-lookup"><span data-stu-id="3cd11-126">SaveAsync()</span></span> 
<span data-ttu-id="3cd11-127">これは、ユーザー通知の変更を発行するときに呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cd11-127">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="3cd11-128">アプリが、UserNotification の更新可能なプロパティを変更するたびに、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="3cd11-128">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>
```C#
public IAsyncOperation SaveAsync()
```

