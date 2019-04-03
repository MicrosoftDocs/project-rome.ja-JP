---
title: MCDUserActivitySession
description: このクラスは、ユーザー アクティビティの追跡 ([MCDUserActivity](MCDUserActivity.md)インスタンス)、ユーザーはそのアクティビティに関与して中にします。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 2ae85e637bb059e811a60e5bde5f33ea767c8314
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909634"
---
# <a name="class-mcduseractivitysession"></a><span data-ttu-id="2a0de-104">クラス `MCDUserActivitySession`</span><span class="sxs-lookup"><span data-stu-id="2a0de-104">class `MCDUserActivitySession`</span></span>

```
@interface MCDUserActivitySession : NSObject
```

<span data-ttu-id="2a0de-105">このクラスは、指定したユーザー アクティビティのエンゲージメントを追跡します ([MCDUserActivity](MCDUserActivity.md)インスタンス)。</span><span class="sxs-lookup"><span data-stu-id="2a0de-105">This class tracks engagement for a specified user activity ([MCDUserActivity](MCDUserActivity.md) instance).</span></span>

<span data-ttu-id="2a0de-106">A [MCDUserActivity](MCDUserActivity.md)はどのくらいの期間、ユーザーが進行中でそのアクティビティを追跡する、MCDUserActivitySession 関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="2a0de-106">A [MCDUserActivity](MCDUserActivity.md) is associated with an MCDUserActivitySession which tracks how long the user is engaged in that activity.</span></span> <span data-ttu-id="2a0de-107">たとえば、映画を見てなど、アクティビティに複数の曜日の過程でオン-と-オフ発生します。</span><span class="sxs-lookup"><span data-stu-id="2a0de-107">For example, an activity such as watching a movie can occur on-and-off over the course of multiple days.</span></span> <span data-ttu-id="2a0de-108">ユーザーは、最初の映画を見て、新しいアクティビティを起動するときに、MCDUserActivitySession を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a0de-108">When the user first starts the new activity of watching a movie, a MCDUserActivitySession must be created.</span></span> <span data-ttu-id="2a0de-109">ユーザーが別のアクティビティに切り替えたときに破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a0de-109">It should be disposed when the user switches to a different activity.</span></span> <span data-ttu-id="2a0de-110">アプリが別作成、ユーザーの再開時**MCDUserActivitySession** 、元の[MCDUserActivity](MCDUserActivity.md)ユーザーがビデオを視聴している限り、アクティビティを追跡するためにします。</span><span class="sxs-lookup"><span data-stu-id="2a0de-110">When the user resumes, the app should create another **MCDUserActivitySession** from the original [MCDUserActivity](MCDUserActivity.md) to track the activity as long as the user is watching the movie.</span></span>


## <a name="properties"></a><span data-ttu-id="2a0de-111">プロパティ</span><span class="sxs-lookup"><span data-stu-id="2a0de-111">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="2a0de-112">ActivityId</span><span class="sxs-lookup"><span data-stu-id="2a0de-112">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="2a0de-113">関連付けられたこの MCDUserActivitySession MCDUserActivity の一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2a0de-113">A unique ID for the MCDUserActivity associated with this MCDUserActivitySession.</span></span>

## <a name="methods"></a><span data-ttu-id="2a0de-114">メソッド</span><span class="sxs-lookup"><span data-stu-id="2a0de-114">Methods</span></span>

### <a name="stop"></a><span data-ttu-id="2a0de-115">stop</span><span class="sxs-lookup"><span data-stu-id="2a0de-115">stop</span></span>
`- (void)stop;`

<span data-ttu-id="2a0de-116">このアクティビティのセッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="2a0de-116">Stops this activity session.</span></span> <span data-ttu-id="2a0de-117">これは、ユーザーが不要になったこのセッションに関連付けられたアクティビティに関与している場合に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a0de-117">This should be called when the user is no longer engaged in the activity associated with this session.</span></span>