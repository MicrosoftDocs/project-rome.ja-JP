---
title: MCDEventSubscription
description: MCDEventSubscription クラスについて説明します。 このインターフェイスは、イベントサブスクリプションを簡単に管理する方法を提供します。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 8f44d1ca75ea247f2cb26fe5b2c136b4db0bd97f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761076"
---
# <a name="class-mcdeventsubscription"></a><span data-ttu-id="f0e82-105">講義 `MCDEventSubscription`</span><span class="sxs-lookup"><span data-stu-id="f0e82-105">class `MCDEventSubscription`</span></span> 

```
@interface MCDEventSubscription : NSObject
```  
<span data-ttu-id="f0e82-106">このインターフェイスは、単純なイベントサブスクリプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="f0e82-106">This interface provides a simple event subscription.</span></span>

## <a name="methods"></a><span data-ttu-id="f0e82-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="f0e82-107">Methods</span></span>

### <a name="cancel"></a><span data-ttu-id="f0e82-108">cancel</span><span class="sxs-lookup"><span data-stu-id="f0e82-108">cancel</span></span>
`- (void)cancel;`

<span data-ttu-id="f0e82-109">イベントのサブスクリプションを取り消します。</span><span class="sxs-lookup"><span data-stu-id="f0e82-109">Cancels an event subscription.</span></span> <span data-ttu-id="f0e82-110">この呼び出しを行った後、アタッチされた EventListener はそれ以上イベントを受信しません (既にフライトイベントが配信されている可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="f0e82-110">After making this call, the attached EventListener will not receive any more events (Already in flight events may still be delivered).</span></span>
<span data-ttu-id="f0e82-111">ConnectedDevices 機能の多くはネイティブコードで実行されるので、EventListener によって保持されているリソースが適切にクリーンアップされるようにするには、常に cancel を呼び出すか、または使用しないことを確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="f0e82-111">Because much of the ConnectedDevices functionality is done in native code, it is important to either always ensure cancel is called or WeakReferences are used to ensure proper clean up of resources held by the EventListener.</span></span>
