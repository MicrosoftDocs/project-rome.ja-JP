---
title: MCDConnectedDevicesNotificationRegistrationState
description: クラウドの登録の状態を通信するために使用される値。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909234"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a><span data-ttu-id="752eb-104">クラス `MCDConnectedDevicesNotificationRegistrationState`</span><span class="sxs-lookup"><span data-stu-id="752eb-104">class `MCDConnectedDevicesNotificationRegistrationState`</span></span> 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
<span data-ttu-id="752eb-105">クラウドの登録の状態を通信するために使用される値。</span><span class="sxs-lookup"><span data-stu-id="752eb-105">Values used to communicate the status of cloud registration.</span></span>

## <a name="fields"></a><span data-ttu-id="752eb-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="752eb-106">Fields</span></span>

| <span data-ttu-id="752eb-107">名前</span><span class="sxs-lookup"><span data-stu-id="752eb-107">Name</span></span>                              |   <span data-ttu-id="752eb-108">値</span><span class="sxs-lookup"><span data-stu-id="752eb-108">Value</span></span>     | <span data-ttu-id="752eb-109">説明</span><span class="sxs-lookup"><span data-stu-id="752eb-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="752eb-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span><span class="sxs-lookup"><span data-stu-id="752eb-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span></span> | <span data-ttu-id="752eb-111">0</span><span class="sxs-lookup"><span data-stu-id="752eb-111">0</span></span> | <span data-ttu-id="752eb-112">登録が開始されていることはありません。</span><span class="sxs-lookup"><span data-stu-id="752eb-112">Registration has never been started.</span></span>
| <span data-ttu-id="752eb-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span><span class="sxs-lookup"><span data-stu-id="752eb-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span></span> | <span data-ttu-id="752eb-114">1</span><span class="sxs-lookup"><span data-stu-id="752eb-114">1</span></span> | <span data-ttu-id="752eb-115">登録が完了しました。</span><span class="sxs-lookup"><span data-stu-id="752eb-115">Registration has finished.</span></span> |
| <span data-ttu-id="752eb-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span><span class="sxs-lookup"><span data-stu-id="752eb-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span></span> | <span data-ttu-id="752eb-117">2</span><span class="sxs-lookup"><span data-stu-id="752eb-117">2</span></span> | <span data-ttu-id="752eb-118">登録の有効期限が近づいてし、そのため、アプリが必要があります登録をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="752eb-118">Registration is about to expire and so the app should perform registration again.</span></span> |
| <span data-ttu-id="752eb-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span><span class="sxs-lookup"><span data-stu-id="752eb-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span></span> | <span data-ttu-id="752eb-120">3</span><span class="sxs-lookup"><span data-stu-id="752eb-120">3</span></span> | <span data-ttu-id="752eb-121">登録の有効期限が切れており、そのため、アプリが必要がありますの登録をもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="752eb-121">Registration has expired and so the app must perform registration again.</span></span> |