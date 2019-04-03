---
title: MCDEvent
description: このインターフェイスは、単純なイベント モデルを提供します。 イベントは、EventListeners によって消費される項目を生成します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: eabe9464a104593b06460153ed30f42f7cc103eb
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907254"
---
# <a name="class-mcdevent"></a><span data-ttu-id="c2e7f-105">クラス `MCDEvent`</span><span class="sxs-lookup"><span data-stu-id="c2e7f-105">class `MCDEvent`</span></span> 

```
@interface MCDEvent<__covariant SourceType, __covariant ArgsType> : NSObject
```  
 
 <span data-ttu-id="c2e7f-106">このインターフェイスは、単純なイベント モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="c2e7f-106">This interface provides a simple event model.</span></span> <span data-ttu-id="c2e7f-107">イベントは、EventListeners によって消費される項目を生成します。</span><span class="sxs-lookup"><span data-stu-id="c2e7f-107">Events produce items consumed by EventListeners.</span></span>
<span data-ttu-id="c2e7f-108">イベントの項目のフローは、MCDEventSubscription によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="c2e7f-108">The flow of event items is controlled by the MCDEventSubscription.</span></span>

## <a name="methods"></a><span data-ttu-id="c2e7f-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="c2e7f-109">Methods</span></span>

### <a name="subscribe"></a><span data-ttu-id="c2e7f-110">サブスクライブ (subscribe)</span><span class="sxs-lookup"><span data-stu-id="c2e7f-110">subscribe</span></span>
`- (nonnull MCDEventSubscription*)subscribe:(nonnull void (^)(SourceType _Nonnull, ArgsType _Nonnull))listener;`

<span data-ttu-id="c2e7f-111">特定の接続されているデバイス プラットフォームでのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="c2e7f-111">Subscribe to given events in the Connected Devices Platform.</span></span>

#### <a name="parameters"></a><span data-ttu-id="c2e7f-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2e7f-112">Parameters</span></span> 
* `listener` 

<span data-ttu-id="c2e7f-113">MCDEventSubscriptions をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="c2e7f-113">Listen to MCDEventSubscriptions.</span></span>

#### <a name="returns"></a><span data-ttu-id="c2e7f-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="c2e7f-114">Returns</span></span>
<span data-ttu-id="c2e7f-115">MCDEventSubscription のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="c2e7f-115">An instance of the MCDEventSubscription.</span></span>