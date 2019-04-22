---
title: MCDStatelessAppServiceResponse
description: リモート アプリ サービスから MCDAppServiceConnection.sendStatelessMessageAsync 以前の呼び出しへの応答でクライアント アプリに渡されるメッセージを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 4e650b1b114a3cb05b2d9b03b833b9e1cdd6607c
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801624"
---
# <a name="class-mcdstatelessappserviceresponse"></a><span data-ttu-id="14738-104">クラス `MCDStatelessAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="14738-104">class `MCDStatelessAppServiceResponse`</span></span> 

```
@interface MCDStatelessAppServiceResponse : NSObject
```  

<span data-ttu-id="14738-105">リモート アプリ サービスから MCDAppServiceConnection.sendStatelessMessageAsync 以前の呼び出しへの応答でクライアント アプリに渡されるメッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="14738-105">Represents a message passed from a remote app service to the client app in response to a previous call to MCDAppServiceConnection.sendStatelessMessageAsync.</span></span>


## <a name="properties"></a><span data-ttu-id="14738-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="14738-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="14738-107">メッセージ</span><span class="sxs-lookup"><span data-stu-id="14738-107">message</span></span>
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="14738-108">キー/値ペアから成る、リモート アプリ サービスによって送信されるメッセージ。</span><span class="sxs-lookup"><span data-stu-id="14738-108">The message sent by the remote app service, consisting of key/value pairs.</span></span>

### <a name="status"></a><span data-ttu-id="14738-109">status</span><span class="sxs-lookup"><span data-stu-id="14738-109">status</span></span>
`@property(nonatomic, readonly) MCDStatelessAppServiceResponseStatus status;`

<span data-ttu-id="14738-110">リモート アプリ サービスからの応答のステータス。</span><span class="sxs-lookup"><span data-stu-id="14738-110">The status of the response from the remote app service.</span></span>

