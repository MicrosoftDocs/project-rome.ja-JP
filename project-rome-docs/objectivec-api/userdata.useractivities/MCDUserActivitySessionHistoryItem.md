---
title: MCDUserActivitySessionHistoryItem
description: このクラスは、特定の活動に従事するユーザーが開始および終了の時間を提供します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 3a480d9d0d028973554c13ee162b359502c8a772
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801634"
---
# <a name="class-mcduseractivitysessionhistoryitem"></a><span data-ttu-id="861e1-104">クラス `MCDUserActivitySessionHistoryItem`</span><span class="sxs-lookup"><span data-stu-id="861e1-104">class `MCDUserActivitySessionHistoryItem`</span></span>

```
@interface MCDUserActivitySessionHistoryItem : NSObject
```

<span data-ttu-id="861e1-105">このクラスは、特定の活動に従事するユーザーが開始および終了の時間を提供します。</span><span class="sxs-lookup"><span data-stu-id="861e1-105">This class provides the start and end time that a user was engaged in a particular activity.</span></span>


## <a name="properties"></a><span data-ttu-id="861e1-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="861e1-106">Properties</span></span>

### <a name="useractivity"></a><span data-ttu-id="861e1-107">UserActivity</span><span class="sxs-lookup"><span data-stu-id="861e1-107">userActivity</span></span>
`@property(nonatomic, readonly, nonnull) MCDUserActivity* userActivity;`

<span data-ttu-id="861e1-108">ユーザー アクティビティの履歴がこのクラスのインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="861e1-108">The user activity whose history this class instance represents.</span></span>

### <a name="starttime"></a><span data-ttu-id="861e1-109">startTime</span><span class="sxs-lookup"><span data-stu-id="861e1-109">startTime</span></span>
`@property(nonatomic, readonly, nonnull) NSDate* startTime;`

<span data-ttu-id="861e1-110">ユーザーの関連付けられているアクティビティで魅力的な開始時刻。</span><span class="sxs-lookup"><span data-stu-id="861e1-110">The time when the user started engaging in the associated activity.</span></span>

### <a name="endtime"></a><span data-ttu-id="861e1-111">終了時刻</span><span class="sxs-lookup"><span data-stu-id="861e1-111">endTime</span></span>
`@property(nonatomic, readonly, nullable) NSDate* endTime;`

<span data-ttu-id="861e1-112">ユーザーが関連付けられているアクティビティで停止したときに時間です。</span><span class="sxs-lookup"><span data-stu-id="861e1-112">The time when the user stopped engaging in the associated activity.</span></span>

### <a name="remotesystemid"></a><span data-ttu-id="861e1-113">remoteSystemId</span><span class="sxs-lookup"><span data-stu-id="861e1-113">remoteSystemId</span></span>
`@property(nonatomic, readonly, nullable) NSString* remoteSystemId;`

<span data-ttu-id="861e1-114">ユーザー デバイスのリモート システム id を示す文字列でこの活動を行っています。</span><span class="sxs-lookup"><span data-stu-id="861e1-114">The string indicating the remote system id of the device the user engaged this activity on.</span></span>