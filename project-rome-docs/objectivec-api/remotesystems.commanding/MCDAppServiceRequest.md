---
title: MCDAppServiceRequest
description: リモート アプリ/デバイスからこのアプリ サービスの接続を受信したメッセージを表します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 553403ab57b594294072dc082f5646eb1646e55b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907574"
---
# <a name="class-mcdappservicerequest"></a><span data-ttu-id="88b5e-104">クラス `MCDAppServiceRequest`</span><span class="sxs-lookup"><span data-stu-id="88b5e-104">class `MCDAppServiceRequest`</span></span>

```
@interface MCDAppServiceRequest : NSObject
```
<span data-ttu-id="88b5e-105">リモート アプリ/デバイスからこのアプリ サービスの接続を受信したメッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="88b5e-105">Represents an incoming message from a remote app/device to this app service connection.</span></span>

## <a name="properties"></a><span data-ttu-id="88b5e-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="88b5e-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="88b5e-107">メッセージ</span><span class="sxs-lookup"><span data-stu-id="88b5e-107">message</span></span> 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="88b5e-108">リモート アプリ サービスのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="88b5e-108">The message for the remote app service.</span></span>

## <a name="methods"></a><span data-ttu-id="88b5e-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="88b5e-109">Methods</span></span>

### <a name="sendresponseasync"></a><span data-ttu-id="88b5e-110">sendResponseAsync</span><span class="sxs-lookup"><span data-stu-id="88b5e-110">sendResponseAsync</span></span> 
```
- (void)sendResponseAsync:(nonnull NSDictionary*)message
               completion:(nonnull void (^)(MCDAppServiceResponseStatus, NSError* _Nullable))completion;
```

<span data-ttu-id="88b5e-111">要求を送信したリモートの app service への応答メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="88b5e-111">Sends a response message to the remote app service that sent the request.</span></span>

#### <a name="parameters"></a><span data-ttu-id="88b5e-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="88b5e-112">Parameters</span></span>
* `message` 

<span data-ttu-id="88b5e-113">リモート アプリ サービスのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="88b5e-113">The message for the remote app service.</span></span>

* `completion`     

<span data-ttu-id="88b5e-114">送信操作の状態を示す MCDAppServiceResponseStatus 値を持つ非同期の操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="88b5e-114">The completion of the asynchronous operation with an MCDAppServiceResponseStatus value indicating the status of the send operation.</span></span>