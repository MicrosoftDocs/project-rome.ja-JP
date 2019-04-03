---
title: MCDStatelessAppServiceResponse
description: リモート アプリ サービスから MCDAppServiceConnection.sendStatelessMessageAsync 以前の呼び出しへの応答でクライアント アプリに渡されるメッセージを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 4e650b1b114a3cb05b2d9b03b833b9e1cdd6607c
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907234"
---
# <a name="class-mcdstatelessappserviceresponse"></a><span data-ttu-id="b0bbf-104">クラス `MCDStatelessAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="b0bbf-104">class `MCDStatelessAppServiceResponse`</span></span> 

```
@interface MCDStatelessAppServiceResponse : NSObject
```  

<span data-ttu-id="b0bbf-105">リモート アプリ サービスから MCDAppServiceConnection.sendStatelessMessageAsync 以前の呼び出しへの応答でクライアント アプリに渡されるメッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="b0bbf-105">Represents a message passed from a remote app service to the client app in response to a previous call to MCDAppServiceConnection.sendStatelessMessageAsync.</span></span>


## <a name="properties"></a><span data-ttu-id="b0bbf-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b0bbf-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="b0bbf-107">メッセージ</span><span class="sxs-lookup"><span data-stu-id="b0bbf-107">message</span></span>
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="b0bbf-108">キー/値ペアから成る、リモート アプリ サービスによって送信されるメッセージ。</span><span class="sxs-lookup"><span data-stu-id="b0bbf-108">The message sent by the remote app service, consisting of key/value pairs.</span></span>

### <a name="status"></a><span data-ttu-id="b0bbf-109">status</span><span class="sxs-lookup"><span data-stu-id="b0bbf-109">status</span></span>
`@property(nonatomic, readonly) MCDStatelessAppServiceResponseStatus status;`

<span data-ttu-id="b0bbf-110">リモート アプリ サービスからの応答のステータス。</span><span class="sxs-lookup"><span data-stu-id="b0bbf-110">The status of the response from the remote app service.</span></span>

