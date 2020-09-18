---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: MCDConnectedDevicesNotificationRegistrationStatus クラスについて説明します。 これらの値は、クラウド登録の状態を伝えるために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: a7dd06a4593203f60275a540702ccfc164aa6b59
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761106"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a><span data-ttu-id="3d7ac-105">講義 `MCDConnectedDevicesNotificationRegistrationStatus`</span><span class="sxs-lookup"><span data-stu-id="3d7ac-105">class `MCDConnectedDevicesNotificationRegistrationStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
<span data-ttu-id="3d7ac-106">登録操作の状態を示す列挙です。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-106">Enumeration indicating the status of the registration operation.</span></span>
<span data-ttu-id="3d7ac-107">エラー状態は、アプリ開発者が登録を再試行する可能性がある一時的な状態を示します。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-107">The error statuses indicate transient conditions where the app developer may want to retry registration.</span></span>

## <a name="fields"></a><span data-ttu-id="3d7ac-108">フィールド</span><span class="sxs-lookup"><span data-stu-id="3d7ac-108">Fields</span></span>

| <span data-ttu-id="3d7ac-109">名前</span><span class="sxs-lookup"><span data-stu-id="3d7ac-109">Name</span></span>                              |   <span data-ttu-id="3d7ac-110">[値]</span><span class="sxs-lookup"><span data-stu-id="3d7ac-110">Value</span></span>     | <span data-ttu-id="3d7ac-111">説明</span><span class="sxs-lookup"><span data-stu-id="3d7ac-111">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="3d7ac-112">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="3d7ac-112">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span></span> | <span data-ttu-id="3d7ac-113">0</span><span class="sxs-lookup"><span data-stu-id="3d7ac-113">0</span></span> | <span data-ttu-id="3d7ac-114">操作は正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-114">Operation completed successfully.</span></span>
| <span data-ttu-id="3d7ac-115">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="3d7ac-115">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span></span> | <span data-ttu-id="3d7ac-116">1</span><span class="sxs-lookup"><span data-stu-id="3d7ac-116">1</span></span> | <span data-ttu-id="3d7ac-117">ネットワークが使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-117">Network was unavailable.</span></span> |
| <span data-ttu-id="3d7ac-118">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span><span class="sxs-lookup"><span data-stu-id="3d7ac-118">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span></span> | <span data-ttu-id="3d7ac-119">2</span><span class="sxs-lookup"><span data-stu-id="3d7ac-119">2</span></span> | <span data-ttu-id="3d7ac-120">Web サービスが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-120">A web service failed.</span></span> |
| <span data-ttu-id="3d7ac-121">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="3d7ac-121">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="3d7ac-122">3</span><span class="sxs-lookup"><span data-stu-id="3d7ac-122">3</span></span> | <span data-ttu-id="3d7ac-123">トークン要求サブスクライバーが応答しませんでした。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-123">No token request subscribers responded.</span></span> |
| <span data-ttu-id="3d7ac-124">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="3d7ac-124">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="3d7ac-125">4</span><span class="sxs-lookup"><span data-stu-id="3d7ac-125">4</span></span> | <span data-ttu-id="3d7ac-126">トークン要求が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-126">The token request failed.</span></span> |
| <span data-ttu-id="3d7ac-127">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span><span class="sxs-lookup"><span data-stu-id="3d7ac-127">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span></span> | <span data-ttu-id="3d7ac-128">5</span><span class="sxs-lookup"><span data-stu-id="3d7ac-128">5</span></span> | <span data-ttu-id="3d7ac-129">情報を登録するためのアカウントが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-129">Account to register information for was not found.</span></span> |
| <span data-ttu-id="3d7ac-130">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="3d7ac-130">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span></span> | <span data-ttu-id="3d7ac-131">6</span><span class="sxs-lookup"><span data-stu-id="3d7ac-131">6</span></span> | <span data-ttu-id="3d7ac-132">操作で不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3d7ac-132">Operation encountered an unknown error.</span></span> |