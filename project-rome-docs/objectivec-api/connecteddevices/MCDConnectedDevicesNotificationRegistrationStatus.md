---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: クラウドの登録の状態を通信するために使用される値。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: c7d770c73479afb949a4917b5457b12e23b78698
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801364"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a><span data-ttu-id="47565-104">クラス `MCDConnectedDevicesNotificationRegistrationStatus`</span><span class="sxs-lookup"><span data-stu-id="47565-104">class `MCDConnectedDevicesNotificationRegistrationStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
<span data-ttu-id="47565-105">登録操作の状態を示す列挙です。</span><span class="sxs-lookup"><span data-stu-id="47565-105">Enumeration indicating the status of the registration operation.</span></span>
<span data-ttu-id="47565-106">エラー状態では、アプリ開発者の登録を再試行する必要のある一時的な状態を示します。</span><span class="sxs-lookup"><span data-stu-id="47565-106">The error statuses indicate transient conditions where the app developer may want to retry registration.</span></span>

## <a name="fields"></a><span data-ttu-id="47565-107">フィールド</span><span class="sxs-lookup"><span data-stu-id="47565-107">Fields</span></span>

| <span data-ttu-id="47565-108">名前</span><span class="sxs-lookup"><span data-stu-id="47565-108">Name</span></span>                              |   <span data-ttu-id="47565-109">値</span><span class="sxs-lookup"><span data-stu-id="47565-109">Value</span></span>     | <span data-ttu-id="47565-110">説明</span><span class="sxs-lookup"><span data-stu-id="47565-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="47565-111">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="47565-111">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span></span> | <span data-ttu-id="47565-112">0</span><span class="sxs-lookup"><span data-stu-id="47565-112">0</span></span> | <span data-ttu-id="47565-113">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="47565-113">Operation completed successfully.</span></span>
| <span data-ttu-id="47565-114">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="47565-114">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span></span> | <span data-ttu-id="47565-115">1</span><span class="sxs-lookup"><span data-stu-id="47565-115">1</span></span> | <span data-ttu-id="47565-116">ネットワークは使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="47565-116">Network was unavailable.</span></span> |
| <span data-ttu-id="47565-117">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span><span class="sxs-lookup"><span data-stu-id="47565-117">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span></span> | <span data-ttu-id="47565-118">2</span><span class="sxs-lookup"><span data-stu-id="47565-118">2</span></span> | <span data-ttu-id="47565-119">Web サービスが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="47565-119">A web service failed.</span></span> |
| <span data-ttu-id="47565-120">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="47565-120">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="47565-121">3</span><span class="sxs-lookup"><span data-stu-id="47565-121">3</span></span> | <span data-ttu-id="47565-122">トークン要求のサブスクライバーが応答しません。</span><span class="sxs-lookup"><span data-stu-id="47565-122">No token request subscribers responded.</span></span> |
| <span data-ttu-id="47565-123">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="47565-123">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="47565-124">4</span><span class="sxs-lookup"><span data-stu-id="47565-124">4</span></span> | <span data-ttu-id="47565-125">トークンの要求が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="47565-125">The token request failed.</span></span> |
| <span data-ttu-id="47565-126">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span><span class="sxs-lookup"><span data-stu-id="47565-126">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span></span> | <span data-ttu-id="47565-127">5</span><span class="sxs-lookup"><span data-stu-id="47565-127">5</span></span> | <span data-ttu-id="47565-128">情報を登録するアカウントが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="47565-128">Account to register information for was not found.</span></span> |
| <span data-ttu-id="47565-129">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="47565-129">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span></span> | <span data-ttu-id="47565-130">6</span><span class="sxs-lookup"><span data-stu-id="47565-130">6</span></span> | <span data-ttu-id="47565-131">操作には、不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="47565-131">Operation encountered an unknown error.</span></span> |