---
title: MCDAppServiceProvider
description: このプロトコルには、ローカル アプリ サービスをリモート デバイスにアクセスできるようにするためのメソッドが含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: f5af56a2c87e3b4335a2a59a0130ef3622af6c26
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908664"
---
# <a name="protocol-mcdappserviceprovider"></a><span data-ttu-id="0a9f5-104">プロトコル `MCDAppServiceProvider`</span><span class="sxs-lookup"><span data-stu-id="0a9f5-104">protocol `MCDAppServiceProvider`</span></span>

```
@protocol MCDAppServiceProvider<NSObject>
```

<span data-ttu-id="0a9f5-105">このプロトコルには、ローカル アプリ サービスをリモート デバイスにアクセスできるようにするためのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0a9f5-105">This protocol contains methods for making a local app service accessible to remote devices.</span></span> <span data-ttu-id="0a9f5-106">開発者は、アプリ サービスをリモート接続に使用できるようにするには、このプロトコルを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a9f5-106">Developers must implement this protocol to make their app services available for remote connectivity.</span></span>

## <a name="properties"></a><span data-ttu-id="0a9f5-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0a9f5-107">Properties</span></span>
 
### <a name="appserviceinfo"></a><span data-ttu-id="0a9f5-108">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="0a9f5-108">appServiceInfo</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="0a9f5-109">この app service についての説明。</span><span class="sxs-lookup"><span data-stu-id="0a9f5-109">The descriptive information about this app service.</span></span>

## <a name="methods"></a><span data-ttu-id="0a9f5-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="0a9f5-110">Methods</span></span>

### <a name="connectiondidopen"></a><span data-ttu-id="0a9f5-111">connectionDidOpen</span><span class="sxs-lookup"><span data-stu-id="0a9f5-111">connectionDidOpen</span></span>
`- (void)connectionDidOpen:(nonnull MCDAppServiceConnectionOpenedInfo*)openedInfo;`

<span data-ttu-id="0a9f5-112">この app service にアプリのリモート サービスの接続を開いたときに、このメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0a9f5-112">This method is called when a remote app service connection is opened to this app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="0a9f5-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a9f5-113">Parameters</span></span> 
* `openedInfo`

<span data-ttu-id="0a9f5-114">App service でリモート メッセージの情報を含む MDCAppServiceConnectionOpenedInfo インスタンス。</span><span class="sxs-lookup"><span data-stu-id="0a9f5-114">A MDCAppServiceConnectionOpenedInfo instance containing information for remote messaging with the app service.</span></span>