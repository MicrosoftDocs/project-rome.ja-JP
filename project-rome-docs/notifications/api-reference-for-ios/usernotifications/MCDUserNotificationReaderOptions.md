---
title: MCDUserNotificationReaderOptions
description: このクラスは、新しいユーザー通知と既存の通知の更新プログラムを受け取るだけなど、通知リーダーでオプションを提供するアプリを使用できます。
keywords: microsoft、windows、グラフの通知、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907984"
---
# <a name="class-mcdusernotificationreaderoptions"></a><span data-ttu-id="a639a-104">クラス `MCDUserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="a639a-104">class `MCDUserNotificationReaderOptions`</span></span>

```
@interface MCDUserNotificationReaderOptions : NSObject
```

<span data-ttu-id="a639a-105">このクラスは、新しいユーザー通知と既存の通知の更新プログラムを受け取るだけなど、通知リーダーでオプションを提供するアプリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a639a-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="properties"></a><span data-ttu-id="a639a-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a639a-106">Properties</span></span>

### <a name="startposition"></a><span data-ttu-id="a639a-107">位置</span><span class="sxs-lookup"><span data-stu-id="a639a-107">startPosition</span></span>
<span data-ttu-id="a639a-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` 取得または UserNotificationReaderOptions のこのインスタンスの開始位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="a639a-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>

### <a name="statusfilter"></a><span data-ttu-id="a639a-109">StatusFilter</span><span class="sxs-lookup"><span data-stu-id="a639a-109">statusFilter</span></span>
<span data-ttu-id="a639a-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` 取得または作成をご希望のこのユーザー通知のリーダーの状態フィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="a639a-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` Get or set the status filter for this user notification reader you desire to create.</span></span>

### <a name="readstatefilter"></a><span data-ttu-id="a639a-111">ReadStateFilter</span><span class="sxs-lookup"><span data-stu-id="a639a-111">readStateFilter</span></span>
<span data-ttu-id="a639a-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` 取得または設定 UserNotificationReaderOptions のこのインスタンスに設定されている読み取り状態フィルター</span><span class="sxs-lookup"><span data-stu-id="a639a-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions</span></span>

### <a name="useractionstatefilter"></a><span data-ttu-id="a639a-113">userActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="a639a-113">userActionStateFilter</span></span>
<span data-ttu-id="a639a-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` Getor は、UserNotificationReaderOptions のこのインスタンスに設定されているユーザーの操作状態のフィルターを設定します。</span><span class="sxs-lookup"><span data-stu-id="a639a-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>

## <a name="constructors"></a><span data-ttu-id="a639a-115">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="a639a-115">Constructors</span></span>

### <a name="options"></a><span data-ttu-id="a639a-116">オプション</span><span class="sxs-lookup"><span data-stu-id="a639a-116">options</span></span>
<span data-ttu-id="a639a-117">`+ (nullable instancetype)options;` 作成し、ユーザーへの通知のオプションの新しいインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="a639a-117">`+ (nullable instancetype)options;` Creates and initializes a new instance of options for User Notifications.</span></span>