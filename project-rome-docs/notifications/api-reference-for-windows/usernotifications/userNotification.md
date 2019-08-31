---
title: UserNotification
description: このクラスは、アプリケーションサーバーによって Graph 通知を使用して発行され、アプリクライアントによって受信されるユーザー通知を表します。
keywords: microsoft、windows、graph 通知、操作方法ウィンドウ
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801594"
---
# <a name="class-usernotification"></a><span data-ttu-id="1b2ad-104">講義`UserNotification`</span><span class="sxs-lookup"><span data-stu-id="1b2ad-104">class `UserNotification`</span></span>

```C#
public sealed class UserNotification : IUserNotification
```

<span data-ttu-id="1b2ad-105">このクラスは、1つのユーザー通知インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="1b2ad-106">ユーザー通知は、ユーザーを対象としたアプリサーバーによって作成および発行され、同じログインユーザーのすべてのデバイスエンドポイントに配布されます。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="1b2ad-107">ユーザー通知は、アプリクライアントによって受信されると、対応するプラットフォームのローカル通知 Api を使用して視覚的通知バナーを生成して表示するなどのエクスペリエンスになります。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="1b2ad-108">Properties</span><span class="sxs-lookup"><span data-stu-id="1b2ad-108">Properties</span></span>

|<span data-ttu-id="1b2ad-109">名前</span><span class="sxs-lookup"><span data-stu-id="1b2ad-109">Name</span></span> | <span data-ttu-id="1b2ad-110">説明</span><span class="sxs-lookup"><span data-stu-id="1b2ad-110">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="1b2ad-111">Id</span><span class="sxs-lookup"><span data-stu-id="1b2ad-111">Id</span></span> |<span data-ttu-id="1b2ad-112">このユーザー通知に対して指定された一意の id を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-112">Gets the developer specified unique id for this user notification.</span></span>|
|   <span data-ttu-id="1b2ad-113">GroupId</span><span class="sxs-lookup"><span data-stu-id="1b2ad-113">GroupId</span></span> |<span data-ttu-id="1b2ad-114">このユーザー通知の開発者が指定したグループ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-114">Gets the developer specified group id for this user notification.</span></span>| 
|   <span data-ttu-id="1b2ad-115">ExpirationTime</span><span class="sxs-lookup"><span data-stu-id="1b2ad-115">ExpirationTime</span></span> |<span data-ttu-id="1b2ad-116">このユーザー通知の有効期限を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-116">Gets the expiration time for this user notification.</span></span>| 
|   <span data-ttu-id="1b2ad-117">[Priority]</span><span class="sxs-lookup"><span data-stu-id="1b2ad-117">Priority</span></span>|<span data-ttu-id="1b2ad-118">このユーザー通知に対して指定された開発者の優先順位を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-118">Gets the developer specified priority for this user notification.</span></span>| 
|   <span data-ttu-id="1b2ad-119">Content</span><span class="sxs-lookup"><span data-stu-id="1b2ad-119">Content</span></span>|<span data-ttu-id="1b2ad-120">この通知のコンテンツペイロードを取得します。これは、開発者が任意のデータを定義したものです。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-120">Gets the content payload for this notification which is developer defined arbitrary data.</span></span>| 
|   <span data-ttu-id="1b2ad-121">ReadState</span><span class="sxs-lookup"><span data-stu-id="1b2ad-121">ReadState</span></span>|<span data-ttu-id="1b2ad-122">通知が開封されたか未読であることを示す、このユーザー通知の読み取り状態の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-122">Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>| 
|   <span data-ttu-id="1b2ad-123">UserActionState</span><span class="sxs-lookup"><span data-stu-id="1b2ad-123">UserActionState</span></span>|<span data-ttu-id="1b2ad-124">通知が対話、破棄、アクティブ化、または再通知されていないかどうかを判断するユーザー通知のユーザー操作状態の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-124">Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span>| 


## <a name="methods"></a><span data-ttu-id="1b2ad-125">メソッド</span><span class="sxs-lookup"><span data-stu-id="1b2ad-125">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="1b2ad-126">SaveAsync ()</span><span class="sxs-lookup"><span data-stu-id="1b2ad-126">SaveAsync()</span></span> 
<span data-ttu-id="1b2ad-127">これは、ユーザー通知の変更を発行するときに呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-127">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="1b2ad-128">アプリケーションが UserNotification の更新可能なプロパティを変更するたびに、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="1b2ad-128">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>
```C#
public IAsyncOperation SaveAsync()
```

