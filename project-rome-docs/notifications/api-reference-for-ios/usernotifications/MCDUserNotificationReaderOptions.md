---
title: MCDUserNotificationReaderOptions
description: このクラスを使用すると、アプリで通知リーダーにオプションを提供できるようになります。たとえば、新しいユーザー通知を受信するだけで、既存の通知を更新することはできません。
keywords: microsoft、windows、Graph 通知、操作方法 iOS、操作方法 iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907984"
---
# <a name="class-mcdusernotificationreaderoptions"></a><span data-ttu-id="367c5-104">講義`MCDUserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="367c5-104">class `MCDUserNotificationReaderOptions`</span></span>

```
@interface MCDUserNotificationReaderOptions : NSObject
```

<span data-ttu-id="367c5-105">このクラスを使用すると、アプリで通知リーダーにオプションを提供できるようになります。たとえば、新しいユーザー通知を受信するだけで、既存の通知を更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="367c5-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="properties"></a><span data-ttu-id="367c5-106">Properties</span><span class="sxs-lookup"><span data-stu-id="367c5-106">Properties</span></span>

### <a name="startposition"></a><span data-ttu-id="367c5-107">開始位置</span><span class="sxs-lookup"><span data-stu-id="367c5-107">startPosition</span></span>
<span data-ttu-id="367c5-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;`UserNotificationReaderOptions のこのインスタンスの開始位置を取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="367c5-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>

### <a name="statusfilter"></a><span data-ttu-id="367c5-109">statusFilter</span><span class="sxs-lookup"><span data-stu-id="367c5-109">statusFilter</span></span>
<span data-ttu-id="367c5-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;`作成するユーザー通知リーダーのステータスフィルターを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="367c5-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` Get or set the status filter for this user notification reader you desire to create.</span></span>

### <a name="readstatefilter"></a><span data-ttu-id="367c5-111">readStateFilter</span><span class="sxs-lookup"><span data-stu-id="367c5-111">readStateFilter</span></span>
<span data-ttu-id="367c5-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;`UserNotificationReaderOptions のこのインスタンスに設定されている読み取り状態フィルターを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="367c5-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions</span></span>

### <a name="useractionstatefilter"></a><span data-ttu-id="367c5-113">userActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="367c5-113">userActionStateFilter</span></span>
<span data-ttu-id="367c5-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;`この UserNotificationReaderOptions のインスタンスに設定されているユーザーアクション状態フィルターを getor に設定します。</span><span class="sxs-lookup"><span data-stu-id="367c5-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>

## <a name="constructors"></a><span data-ttu-id="367c5-115">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="367c5-115">Constructors</span></span>

### <a name="options"></a><span data-ttu-id="367c5-116">options</span><span class="sxs-lookup"><span data-stu-id="367c5-116">options</span></span>
<span data-ttu-id="367c5-117">`+ (nullable instancetype)options;`ユーザー通知のオプションの新しいインスタンスを作成して初期化します。</span><span class="sxs-lookup"><span data-stu-id="367c5-117">`+ (nullable instancetype)options;` Creates and initializes a new instance of options for User Notifications.</span></span>