---
title: MCDRemoteSystemAuthorizationKind
description: リモート システムの探索の潜在的な承認種類 (ユーザー アカウント ベースの承認スコープ) を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 4f54d187282e946dd2912d1d72eacc02c7ee4077
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907634"
---
# <a name="enum-mcdremotesystemauthorizationkind"></a><span data-ttu-id="a0cce-104">列挙型 `MCDRemoteSystemAuthorizationKind`</span><span class="sxs-lookup"><span data-stu-id="a0cce-104">enum `MCDRemoteSystemAuthorizationKind`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemAuthorizationKind)
```  

<span data-ttu-id="a0cce-105">リモート システムの探索の潜在的な承認種類 (ユーザー アカウント ベースの承認スコープ) を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0cce-105">Contains values that describe the potential authorization kinds (user-account-based authorization scopes) for remote system discovery.</span></span> 

## <a name="fields"></a><span data-ttu-id="a0cce-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="a0cce-106">Fields</span></span>

| <span data-ttu-id="a0cce-107">名前</span><span class="sxs-lookup"><span data-stu-id="a0cce-107">Name</span></span>                              | <span data-ttu-id="a0cce-108">値</span><span class="sxs-lookup"><span data-stu-id="a0cce-108">Value</span></span> | <span data-ttu-id="a0cce-109">説明</span><span class="sxs-lookup"><span data-stu-id="a0cce-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="a0cce-110">MCDRemoteSystemAuthorizationKindSameUser</span><span class="sxs-lookup"><span data-stu-id="a0cce-110">MCDRemoteSystemAuthorizationKindSameUser</span></span>   | <span data-ttu-id="a0cce-111">0</span><span class="sxs-lookup"><span data-stu-id="a0cce-111">0</span></span>     | <span data-ttu-id="a0cce-112">システムは検出し、上に同じユーザー アカウントによって署名されたデバイスとの接続のみです。</span><span class="sxs-lookup"><span data-stu-id="a0cce-112">The system can only discover and connect with devices signed onto by the same user account.</span></span>   |
| <span data-ttu-id="a0cce-113">MCDRemoteSystemAuthorizationKindAnonymous</span><span class="sxs-lookup"><span data-stu-id="a0cce-113">MCDRemoteSystemAuthorizationKindAnonymous</span></span> | <span data-ttu-id="a0cce-114">1</span><span class="sxs-lookup"><span data-stu-id="a0cce-114">1</span></span>     | <span data-ttu-id="a0cce-115">システムでは、検出でき、指定の近くでされていて、匿名の検出を許可、他のユーザーのデバイスと接続することができます。</span><span class="sxs-lookup"><span data-stu-id="a0cce-115">The system can discover and connect with other users' devices, provided they are in proximity and allow anonymous discovery.</span></span>  |

