---
title: MCDConnectedDevicesAccountAddedStatus
description: MCDConnectedDevicesAccountAddedStatus 列挙型について説明します。 この列挙には、アカウントの追加操作の状態を表す値が含まれます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: f7ea80735a8df2138f2557ff2e7ab4db0b4a9800
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761036"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a><span data-ttu-id="9f7b8-105">enum `MCDConnectedDevicesAccountAddedStatus`</span><span class="sxs-lookup"><span data-stu-id="9f7b8-105">enum `MCDConnectedDevicesAccountAddedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
<span data-ttu-id="9f7b8-106">アカウントの追加操作の状態を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="9f7b8-106">Contains the values that describe the add account operation status.</span></span>

## <a name="fields"></a><span data-ttu-id="9f7b8-107">フィールド</span><span class="sxs-lookup"><span data-stu-id="9f7b8-107">Fields</span></span>

| <span data-ttu-id="9f7b8-108">名前</span><span class="sxs-lookup"><span data-stu-id="9f7b8-108">Name</span></span>                              |   <span data-ttu-id="9f7b8-109">[値]</span><span class="sxs-lookup"><span data-stu-id="9f7b8-109">Value</span></span>     | <span data-ttu-id="9f7b8-110">説明</span><span class="sxs-lookup"><span data-stu-id="9f7b8-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="9f7b8-111">MCDConnectedDevicesAccountAddedStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="9f7b8-111">MCDConnectedDevicesAccountAddedStatusSuccess</span></span> | <span data-ttu-id="9f7b8-112">0</span><span class="sxs-lookup"><span data-stu-id="9f7b8-112">0</span></span> | <span data-ttu-id="9f7b8-113">アカウントがプラットフォームに正常に追加されました。</span><span class="sxs-lookup"><span data-stu-id="9f7b8-113">The account was successfully added to the platform.</span></span> |
| <span data-ttu-id="9f7b8-114">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="9f7b8-114">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span></span> | <span data-ttu-id="9f7b8-115">1</span><span class="sxs-lookup"><span data-stu-id="9f7b8-115">1</span></span> | <span data-ttu-id="9f7b8-116">ローマがネットワークアクセスを検出しなかったため、アカウント操作に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f7b8-116">The account operation failed since Rome detected no network access.</span></span> |
| <span data-ttu-id="9f7b8-117">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span><span class="sxs-lookup"><span data-stu-id="9f7b8-117">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span></span> | <span data-ttu-id="9f7b8-118">2</span><span class="sxs-lookup"><span data-stu-id="9f7b8-118">2</span></span> | <span data-ttu-id="9f7b8-119">ローマが web サービスに接続できなかったため、アカウント操作に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f7b8-119">The account operation failed since Rome was unable to contact web services.</span></span> |
| <span data-ttu-id="9f7b8-120">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="9f7b8-120">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="9f7b8-121">3</span><span class="sxs-lookup"><span data-stu-id="9f7b8-121">3</span></span> | <span data-ttu-id="9f7b8-122">アプリが AccessTokenRequested イベントをサブスクライブしていなかったため、アカウント操作に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f7b8-122">The account operation failed since the app didn't subscribe to the AccessTokenRequested event.</span></span> |
| <span data-ttu-id="9f7b8-123">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="9f7b8-123">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="9f7b8-124">4</span><span class="sxs-lookup"><span data-stu-id="9f7b8-124">4</span></span> | <span data-ttu-id="9f7b8-125">アプリが要求されたときにトークンを返すことができなかったため、アカウント操作に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f7b8-125">The account operation failed since the app failed to return a token when requested.</span></span> |
| <span data-ttu-id="9f7b8-126">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="9f7b8-126">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span></span> | <span data-ttu-id="9f7b8-127">5</span><span class="sxs-lookup"><span data-stu-id="9f7b8-127">5</span></span> | <span data-ttu-id="9f7b8-128">不明な理由により、アカウント操作に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="9f7b8-128">The account operation failed for unknown reasons.</span></span> |
