---
title: MCDConnectedDevicesAccountType
description: Microsoft 提供のユーザー アカウントの種類を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5461398e3725b7a1e6937172c40336db60432666
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801514"
---
# <a name="enum-mcdconnecteddevicesaccounttype"></a><span data-ttu-id="f8099-104">列挙型 `MCDConnectedDevicesAccountType`</span><span class="sxs-lookup"><span data-stu-id="f8099-104">enum `MCDConnectedDevicesAccountType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountType)
```  

<span data-ttu-id="f8099-105">Microsoft 提供のユーザー アカウントの種類を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f8099-105">Contains values that describe the type of Microsoft-provided user account.</span></span>

## <a name="fields"></a><span data-ttu-id="f8099-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="f8099-106">Fields</span></span>

| <span data-ttu-id="f8099-107">名前</span><span class="sxs-lookup"><span data-stu-id="f8099-107">Name</span></span>                              | <span data-ttu-id="f8099-108">値</span><span class="sxs-lookup"><span data-stu-id="f8099-108">Value</span></span> | <span data-ttu-id="f8099-109">説明</span><span class="sxs-lookup"><span data-stu-id="f8099-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="f8099-110">MCDConnectedDevicesAccountTypeAAD</span><span class="sxs-lookup"><span data-stu-id="f8099-110">MCDConnectedDevicesAccountTypeAAD</span></span>       | <span data-ttu-id="f8099-111">0</span><span class="sxs-lookup"><span data-stu-id="f8099-111">0</span></span>     | <span data-ttu-id="f8099-112">Azure Active Directory に社内アカウント</span><span class="sxs-lookup"><span data-stu-id="f8099-112">Azure Active Directory workplace Account</span></span>  |
| <span data-ttu-id="f8099-113">MCDConnectedDevicesAccountTypeMSA</span><span class="sxs-lookup"><span data-stu-id="f8099-113">MCDConnectedDevicesAccountTypeMSA</span></span>       | <span data-ttu-id="f8099-114">1</span><span class="sxs-lookup"><span data-stu-id="f8099-114">1</span></span>     | <span data-ttu-id="f8099-115">Microsoft の個人アカウント</span><span class="sxs-lookup"><span data-stu-id="f8099-115">Microsoft Personal Account</span></span> |
| <span data-ttu-id="f8099-116">MCDConnectedDevicesAccountTypeAnonymous</span><span class="sxs-lookup"><span data-stu-id="f8099-116">MCDConnectedDevicesAccountTypeAnonymous</span></span> | <span data-ttu-id="f8099-117">2</span><span class="sxs-lookup"><span data-stu-id="f8099-117">2</span></span>     | <span data-ttu-id="f8099-118">匿名 (ローカル、認証されていない) アカウント</span><span class="sxs-lookup"><span data-stu-id="f8099-118">Anonymous (local, non-authenticated) Account</span></span> |