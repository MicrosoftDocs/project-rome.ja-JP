---
title: MCDRemoteSystem
description: MCDRemoteSystem クラスとそのプロパティについて説明します。 このクラスは、リモートシステムを表すために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: e211de33117f48cc221152cf40645015693dcddc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760996"
---
# <a name="class-mcdremotesystem"></a><span data-ttu-id="1cf92-105">講義 `MCDRemoteSystem`</span><span class="sxs-lookup"><span data-stu-id="1cf92-105">class `MCDRemoteSystem`</span></span> 

```
@interface MCDRemoteSystem : NSObject
```  

<span data-ttu-id="1cf92-106">リモートシステムを表すクラス。</span><span class="sxs-lookup"><span data-stu-id="1cf92-106">A class to represent a remote system.</span></span>

## <a name="properties"></a><span data-ttu-id="1cf92-107">Properties</span><span class="sxs-lookup"><span data-stu-id="1cf92-107">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="1cf92-108">kind</span><span class="sxs-lookup"><span data-stu-id="1cf92-108">kind</span></span>
`@property(nonatomic, readonly, nonnull) NSString* kind;`

<span data-ttu-id="1cf92-109">このリモートシステムのデバイスの種類。</span><span class="sxs-lookup"><span data-stu-id="1cf92-109">The device type of this remote system.</span></span>

### <a name="systemid"></a><span data-ttu-id="1cf92-110">systemId</span><span class="sxs-lookup"><span data-stu-id="1cf92-110">systemId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

<span data-ttu-id="1cf92-111">このリモートシステムの識別子。</span><span class="sxs-lookup"><span data-stu-id="1cf92-111">The identifier for this remote system.</span></span>

### <a name="displayname"></a><span data-ttu-id="1cf92-112">displayName</span><span class="sxs-lookup"><span data-stu-id="1cf92-112">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="1cf92-113">指定されたリモートシステムの名前。</span><span class="sxs-lookup"><span data-stu-id="1cf92-113">The name of the given remote system.</span></span>

### <a name="status"></a><span data-ttu-id="1cf92-114">status</span><span class="sxs-lookup"><span data-stu-id="1cf92-114">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

<span data-ttu-id="1cf92-115">このリモートシステムの可用性の状態。</span><span class="sxs-lookup"><span data-stu-id="1cf92-115">The status of this remote system's availability.</span></span>

> [!NOTE]
<span data-ttu-id="1cf92-116">WNS プレゼンスは、通知の種類として WNS を使用する Windows デバイスとアプリの可用性をレポートするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1cf92-116">WNS presence is used for reporting availability for Windows devices and apps which use WNS as notification type.</span></span>  <span data-ttu-id="1cf92-117">デバイスが使用可能と見なされた場合 (Windows の場合)、または基になるアプリの1つが利用可能として表示される場合 (iOS と Android)、RemoteSystem は "利用可能" とマークされます。</span><span class="sxs-lookup"><span data-stu-id="1cf92-117">RemoteSystem will be marked as "available" when the device is considered available (Windows) or when one of the underlying apps reports their presence as available (iOS and Android).</span></span> 

### <a name="manufacturerdisplayname"></a><span data-ttu-id="1cf92-118">manufacturerDisplayName</span><span class="sxs-lookup"><span data-stu-id="1cf92-118">manufacturerDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

<span data-ttu-id="1cf92-119">指定されたリモートシステムの製造元名。</span><span class="sxs-lookup"><span data-stu-id="1cf92-119">The manufacturer name of the given remote system.</span></span>

### <a name="modeldisplayname"></a><span data-ttu-id="1cf92-120">modelDisplayName</span><span class="sxs-lookup"><span data-stu-id="1cf92-120">modelDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

<span data-ttu-id="1cf92-121">指定されたリモートシステムのモデル名。</span><span class="sxs-lookup"><span data-stu-id="1cf92-121">The model name of the given remote system.</span></span>

### <a name="apps"></a><span data-ttu-id="1cf92-122">アプリ</span><span class="sxs-lookup"><span data-stu-id="1cf92-122">apps</span></span>
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

<span data-ttu-id="1cf92-123">このリモートシステム上の接続に使用できるアプリケーションの配列。</span><span class="sxs-lookup"><span data-stu-id="1cf92-123">An array of the applications on this remote system that are available for connectivity.</span></span>

### <a name="platform"></a><span data-ttu-id="1cf92-124">platform</span><span class="sxs-lookup"><span data-stu-id="1cf92-124">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="1cf92-125">リモートシステムアクティビティを管理する MCDRemoteSystemPlatform。</span><span class="sxs-lookup"><span data-stu-id="1cf92-125">The MCDRemoteSystemPlatform managing remote system activity.</span></span>