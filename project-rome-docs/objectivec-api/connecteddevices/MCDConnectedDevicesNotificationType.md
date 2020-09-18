---
title: MCDConnectedDevicesNotificationType
description: MCDConnectedDevicesNotificationType 列挙型について説明します。 この列挙には、通知の種類 (サービス) を説明する値が含まれます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 5daf6db553df72a14a2cf201b4e974083eb7cf80
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761096"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a><span data-ttu-id="440e5-105">enum `MCDConnectedDevicesNotificationType`</span><span class="sxs-lookup"><span data-stu-id="440e5-105">enum `MCDConnectedDevicesNotificationType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
<span data-ttu-id="440e5-106">通知の種類 (サービス) を説明する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="440e5-106">Contains values that describe the type (service) of a notification.</span></span>

## <a name="fields"></a><span data-ttu-id="440e5-107">フィールド</span><span class="sxs-lookup"><span data-stu-id="440e5-107">Fields</span></span>

| <span data-ttu-id="440e5-108">名前</span><span class="sxs-lookup"><span data-stu-id="440e5-108">Name</span></span>                              |   <span data-ttu-id="440e5-109">[値]</span><span class="sxs-lookup"><span data-stu-id="440e5-109">Value</span></span>     | <span data-ttu-id="440e5-110">説明</span><span class="sxs-lookup"><span data-stu-id="440e5-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="440e5-111">MCDNotificationTypeUnknown</span><span class="sxs-lookup"><span data-stu-id="440e5-111">MCDNotificationTypeUnknown</span></span> | <span data-ttu-id="440e5-112">0</span><span class="sxs-lookup"><span data-stu-id="440e5-112">0</span></span> | <span data-ttu-id="440e5-113">ConnectedDevicesNotificationType は不明です。</span><span class="sxs-lookup"><span data-stu-id="440e5-113">ConnectedDevicesNotificationType is unknown.</span></span> |
| <span data-ttu-id="440e5-114">MCDNotificationTypeWNS</span><span class="sxs-lookup"><span data-stu-id="440e5-114">MCDNotificationTypeWNS</span></span> | <span data-ttu-id="440e5-115">1</span><span class="sxs-lookup"><span data-stu-id="440e5-115">1</span></span> | <span data-ttu-id="440e5-116">Windows プッシュ Notification Services。</span><span class="sxs-lookup"><span data-stu-id="440e5-116">Windows Push Notification Services.</span></span> |
| <span data-ttu-id="440e5-117">MCDNotificationTypeGCM</span><span class="sxs-lookup"><span data-stu-id="440e5-117">MCDNotificationTypeGCM</span></span> | <span data-ttu-id="440e5-118">2</span><span class="sxs-lookup"><span data-stu-id="440e5-118">2</span></span> | <span data-ttu-id="440e5-119">Google Cloud Messaging。</span><span class="sxs-lookup"><span data-stu-id="440e5-119">Google Cloud Messaging.</span></span> |
| <span data-ttu-id="440e5-120">MCDNotificationTypeFCM</span><span class="sxs-lookup"><span data-stu-id="440e5-120">MCDNotificationTypeFCM</span></span> | <span data-ttu-id="440e5-121">3</span><span class="sxs-lookup"><span data-stu-id="440e5-121">3</span></span> | <span data-ttu-id="440e5-122">焼討 base Cloud Messaging。</span><span class="sxs-lookup"><span data-stu-id="440e5-122">Firebase Cloud Messaging.</span></span>|
| <span data-ttu-id="440e5-123">MCDNotificationTypeAPN</span><span class="sxs-lookup"><span data-stu-id="440e5-123">MCDNotificationTypeAPN</span></span> | <span data-ttu-id="440e5-124">4</span><span class="sxs-lookup"><span data-stu-id="440e5-124">4</span></span> | <span data-ttu-id="440e5-125">Apple Push Notification Service。</span><span class="sxs-lookup"><span data-stu-id="440e5-125">Apple Push Notification Service.</span></span> |
| <span data-ttu-id="440e5-126">MCDNotificationTypePolling</span><span class="sxs-lookup"><span data-stu-id="440e5-126">MCDNotificationTypePolling</span></span> | <span data-ttu-id="440e5-127">5</span><span class="sxs-lookup"><span data-stu-id="440e5-127">5</span></span> | <span data-ttu-id="440e5-128">クラウド通知サービスがありません。代わりに、受信した応答をポーリングします。</span><span class="sxs-lookup"><span data-stu-id="440e5-128">No cloud notification service; instead poll for incoming responses.</span></span> |
