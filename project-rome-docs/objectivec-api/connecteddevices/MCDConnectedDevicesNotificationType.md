---
title: MCDConnectedDevicesNotificationType
description: 通知の種類 (サービス) を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: eb537450a9e8a970bd07652fe201e94071211d92
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909484"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a><span data-ttu-id="f639d-104">列挙型 `MCDConnectedDevicesNotificationType`</span><span class="sxs-lookup"><span data-stu-id="f639d-104">enum `MCDConnectedDevicesNotificationType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
<span data-ttu-id="f639d-105">通知の種類 (サービス) を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f639d-105">Contains values that describe the type (service) of a notification.</span></span>

## <a name="fields"></a><span data-ttu-id="f639d-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="f639d-106">Fields</span></span>

| <span data-ttu-id="f639d-107">名前</span><span class="sxs-lookup"><span data-stu-id="f639d-107">Name</span></span>                              |   <span data-ttu-id="f639d-108">値</span><span class="sxs-lookup"><span data-stu-id="f639d-108">Value</span></span>     | <span data-ttu-id="f639d-109">説明</span><span class="sxs-lookup"><span data-stu-id="f639d-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="f639d-110">MCDNotificationTypeUnknown</span><span class="sxs-lookup"><span data-stu-id="f639d-110">MCDNotificationTypeUnknown</span></span> | <span data-ttu-id="f639d-111">0</span><span class="sxs-lookup"><span data-stu-id="f639d-111">0</span></span> | <span data-ttu-id="f639d-112">ConnectedDevicesNotificationType が不明です。</span><span class="sxs-lookup"><span data-stu-id="f639d-112">ConnectedDevicesNotificationType is unknown.</span></span> |
| <span data-ttu-id="f639d-113">MCDNotificationTypeWNS</span><span class="sxs-lookup"><span data-stu-id="f639d-113">MCDNotificationTypeWNS</span></span> | <span data-ttu-id="f639d-114">1</span><span class="sxs-lookup"><span data-stu-id="f639d-114">1</span></span> | <span data-ttu-id="f639d-115">Windows プッシュ通知サービス。</span><span class="sxs-lookup"><span data-stu-id="f639d-115">Windows Push Notification Services.</span></span> |
| <span data-ttu-id="f639d-116">MCDNotificationTypeGCM</span><span class="sxs-lookup"><span data-stu-id="f639d-116">MCDNotificationTypeGCM</span></span> | <span data-ttu-id="f639d-117">2</span><span class="sxs-lookup"><span data-stu-id="f639d-117">2</span></span> | <span data-ttu-id="f639d-118">Google のクラウド メッセージングします。</span><span class="sxs-lookup"><span data-stu-id="f639d-118">Google Cloud Messaging.</span></span> |
| <span data-ttu-id="f639d-119">MCDNotificationTypeFCM</span><span class="sxs-lookup"><span data-stu-id="f639d-119">MCDNotificationTypeFCM</span></span> | <span data-ttu-id="f639d-120">3</span><span class="sxs-lookup"><span data-stu-id="f639d-120">3</span></span> | <span data-ttu-id="f639d-121">Firebase クラウド メッセージングのします。</span><span class="sxs-lookup"><span data-stu-id="f639d-121">Firebase Cloud Messaging.</span></span>|
| <span data-ttu-id="f639d-122">MCDNotificationTypeAPN</span><span class="sxs-lookup"><span data-stu-id="f639d-122">MCDNotificationTypeAPN</span></span> | <span data-ttu-id="f639d-123">4</span><span class="sxs-lookup"><span data-stu-id="f639d-123">4</span></span> | <span data-ttu-id="f639d-124">Apple Push Notification Service。</span><span class="sxs-lookup"><span data-stu-id="f639d-124">Apple Push Notification Service.</span></span> |
| <span data-ttu-id="f639d-125">MCDNotificationTypePolling</span><span class="sxs-lookup"><span data-stu-id="f639d-125">MCDNotificationTypePolling</span></span> | <span data-ttu-id="f639d-126">5</span><span class="sxs-lookup"><span data-stu-id="f639d-126">5</span></span> | <span data-ttu-id="f639d-127">クラウド通知サービス。受信応答の代わりにポーリングします。</span><span class="sxs-lookup"><span data-stu-id="f639d-127">No cloud notification service; instead poll for incoming responses.</span></span> |
