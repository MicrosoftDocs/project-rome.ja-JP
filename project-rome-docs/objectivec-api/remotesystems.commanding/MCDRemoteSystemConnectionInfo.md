---
title: MCDRemoteSystemConnectionInfo
description: さらに、指定された MCDAppServiceConnection インスタンスに関する情報を提供するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: cdfe9dec49e90013f8c967223803144ad655378e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907054"
---
# <a name="class-mcdremotesystemconnectioninfo"></a><span data-ttu-id="5d67b-104">クラス `MCDRemoteSystemConnectionInfo`</span><span class="sxs-lookup"><span data-stu-id="5d67b-104">class `MCDRemoteSystemConnectionInfo`</span></span> 

```
@interface MCDRemoteSystemConnectionInfo : NSObject
```  

<span data-ttu-id="5d67b-105">に関する情報を提供するクラスを指定した**[MCDAppServiceConnection](MCDAppServiceConnection.md)** インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5d67b-105">A class that provides further information about a given **[MCDAppServiceConnection](MCDAppServiceConnection.md)** instance.</span></span>

## <a name="properties"></a><span data-ttu-id="5d67b-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5d67b-106">Properties</span></span>

### <a name="proximal"></a><span data-ttu-id="5d67b-107">位</span><span class="sxs-lookup"><span data-stu-id="5d67b-107">proximal</span></span>
`@property(nonatomic, readonly, getter=isProximal) BOOL proximal;`

<span data-ttu-id="5d67b-108">位の接続に関連付けられているかどうかが表示されます (**はい**) かどうか (**いいえ**)。</span><span class="sxs-lookup"><span data-stu-id="5d67b-108">Displays whether the associated connection is a proximal connection (**YES**) or not (**NO**).</span></span>

## <a name="constructors"></a><span data-ttu-id="5d67b-109">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="5d67b-109">Constructors</span></span>

### <a name="trycreatefromappserviceconnection"></a><span data-ttu-id="5d67b-110">tryCreateFromAppServiceConnection</span><span class="sxs-lookup"><span data-stu-id="5d67b-110">tryCreateFromAppServiceConnection</span></span>
`+ (nullable instancetype)tryCreateFromAppServiceConnection:(nonnull MCDAppServiceConnection*)appServiceConnection;`

<span data-ttu-id="5d67b-111">特定のアプリ サービスの接続からは、このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5d67b-111">Creates an instance of this class from the given app service connection.</span></span>

#### <a name="parameters"></a><span data-ttu-id="5d67b-112">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5d67b-112">Parameters</span></span>
* `appServiceConnection` 

<span data-ttu-id="5d67b-113">**MCDAppServiceConnection**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5d67b-113">An **MCDAppServiceConnection** instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="5d67b-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="5d67b-114">Returns</span></span>
<span data-ttu-id="5d67b-115">アプリ サービスの接続に対応するこのクラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="5d67b-115">Returns an instance of this class corresponding to the app service connection.</span></span>