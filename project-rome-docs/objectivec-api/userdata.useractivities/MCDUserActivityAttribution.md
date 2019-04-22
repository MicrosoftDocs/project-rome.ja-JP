---
title: MCDUserActivityAttribution
description: このクラスは、ユーザーの利用状況のグラフィカル要素を管理します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 94ae2f5afef24a1f4e320014ac930d67b657b0d7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801544"
---
# <a name="class-mcduseractivityattribution"></a><span data-ttu-id="ecbf9-104">クラス `MCDUserActivityAttribution`</span><span class="sxs-lookup"><span data-stu-id="ecbf9-104">class `MCDUserActivityAttribution`</span></span>

```
@interface MCDUserActivityAttribution : NSObject
```

<span data-ttu-id="ecbf9-105">このクラスは、ユーザーの利用状況のグラフィカル要素を管理します。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-105">This class manages the graphical elements of a user activity.</span></span>

## <a name="properties"></a><span data-ttu-id="ecbf9-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ecbf9-106">Properties</span></span>

### <a name="iconuri"></a><span data-ttu-id="ecbf9-107">iconUri</span><span class="sxs-lookup"><span data-stu-id="ecbf9-107">iconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="ecbf9-108">アイコン イメージの URI。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-108">The URI for the icon image.</span></span>

### <a name="alternatetext"></a><span data-ttu-id="ecbf9-109">AlternateText</span><span class="sxs-lookup"><span data-stu-id="ecbf9-109">alternateText</span></span>
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

<span data-ttu-id="ecbf9-110">(スクリーン リーダーで使用する) のアイコンの画像を説明するテキスト。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-110">The text that describes the icon image (for use with screen readers).</span></span>

### <a name="addimagequery"></a><span data-ttu-id="ecbf9-111">addImageQuery</span><span class="sxs-lookup"><span data-stu-id="ecbf9-111">addImageQuery</span></span>
`@property(nonatomic, assign) BOOL addImageQuery;`

<span data-ttu-id="ecbf9-112">Windows イメージから指定された URI にクエリ文字列を追加するを許可するかどうかを判断します**IconUri**イメージを取得するときにします。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-112">Determines whether to allow Windows to append a query string to the image URI supplied from **IconUri** when retrieving the image.</span></span> <span data-ttu-id="ecbf9-113">クエリ文字列には、ユーザーの表示、ハイ コントラスト設定、およびユーザーの言語の DPI に基づく最適なイメージを選択するのに役立つ情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-113">The query string includes information that can help select the ideal image based on the DPI of the user's display, the high contrast setting, and the user's language.</span></span> <span data-ttu-id="ecbf9-114">このクエリ文字列は、スケール、コントラスト設定、および言語を指定します。たとえば、 **IconUri** "www.website.com/images/hello.png"の値になります"www.website.com/images/hello.png?ms-scale=100 & ms コントラスト = 標準 & ms lang = en-米国"。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-114">This query string specifies scale, contrast setting, and language; for instance, an **IconUri** value of "www.website.com/images/hello.png" becomes "www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us".</span></span>

## <a name="constructors"></a><span data-ttu-id="ecbf9-115">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="ecbf9-115">Constructors</span></span>

### <a name="useractivityattributionwithiconuri"></a><span data-ttu-id="ecbf9-116">userActivityAttributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="ecbf9-116">userActivityAttributionWithIconUri</span></span>
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="ecbf9-117">アイコンの URI をこのクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-117">Creates an instance of this class with an Icon URI.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ecbf9-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ecbf9-118">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="ecbf9-119">作成されたインスタンスに属している、アイコンの URI の文字列値。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-119">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="ecbf9-120">戻り値</span><span class="sxs-lookup"><span data-stu-id="ecbf9-120">Returns</span></span>
<span data-ttu-id="ecbf9-121">アイコンの uri を使用して初期化 MCDUserActivityAttribution オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-121">Returns an MCDUserActivityAttribution object initialized with an icon uri.</span></span>

### <a name="attributionwithiconuri"></a><span data-ttu-id="ecbf9-122">attributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="ecbf9-122">attributionWithIconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="ecbf9-123">アイコンの uri への帰属をこのクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-123">Creates an instance of this class with attribution to a icon uri.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ecbf9-124">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ecbf9-124">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="ecbf9-125">作成されたインスタンスに属している、アイコンの URI の文字列値。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-125">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="ecbf9-126">戻り値</span><span class="sxs-lookup"><span data-stu-id="ecbf9-126">Returns</span></span>
<span data-ttu-id="ecbf9-127">MCDUserActivityAttribution オブジェクト属性とアイコンの uri を返します。</span><span class="sxs-lookup"><span data-stu-id="ecbf9-127">Returns an MCDUserActivityAttribution object attributing with an icon uri.</span></span>