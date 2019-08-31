---
title: UserNotificationReaderOptions
description: このクラスを使用すると、アプリで通知リーダーにオプションを提供できるようになります。たとえば、新しいユーザー通知を受信するだけで、既存の通知を更新することはできません。
keywords: microsoft、windows、Graph 通知、操作方法ウィンドウ
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801384"
---
# <a name="class-usernotificationreaderoptions"></a><span data-ttu-id="cff95-104">講義`UserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="cff95-104">class `UserNotificationReaderOptions`</span></span>

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

<span data-ttu-id="cff95-105">このクラスを使用すると、アプリで通知リーダーにオプションを提供できるようになります。たとえば、新しいユーザー通知を受信するだけで、既存の通知を更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="cff95-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="constructors"></a><span data-ttu-id="cff95-106">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="cff95-106">Constructors</span></span>

### <a name="usernotificationreaderoptions"></a><span data-ttu-id="cff95-107">UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="cff95-107">UserNotificationReaderOptions</span></span>
<span data-ttu-id="cff95-108">UserNotificationReaderOptions の新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="cff95-108">Creates and initializes a new instance of UserNotificationReaderOptions.</span></span>

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a><span data-ttu-id="cff95-109">UserNotificationReaderOptions (UserNotificationReaderStartPosition、Usernotificationreaderoptions、UserNotificationReadStateFilter、UserNotificationUserActionStateFilter)</span><span class="sxs-lookup"><span data-stu-id="cff95-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span></span>
<span data-ttu-id="cff95-110">フィルターと開始位置を指定して UserNotificationReaderOptions の新しいインスタンスを作成し、初期化します。</span><span class="sxs-lookup"><span data-stu-id="cff95-110">Creates and initializes a new instance of UserNotificationReaderOptions with filters and start position specified.</span></span> 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a><span data-ttu-id="cff95-111">Properties</span><span class="sxs-lookup"><span data-stu-id="cff95-111">Properties</span></span>

|<span data-ttu-id="cff95-112">名前</span><span class="sxs-lookup"><span data-stu-id="cff95-112">Name</span></span> | <span data-ttu-id="cff95-113">説明</span><span class="sxs-lookup"><span data-stu-id="cff95-113">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="cff95-114">開始位置</span><span class="sxs-lookup"><span data-stu-id="cff95-114">StartPosition</span></span> |<span data-ttu-id="cff95-115">UserNotificationReaderOptions のこのインスタンスの開始位置を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="cff95-115">Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>|
|   <span data-ttu-id="cff95-116">StatusFilter</span><span class="sxs-lookup"><span data-stu-id="cff95-116">StatusFilter</span></span> |<span data-ttu-id="cff95-117">作成するユーザー通知リーダーのステータスフィルターを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="cff95-117">Get or set the status filter for this user notification reader you desire to create.</span></span>| 
|   <span data-ttu-id="cff95-118">ReadStateFilter</span><span class="sxs-lookup"><span data-stu-id="cff95-118">ReadStateFilter</span></span> |<span data-ttu-id="cff95-119">UserNotificationReaderOptions のこのインスタンスに設定されている読み取り状態フィルターを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="cff95-119">Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 
|   <span data-ttu-id="cff95-120">UserActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="cff95-120">UserActionStateFilter</span></span>|<span data-ttu-id="cff95-121">この UserNotificationReaderOptions のインスタンスに設定されているユーザーアクション状態フィルターを getor に設定します。</span><span class="sxs-lookup"><span data-stu-id="cff95-121">Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 




