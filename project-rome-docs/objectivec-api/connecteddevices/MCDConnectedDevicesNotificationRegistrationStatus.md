---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: クラウドの登録の状態を通信するために使用される値。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: c7d770c73479afb949a4917b5457b12e23b78698
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909134"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a><span data-ttu-id="bd557-104">クラス `MCDConnectedDevicesNotificationRegistrationStatus`</span><span class="sxs-lookup"><span data-stu-id="bd557-104">class `MCDConnectedDevicesNotificationRegistrationStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
<span data-ttu-id="bd557-105">登録操作の状態を示す列挙です。</span><span class="sxs-lookup"><span data-stu-id="bd557-105">Enumeration indicating the status of the registration operation.</span></span>
<span data-ttu-id="bd557-106">エラー状態では、アプリ開発者の登録を再試行する必要のある一時的な状態を示します。</span><span class="sxs-lookup"><span data-stu-id="bd557-106">The error statuses indicate transient conditions where the app developer may want to retry registration.</span></span>

## <a name="fields"></a><span data-ttu-id="bd557-107">フィールド</span><span class="sxs-lookup"><span data-stu-id="bd557-107">Fields</span></span>

| <span data-ttu-id="bd557-108">名前</span><span class="sxs-lookup"><span data-stu-id="bd557-108">Name</span></span>                              |   <span data-ttu-id="bd557-109">値</span><span class="sxs-lookup"><span data-stu-id="bd557-109">Value</span></span>     | <span data-ttu-id="bd557-110">説明</span><span class="sxs-lookup"><span data-stu-id="bd557-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="bd557-111">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="bd557-111">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span></span> | <span data-ttu-id="bd557-112">0</span><span class="sxs-lookup"><span data-stu-id="bd557-112">0</span></span> | <span data-ttu-id="bd557-113">操作が正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="bd557-113">Operation completed successfully.</span></span>
| <span data-ttu-id="bd557-114">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="bd557-114">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span></span> | <span data-ttu-id="bd557-115">1</span><span class="sxs-lookup"><span data-stu-id="bd557-115">1</span></span> | <span data-ttu-id="bd557-116">ネットワークは使用できませんでした。</span><span class="sxs-lookup"><span data-stu-id="bd557-116">Network was unavailable.</span></span> |
| <span data-ttu-id="bd557-117">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span><span class="sxs-lookup"><span data-stu-id="bd557-117">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span></span> | <span data-ttu-id="bd557-118">2</span><span class="sxs-lookup"><span data-stu-id="bd557-118">2</span></span> | <span data-ttu-id="bd557-119">Web サービスが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="bd557-119">A web service failed.</span></span> |
| <span data-ttu-id="bd557-120">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="bd557-120">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="bd557-121">3</span><span class="sxs-lookup"><span data-stu-id="bd557-121">3</span></span> | <span data-ttu-id="bd557-122">トークン要求のサブスクライバーが応答しません。</span><span class="sxs-lookup"><span data-stu-id="bd557-122">No token request subscribers responded.</span></span> |
| <span data-ttu-id="bd557-123">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="bd557-123">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="bd557-124">4</span><span class="sxs-lookup"><span data-stu-id="bd557-124">4</span></span> | <span data-ttu-id="bd557-125">トークンの要求が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="bd557-125">The token request failed.</span></span> |
| <span data-ttu-id="bd557-126">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span><span class="sxs-lookup"><span data-stu-id="bd557-126">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span></span> | <span data-ttu-id="bd557-127">5</span><span class="sxs-lookup"><span data-stu-id="bd557-127">5</span></span> | <span data-ttu-id="bd557-128">情報を登録するアカウントが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="bd557-128">Account to register information for was not found.</span></span> |
| <span data-ttu-id="bd557-129">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="bd557-129">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span></span> | <span data-ttu-id="bd557-130">6</span><span class="sxs-lookup"><span data-stu-id="bd557-130">6</span></span> | <span data-ttu-id="bd557-131">操作には、不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bd557-131">Operation encountered an unknown error.</span></span> |