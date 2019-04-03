---
title: MCDRemoteSystemLocalVisibilityKind
description: リモート システムの探索時に、ローカル アプリケーションの可視性の基本設定を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908864"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a><span data-ttu-id="c80b7-104">列挙型 `MCDRemoteSystemLocalVisibilityKind`</span><span class="sxs-lookup"><span data-stu-id="c80b7-104">enum `MCDRemoteSystemLocalVisibilityKind`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
<span data-ttu-id="c80b7-105">リモート システムの探索時に、ローカル アプリケーションの可視性の基本設定を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c80b7-105">Contains values that describe the local application visibility preference when discovering remote systems.</span></span>

## <a name="fields"></a><span data-ttu-id="c80b7-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="c80b7-106">Fields</span></span>

| <span data-ttu-id="c80b7-107">名前</span><span class="sxs-lookup"><span data-stu-id="c80b7-107">Name</span></span>                              | <span data-ttu-id="c80b7-108">値</span><span class="sxs-lookup"><span data-stu-id="c80b7-108">Value</span></span> | <span data-ttu-id="c80b7-109">説明</span><span class="sxs-lookup"><span data-stu-id="c80b7-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="c80b7-110">MCDRemoteSystemLocalVisibilityKindShowAll</span><span class="sxs-lookup"><span data-stu-id="c80b7-110">MCDRemoteSystemLocalVisibilityKindShowAll</span></span> | <span data-ttu-id="c80b7-111">0</span><span class="sxs-lookup"><span data-stu-id="c80b7-111">0</span></span> | <span data-ttu-id="c80b7-112">呼び出し元のアプリを含むすべての探索可能なアプリケーションを表示します。</span><span class="sxs-lookup"><span data-stu-id="c80b7-112">Show all discoverable applications, including the calling app.</span></span>
| <span data-ttu-id="c80b7-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span><span class="sxs-lookup"><span data-stu-id="c80b7-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span></span> | <span data-ttu-id="c80b7-114">1</span><span class="sxs-lookup"><span data-stu-id="c80b7-114">1</span></span> | <span data-ttu-id="c80b7-115">呼び出し元のアプリケーションを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="c80b7-115">Hide the calling application.</span></span>