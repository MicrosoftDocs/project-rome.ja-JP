---
title: MCDConnectedDevicesNotificationRegistrationState
description: MCDConnectedDevicesNotificationRegistrationState クラスについて説明します。 これらの値は、クラウド登録の状態を伝えるために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 8b69443b53532280df3deeef51025f18e70fecac
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761116"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a><span data-ttu-id="4342f-105">講義 `MCDConnectedDevicesNotificationRegistrationState`</span><span class="sxs-lookup"><span data-stu-id="4342f-105">class `MCDConnectedDevicesNotificationRegistrationState`</span></span> 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
<span data-ttu-id="4342f-106">クラウド登録の状態を伝えるために使用される値。</span><span class="sxs-lookup"><span data-stu-id="4342f-106">Values used to communicate the status of cloud registration.</span></span>

## <a name="fields"></a><span data-ttu-id="4342f-107">フィールド</span><span class="sxs-lookup"><span data-stu-id="4342f-107">Fields</span></span>

| <span data-ttu-id="4342f-108">名前</span><span class="sxs-lookup"><span data-stu-id="4342f-108">Name</span></span>                              |   <span data-ttu-id="4342f-109">[値]</span><span class="sxs-lookup"><span data-stu-id="4342f-109">Value</span></span>     | <span data-ttu-id="4342f-110">説明</span><span class="sxs-lookup"><span data-stu-id="4342f-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="4342f-111">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span><span class="sxs-lookup"><span data-stu-id="4342f-111">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span></span> | <span data-ttu-id="4342f-112">0</span><span class="sxs-lookup"><span data-stu-id="4342f-112">0</span></span> | <span data-ttu-id="4342f-113">登録が開始されていません。</span><span class="sxs-lookup"><span data-stu-id="4342f-113">Registration has never been started.</span></span>
| <span data-ttu-id="4342f-114">MCDConnectedDevicesNotificationRegistrationStateRegistered</span><span class="sxs-lookup"><span data-stu-id="4342f-114">MCDConnectedDevicesNotificationRegistrationStateRegistered</span></span> | <span data-ttu-id="4342f-115">1</span><span class="sxs-lookup"><span data-stu-id="4342f-115">1</span></span> | <span data-ttu-id="4342f-116">登録が完了しました。</span><span class="sxs-lookup"><span data-stu-id="4342f-116">Registration has finished.</span></span> |
| <span data-ttu-id="4342f-117">MCDConnectedDevicesNotificationRegistrationStateExpiring</span><span class="sxs-lookup"><span data-stu-id="4342f-117">MCDConnectedDevicesNotificationRegistrationStateExpiring</span></span> | <span data-ttu-id="4342f-118">2</span><span class="sxs-lookup"><span data-stu-id="4342f-118">2</span></span> | <span data-ttu-id="4342f-119">登録の有効期限が間もなく切れます。アプリで登録を再度実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4342f-119">Registration is about to expire and so the app should perform registration again.</span></span> |
| <span data-ttu-id="4342f-120">MCDConnectedDevicesNotificationRegistrationStateExpired</span><span class="sxs-lookup"><span data-stu-id="4342f-120">MCDConnectedDevicesNotificationRegistrationStateExpired</span></span> | <span data-ttu-id="4342f-121">3</span><span class="sxs-lookup"><span data-stu-id="4342f-121">3</span></span> | <span data-ttu-id="4342f-122">登録の有効期限が切れているため、アプリで登録を再度実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4342f-122">Registration has expired and so the app must perform registration again.</span></span> |