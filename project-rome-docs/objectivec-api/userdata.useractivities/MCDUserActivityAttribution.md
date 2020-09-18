---
title: MCDUserActivityAttribution
description: MCDUserActivityAttribution クラスについて説明します。 このクラスは、ユーザーアクティビティのグラフィカル要素を管理します。
keywords: microsoft、windows、ユーザーアクティビティ、iOS、iPhone、、接続デバイス、プロジェクトローマ
ms.openlocfilehash: e4cf9f078215e987c2f0e8068c4afdf640409acc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760196"
---
# <a name="class-mcduseractivityattribution"></a><span data-ttu-id="07427-105">講義 `MCDUserActivityAttribution`</span><span class="sxs-lookup"><span data-stu-id="07427-105">class `MCDUserActivityAttribution`</span></span>

```
@interface MCDUserActivityAttribution : NSObject
```

<span data-ttu-id="07427-106">このクラスは、ユーザーアクティビティのグラフィカル要素を管理します。</span><span class="sxs-lookup"><span data-stu-id="07427-106">This class manages the graphical elements of a user activity.</span></span>

## <a name="properties"></a><span data-ttu-id="07427-107">Properties</span><span class="sxs-lookup"><span data-stu-id="07427-107">Properties</span></span>

### <a name="iconuri"></a><span data-ttu-id="07427-108">iconUri</span><span class="sxs-lookup"><span data-stu-id="07427-108">iconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="07427-109">アイコンイメージの URI。</span><span class="sxs-lookup"><span data-stu-id="07427-109">The URI for the icon image.</span></span>

### <a name="alternatetext"></a><span data-ttu-id="07427-110">alternateText</span><span class="sxs-lookup"><span data-stu-id="07427-110">alternateText</span></span>
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

<span data-ttu-id="07427-111">アイコンイメージを説明するテキスト。スクリーンリーダーで使用します。</span><span class="sxs-lookup"><span data-stu-id="07427-111">The text that describes the icon image (for use with screen readers).</span></span>

### <a name="addimagequery"></a><span data-ttu-id="07427-112">addImageQuery</span><span class="sxs-lookup"><span data-stu-id="07427-112">addImageQuery</span></span>
`@property(nonatomic, assign) BOOL addImageQuery;`

<span data-ttu-id="07427-113">イメージを取得するときに、 **IconUri** から提供されたイメージ URI に Windows がクエリ文字列を追加できるようにするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="07427-113">Determines whether to allow Windows to append a query string to the image URI supplied from **IconUri** when retrieving the image.</span></span> <span data-ttu-id="07427-114">クエリ文字列には、ユーザーのディスプレイの DPI、ハイコントラストの設定、およびユーザーの言語に基づいて最適なイメージを選択するのに役立つ情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="07427-114">The query string includes information that can help select the ideal image based on the DPI of the user's display, the high contrast setting, and the user's language.</span></span> <span data-ttu-id="07427-115">このクエリ文字列は、スケール、コントラスト設定、および言語を指定します。たとえば、 **IconUri** 値 "www.website.com/images/hello.png" は、"www.website.com/images/hello.png? ms-scale = 100&ms-contrast = standard&ms-lang = en-us" になります。</span><span class="sxs-lookup"><span data-stu-id="07427-115">This query string specifies scale, contrast setting, and language; for instance, an **IconUri** value of "www.website.com/images/hello.png" becomes "www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us".</span></span>

## <a name="constructors"></a><span data-ttu-id="07427-116">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="07427-116">Constructors</span></span>

### <a name="useractivityattributionwithiconuri"></a><span data-ttu-id="07427-117">userActivityAttributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="07427-117">userActivityAttributionWithIconUri</span></span>
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="07427-118">アイコン URI を使用して、このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="07427-118">Creates an instance of this class with an Icon URI.</span></span>

#### <a name="parameters"></a><span data-ttu-id="07427-119">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07427-119">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="07427-120">作成されたインスタンスに属するアイコン URI の文字列値。</span><span class="sxs-lookup"><span data-stu-id="07427-120">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="07427-121">戻り値</span><span class="sxs-lookup"><span data-stu-id="07427-121">Returns</span></span>
<span data-ttu-id="07427-122">アイコン uri で初期化された MCDUserActivityAttribution オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="07427-122">Returns an MCDUserActivityAttribution object initialized with an icon uri.</span></span>

### <a name="attributionwithiconuri"></a><span data-ttu-id="07427-123">attributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="07427-123">attributionWithIconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="07427-124">アイコン uri に対する属性を使用して、このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="07427-124">Creates an instance of this class with attribution to a icon uri.</span></span>

#### <a name="parameters"></a><span data-ttu-id="07427-125">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07427-125">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="07427-126">作成されたインスタンスに属するアイコン URI の文字列値。</span><span class="sxs-lookup"><span data-stu-id="07427-126">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="07427-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="07427-127">Returns</span></span>
<span data-ttu-id="07427-128">アイコンの uri を持つ MCDUserActivityAttribution オブジェクト属性を返します。</span><span class="sxs-lookup"><span data-stu-id="07427-128">Returns an MCDUserActivityAttribution object attributing with an icon uri.</span></span>