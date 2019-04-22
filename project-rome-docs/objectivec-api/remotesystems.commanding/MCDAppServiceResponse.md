---
title: MCDAppServiceResponse
description: 接続されたリモート アプリ サービスから受信した応答を表すクラス。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 74cff4a84bdc4bf073dd57319c987e274ea8ceaf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800794"
---
# <a name="class-mcdappserviceresponse"></a><span data-ttu-id="75100-104">クラス `MCDAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="75100-104">class `MCDAppServiceResponse`</span></span>

```
@interface MCDAppServiceResponse : NSObject
```

<span data-ttu-id="75100-105">接続されたリモート アプリ サービスから受信した応答を表すクラス。</span><span class="sxs-lookup"><span data-stu-id="75100-105">A class that represents a response received from a connected remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="75100-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="75100-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="75100-107">メッセージ</span><span class="sxs-lookup"><span data-stu-id="75100-107">message</span></span> 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="75100-108">リモート アプリ サービスから受信したメッセージ。</span><span class="sxs-lookup"><span data-stu-id="75100-108">The message received from the remote app service.</span></span>

### <a name="status"></a><span data-ttu-id="75100-109">status</span><span class="sxs-lookup"><span data-stu-id="75100-109">status</span></span>
`@property(nonatomic, readonly) MCDAppServiceResponseStatus status;`

<span data-ttu-id="75100-110">受信した応答の状態です。</span><span class="sxs-lookup"><span data-stu-id="75100-110">The status of the response received.</span></span>