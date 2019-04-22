---
title: MCDConnectedDevicesNotificationType
description: 通知の種類 (サービス) を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: eb537450a9e8a970bd07652fe201e94071211d92
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801694"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a><span data-ttu-id="3934f-104">列挙型 `MCDConnectedDevicesNotificationType`</span><span class="sxs-lookup"><span data-stu-id="3934f-104">enum `MCDConnectedDevicesNotificationType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
<span data-ttu-id="3934f-105">通知の種類 (サービス) を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3934f-105">Contains values that describe the type (service) of a notification.</span></span>

## <a name="fields"></a><span data-ttu-id="3934f-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="3934f-106">Fields</span></span>

| <span data-ttu-id="3934f-107">名前</span><span class="sxs-lookup"><span data-stu-id="3934f-107">Name</span></span>                              |   <span data-ttu-id="3934f-108">値</span><span class="sxs-lookup"><span data-stu-id="3934f-108">Value</span></span>     | <span data-ttu-id="3934f-109">説明</span><span class="sxs-lookup"><span data-stu-id="3934f-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="3934f-110">MCDNotificationTypeUnknown</span><span class="sxs-lookup"><span data-stu-id="3934f-110">MCDNotificationTypeUnknown</span></span> | <span data-ttu-id="3934f-111">0</span><span class="sxs-lookup"><span data-stu-id="3934f-111">0</span></span> | <span data-ttu-id="3934f-112">ConnectedDevicesNotificationType が不明です。</span><span class="sxs-lookup"><span data-stu-id="3934f-112">ConnectedDevicesNotificationType is unknown.</span></span> |
| <span data-ttu-id="3934f-113">MCDNotificationTypeWNS</span><span class="sxs-lookup"><span data-stu-id="3934f-113">MCDNotificationTypeWNS</span></span> | <span data-ttu-id="3934f-114">1</span><span class="sxs-lookup"><span data-stu-id="3934f-114">1</span></span> | <span data-ttu-id="3934f-115">Windows プッシュ通知サービス。</span><span class="sxs-lookup"><span data-stu-id="3934f-115">Windows Push Notification Services.</span></span> |
| <span data-ttu-id="3934f-116">MCDNotificationTypeGCM</span><span class="sxs-lookup"><span data-stu-id="3934f-116">MCDNotificationTypeGCM</span></span> | <span data-ttu-id="3934f-117">2</span><span class="sxs-lookup"><span data-stu-id="3934f-117">2</span></span> | <span data-ttu-id="3934f-118">Google のクラウド メッセージングします。</span><span class="sxs-lookup"><span data-stu-id="3934f-118">Google Cloud Messaging.</span></span> |
| <span data-ttu-id="3934f-119">MCDNotificationTypeFCM</span><span class="sxs-lookup"><span data-stu-id="3934f-119">MCDNotificationTypeFCM</span></span> | <span data-ttu-id="3934f-120">3</span><span class="sxs-lookup"><span data-stu-id="3934f-120">3</span></span> | <span data-ttu-id="3934f-121">Firebase クラウド メッセージングのします。</span><span class="sxs-lookup"><span data-stu-id="3934f-121">Firebase Cloud Messaging.</span></span>|
| <span data-ttu-id="3934f-122">MCDNotificationTypeAPN</span><span class="sxs-lookup"><span data-stu-id="3934f-122">MCDNotificationTypeAPN</span></span> | <span data-ttu-id="3934f-123">4</span><span class="sxs-lookup"><span data-stu-id="3934f-123">4</span></span> | <span data-ttu-id="3934f-124">Apple Push Notification Service。</span><span class="sxs-lookup"><span data-stu-id="3934f-124">Apple Push Notification Service.</span></span> |
| <span data-ttu-id="3934f-125">MCDNotificationTypePolling</span><span class="sxs-lookup"><span data-stu-id="3934f-125">MCDNotificationTypePolling</span></span> | <span data-ttu-id="3934f-126">5</span><span class="sxs-lookup"><span data-stu-id="3934f-126">5</span></span> | <span data-ttu-id="3934f-127">クラウド通知サービス。受信応答の代わりにポーリングします。</span><span class="sxs-lookup"><span data-stu-id="3934f-127">No cloud notification service; instead poll for incoming responses.</span></span> |
