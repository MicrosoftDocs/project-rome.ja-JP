---
title: MCDRemoteSystem
description: リモート システムを表すクラス。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5f0ab2108d4efa486b992bf7bc8c8847692623da
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801764"
---
# <a name="class-mcdremotesystem"></a><span data-ttu-id="9fade-104">クラス `MCDRemoteSystem`</span><span class="sxs-lookup"><span data-stu-id="9fade-104">class `MCDRemoteSystem`</span></span> 

```
@interface MCDRemoteSystem : NSObject
```  

<span data-ttu-id="9fade-105">リモート システムを表すクラス。</span><span class="sxs-lookup"><span data-stu-id="9fade-105">A class to represent a remote system.</span></span>

## <a name="properties"></a><span data-ttu-id="9fade-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9fade-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="9fade-107">種類</span><span class="sxs-lookup"><span data-stu-id="9fade-107">kind</span></span>
`@property(nonatomic, readonly, nonnull) NSString* kind;`

<span data-ttu-id="9fade-108">このリモート システムのデバイスの種類。</span><span class="sxs-lookup"><span data-stu-id="9fade-108">The device type of this remote system.</span></span>

### <a name="systemid"></a><span data-ttu-id="9fade-109">systemId</span><span class="sxs-lookup"><span data-stu-id="9fade-109">systemId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

<span data-ttu-id="9fade-110">このリモート システムの識別子。</span><span class="sxs-lookup"><span data-stu-id="9fade-110">The identifier for this remote system.</span></span>

### <a name="displayname"></a><span data-ttu-id="9fade-111">displayName</span><span class="sxs-lookup"><span data-stu-id="9fade-111">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="9fade-112">リモート システムの名前。</span><span class="sxs-lookup"><span data-stu-id="9fade-112">The name of the given remote system.</span></span>

### <a name="status"></a><span data-ttu-id="9fade-113">status</span><span class="sxs-lookup"><span data-stu-id="9fade-113">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

<span data-ttu-id="9fade-114">このリモート システムの可用性の状態です。</span><span class="sxs-lookup"><span data-stu-id="9fade-114">The status of this remote system's availability.</span></span>

> [!NOTE]
<span data-ttu-id="9fade-115">WNS プレゼンスは、Windows デバイスと通知の種類として WNS を使用している場合、アプリケーションの可用性をレポートに使用されます。</span><span class="sxs-lookup"><span data-stu-id="9fade-115">WNS presence is used for reporting availability for Windows devices and apps which use WNS as notification type.</span></span>  <span data-ttu-id="9fade-116">デバイスは使用可能な (Windows) と見なされる場合、または基になるアプリのいずれかのレポートの自分の存在「使用可能な」とマークされます RemoteSystem 利用可能な (iOS と Android)。</span><span class="sxs-lookup"><span data-stu-id="9fade-116">RemoteSystem will be marked as "available" when the device is considered available (Windows) or when one of the underlying apps reports their presence as available (iOS and Android).</span></span> 

### <a name="manufacturerdisplayname"></a><span data-ttu-id="9fade-117">manufacturerDisplayName</span><span class="sxs-lookup"><span data-stu-id="9fade-117">manufacturerDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

<span data-ttu-id="9fade-118">リモート システムの製造元の名前。</span><span class="sxs-lookup"><span data-stu-id="9fade-118">The manufacturer name of the given remote system.</span></span>

### <a name="modeldisplayname"></a><span data-ttu-id="9fade-119">modelDisplayName</span><span class="sxs-lookup"><span data-stu-id="9fade-119">modelDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

<span data-ttu-id="9fade-120">リモート システムのモデル名。</span><span class="sxs-lookup"><span data-stu-id="9fade-120">The model name of the given remote system.</span></span>

### <a name="apps"></a><span data-ttu-id="9fade-121">アプリ</span><span class="sxs-lookup"><span data-stu-id="9fade-121">apps</span></span>
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

<span data-ttu-id="9fade-122">このリモート システム上の接続で利用可能なアプリケーションの配列。</span><span class="sxs-lookup"><span data-stu-id="9fade-122">An array of the applications on this remote system that are available for connectivity.</span></span>

### <a name="platform"></a><span data-ttu-id="9fade-123">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="9fade-123">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="9fade-124">リモート システムの使用状況を管理する MCDRemoteSystemPlatform します。</span><span class="sxs-lookup"><span data-stu-id="9fade-124">The MCDRemoteSystemPlatform managing remote system activity.</span></span>