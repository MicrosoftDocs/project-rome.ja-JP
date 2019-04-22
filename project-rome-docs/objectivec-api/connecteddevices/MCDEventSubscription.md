---
title: MCDEventSubscription
description: このインターフェイスは、単純なイベントのサブスクリプションを提供します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: ce5a5782f80b54e78a6e3890cd68d9e92c52226c
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801620"
---
# <a name="class-mcdeventsubscription"></a><span data-ttu-id="b8f64-104">クラス `MCDEventSubscription`</span><span class="sxs-lookup"><span data-stu-id="b8f64-104">class `MCDEventSubscription`</span></span> 

```
@interface MCDEventSubscription : NSObject
```  
<span data-ttu-id="b8f64-105">このインターフェイスは、単純なイベントのサブスクリプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="b8f64-105">This interface provides a simple event subscription.</span></span>

## <a name="methods"></a><span data-ttu-id="b8f64-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="b8f64-106">Methods</span></span>

### <a name="cancel"></a><span data-ttu-id="b8f64-107">キャンセル</span><span class="sxs-lookup"><span data-stu-id="b8f64-107">cancel</span></span>
`- (void)cancel;`

<span data-ttu-id="b8f64-108">イベントのサブスクリプションを取り消します。</span><span class="sxs-lookup"><span data-stu-id="b8f64-108">Cancels an event subscription.</span></span> <span data-ttu-id="b8f64-109">この呼び出しを行った後、アタッチされた EventListener はこれ以上のイベント (Already in フライト イベントを配信も可能性があります) を受信しません。</span><span class="sxs-lookup"><span data-stu-id="b8f64-109">After making this call, the attached EventListener will not receive any more events (Already in flight events may still be delivered).</span></span>
<span data-ttu-id="b8f64-110">ConnectedDevices 機能の多くは、ネイティブ コードで行われる、ためにが確実か、常に、キャンセルが呼び出されるか、弱参照は、EventListener によって保持されているリソースの適切なクリーンアップすることを確認するために使用する重要です。</span><span class="sxs-lookup"><span data-stu-id="b8f64-110">Because much of the ConnectedDevices functionality is done in native code, it is important to either always ensure cancel is called or WeakReferences are used to ensure proper clean up of resources held by the EventListener.</span></span>
