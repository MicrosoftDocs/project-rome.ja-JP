---
title: MCDRemoteSystemLocalVisibilityKind
description: リモート システムの探索時に、ローカル アプリケーションの可視性の基本設定を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801104"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a><span data-ttu-id="0af54-104">列挙型 `MCDRemoteSystemLocalVisibilityKind`</span><span class="sxs-lookup"><span data-stu-id="0af54-104">enum `MCDRemoteSystemLocalVisibilityKind`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
<span data-ttu-id="0af54-105">リモート システムの探索時に、ローカル アプリケーションの可視性の基本設定を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0af54-105">Contains values that describe the local application visibility preference when discovering remote systems.</span></span>

## <a name="fields"></a><span data-ttu-id="0af54-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="0af54-106">Fields</span></span>

| <span data-ttu-id="0af54-107">名前</span><span class="sxs-lookup"><span data-stu-id="0af54-107">Name</span></span>                              | <span data-ttu-id="0af54-108">値</span><span class="sxs-lookup"><span data-stu-id="0af54-108">Value</span></span> | <span data-ttu-id="0af54-109">説明</span><span class="sxs-lookup"><span data-stu-id="0af54-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="0af54-110">MCDRemoteSystemLocalVisibilityKindShowAll</span><span class="sxs-lookup"><span data-stu-id="0af54-110">MCDRemoteSystemLocalVisibilityKindShowAll</span></span> | <span data-ttu-id="0af54-111">0</span><span class="sxs-lookup"><span data-stu-id="0af54-111">0</span></span> | <span data-ttu-id="0af54-112">呼び出し元のアプリを含むすべての探索可能なアプリケーションを表示します。</span><span class="sxs-lookup"><span data-stu-id="0af54-112">Show all discoverable applications, including the calling app.</span></span>
| <span data-ttu-id="0af54-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span><span class="sxs-lookup"><span data-stu-id="0af54-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span></span> | <span data-ttu-id="0af54-114">1</span><span class="sxs-lookup"><span data-stu-id="0af54-114">1</span></span> | <span data-ttu-id="0af54-115">呼び出し元のアプリケーションを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="0af54-115">Hide the calling application.</span></span>