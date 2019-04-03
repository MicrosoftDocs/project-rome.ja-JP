---
title: MCDConnectedDevicesAccountType
description: Microsoft 提供のユーザー アカウントの種類を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5461398e3725b7a1e6937172c40336db60432666
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908904"
---
# <a name="enum-mcdconnecteddevicesaccounttype"></a><span data-ttu-id="d5ec9-104">列挙型 `MCDConnectedDevicesAccountType`</span><span class="sxs-lookup"><span data-stu-id="d5ec9-104">enum `MCDConnectedDevicesAccountType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountType)
```  

<span data-ttu-id="d5ec9-105">Microsoft 提供のユーザー アカウントの種類を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d5ec9-105">Contains values that describe the type of Microsoft-provided user account.</span></span>

## <a name="fields"></a><span data-ttu-id="d5ec9-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="d5ec9-106">Fields</span></span>

| <span data-ttu-id="d5ec9-107">名前</span><span class="sxs-lookup"><span data-stu-id="d5ec9-107">Name</span></span>                              | <span data-ttu-id="d5ec9-108">値</span><span class="sxs-lookup"><span data-stu-id="d5ec9-108">Value</span></span> | <span data-ttu-id="d5ec9-109">説明</span><span class="sxs-lookup"><span data-stu-id="d5ec9-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="d5ec9-110">MCDConnectedDevicesAccountTypeAAD</span><span class="sxs-lookup"><span data-stu-id="d5ec9-110">MCDConnectedDevicesAccountTypeAAD</span></span>       | <span data-ttu-id="d5ec9-111">0</span><span class="sxs-lookup"><span data-stu-id="d5ec9-111">0</span></span>     | <span data-ttu-id="d5ec9-112">Azure Active Directory に社内アカウント</span><span class="sxs-lookup"><span data-stu-id="d5ec9-112">Azure Active Directory workplace Account</span></span>  |
| <span data-ttu-id="d5ec9-113">MCDConnectedDevicesAccountTypeMSA</span><span class="sxs-lookup"><span data-stu-id="d5ec9-113">MCDConnectedDevicesAccountTypeMSA</span></span>       | <span data-ttu-id="d5ec9-114">1</span><span class="sxs-lookup"><span data-stu-id="d5ec9-114">1</span></span>     | <span data-ttu-id="d5ec9-115">Microsoft の個人アカウント</span><span class="sxs-lookup"><span data-stu-id="d5ec9-115">Microsoft Personal Account</span></span> |
| <span data-ttu-id="d5ec9-116">MCDConnectedDevicesAccountTypeAnonymous</span><span class="sxs-lookup"><span data-stu-id="d5ec9-116">MCDConnectedDevicesAccountTypeAnonymous</span></span> | <span data-ttu-id="d5ec9-117">2</span><span class="sxs-lookup"><span data-stu-id="d5ec9-117">2</span></span>     | <span data-ttu-id="d5ec9-118">匿名 (ローカル、認証されていない) アカウント</span><span class="sxs-lookup"><span data-stu-id="d5ec9-118">Anonymous (local, non-authenticated) Account</span></span> |