---
title: MCDConnectedDevicesNotificationRegistrationState
description: クラウドの登録の状態を通信するために使用される値。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800714"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a><span data-ttu-id="960cb-104">クラス `MCDConnectedDevicesNotificationRegistrationState`</span><span class="sxs-lookup"><span data-stu-id="960cb-104">class `MCDConnectedDevicesNotificationRegistrationState`</span></span> 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
<span data-ttu-id="960cb-105">クラウドの登録の状態を通信するために使用される値。</span><span class="sxs-lookup"><span data-stu-id="960cb-105">Values used to communicate the status of cloud registration.</span></span>

## <a name="fields"></a><span data-ttu-id="960cb-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="960cb-106">Fields</span></span>

| <span data-ttu-id="960cb-107">名前</span><span class="sxs-lookup"><span data-stu-id="960cb-107">Name</span></span>                              |   <span data-ttu-id="960cb-108">値</span><span class="sxs-lookup"><span data-stu-id="960cb-108">Value</span></span>     | <span data-ttu-id="960cb-109">説明</span><span class="sxs-lookup"><span data-stu-id="960cb-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="960cb-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span><span class="sxs-lookup"><span data-stu-id="960cb-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span></span> | <span data-ttu-id="960cb-111">0</span><span class="sxs-lookup"><span data-stu-id="960cb-111">0</span></span> | <span data-ttu-id="960cb-112">登録が開始されていることはありません。</span><span class="sxs-lookup"><span data-stu-id="960cb-112">Registration has never been started.</span></span>
| <span data-ttu-id="960cb-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span><span class="sxs-lookup"><span data-stu-id="960cb-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span></span> | <span data-ttu-id="960cb-114">1</span><span class="sxs-lookup"><span data-stu-id="960cb-114">1</span></span> | <span data-ttu-id="960cb-115">登録が完了しました。</span><span class="sxs-lookup"><span data-stu-id="960cb-115">Registration has finished.</span></span> |
| <span data-ttu-id="960cb-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span><span class="sxs-lookup"><span data-stu-id="960cb-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span></span> | <span data-ttu-id="960cb-117">2</span><span class="sxs-lookup"><span data-stu-id="960cb-117">2</span></span> | <span data-ttu-id="960cb-118">登録の有効期限が近づいてし、そのため、アプリが必要があります登録をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="960cb-118">Registration is about to expire and so the app should perform registration again.</span></span> |
| <span data-ttu-id="960cb-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span><span class="sxs-lookup"><span data-stu-id="960cb-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span></span> | <span data-ttu-id="960cb-120">3</span><span class="sxs-lookup"><span data-stu-id="960cb-120">3</span></span> | <span data-ttu-id="960cb-121">登録の有効期限が切れており、そのため、アプリが必要がありますの登録をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="960cb-121">Registration has expired and so the app must perform registration again.</span></span> |