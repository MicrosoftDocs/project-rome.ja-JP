---
title: UserNotificationReaderOptions
description: このクラスは、新しいユーザー通知と既存の通知の更新プログラムを受け取るだけなど、通知リーダーでオプションを提供するアプリを使用できます。
keywords: microsoft、windows、グラフの通知、Windows の操作方法
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909684"
---
# <a name="class-usernotificationreaderoptions"></a><span data-ttu-id="12690-104">クラス `UserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="12690-104">class `UserNotificationReaderOptions`</span></span>

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

<span data-ttu-id="12690-105">このクラスは、新しいユーザー通知と既存の通知の更新プログラムを受け取るだけなど、通知リーダーでオプションを提供するアプリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="12690-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="constructors"></a><span data-ttu-id="12690-106">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="12690-106">Constructors</span></span>

### <a name="usernotificationreaderoptions"></a><span data-ttu-id="12690-107">UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="12690-107">UserNotificationReaderOptions</span></span>
<span data-ttu-id="12690-108">作成し、UserNotificationReaderOptions の新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="12690-108">Creates and initializes a new instance of UserNotificationReaderOptions.</span></span>

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a><span data-ttu-id="12690-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span><span class="sxs-lookup"><span data-stu-id="12690-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span></span>
<span data-ttu-id="12690-110">作成し、開始位置が指定されたフィルターと UserNotificationReaderOptions の新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="12690-110">Creates and initializes a new instance of UserNotificationReaderOptions with filters and start position specified.</span></span> 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a><span data-ttu-id="12690-111">プロパティ</span><span class="sxs-lookup"><span data-stu-id="12690-111">Properties</span></span>

|<span data-ttu-id="12690-112">名前</span><span class="sxs-lookup"><span data-stu-id="12690-112">Name</span></span> | <span data-ttu-id="12690-113">説明</span><span class="sxs-lookup"><span data-stu-id="12690-113">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="12690-114">位置</span><span class="sxs-lookup"><span data-stu-id="12690-114">StartPosition</span></span> |<span data-ttu-id="12690-115">取得または UserNotificationReaderOptions のこのインスタンスの開始位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="12690-115">Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>|
|   <span data-ttu-id="12690-116">StatusFilter</span><span class="sxs-lookup"><span data-stu-id="12690-116">StatusFilter</span></span> |<span data-ttu-id="12690-117">取得または作成をご希望のこのユーザー通知のリーダーの状態フィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="12690-117">Get or set the status filter for this user notification reader you desire to create.</span></span>| 
|   <span data-ttu-id="12690-118">ReadStateFilter</span><span class="sxs-lookup"><span data-stu-id="12690-118">ReadStateFilter</span></span> |<span data-ttu-id="12690-119">取得または UserNotificationReaderOptions のこのインスタンスに設定されている読み取り状態フィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="12690-119">Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 
|   <span data-ttu-id="12690-120">UserActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="12690-120">UserActionStateFilter</span></span>|<span data-ttu-id="12690-121">Getor は、UserNotificationReaderOptions のこのインスタンスに設定されているユーザーの操作状態のフィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="12690-121">Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 




