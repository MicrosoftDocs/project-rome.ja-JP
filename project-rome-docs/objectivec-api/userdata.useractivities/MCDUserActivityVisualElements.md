---
title: MCDUserActivityVisualElements
description: このクラスには、説明、アイコンを MCDUserActivity を"details"タイルを表示するなど、visual 情報が含まれています。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: c969b8a52bc6d2a22fd0a00808f9bb374c63cd8a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801064"
---
# <a name="class-mcduseractivityvisualelements"></a><span data-ttu-id="e9cfb-104">クラス `MCDUserActivityVisualElements`</span><span class="sxs-lookup"><span data-stu-id="e9cfb-104">class `MCDUserActivityVisualElements`</span></span>

```
@interface MCDUserActivityVisualElements : NSObject 
```

<span data-ttu-id="e9cfb-105">このクラスには、説明、アイコンを MCDUserActivity を"details"タイルを表示するなど、visual 情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e9cfb-105">This class contains the visual information, such as the description and icon, that can be shown in the "details" tile for a MCDUserActivity.</span></span>

## <a name="properties"></a><span data-ttu-id="e9cfb-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e9cfb-106">Properties</span></span>

### <a name="displaytext"></a><span data-ttu-id="e9cfb-107">displayText</span><span class="sxs-lookup"><span data-stu-id="e9cfb-107">displayText</span></span>
`@property(nonatomic, copy, nonnull) NSString* displayText;`

<span data-ttu-id="e9cfb-108">アクティビティの詳細」のタイルの表示テキスト。</span><span class="sxs-lookup"><span data-stu-id="e9cfb-108">The display text for the "details" tile of the activity.</span></span>

### <a name="descriptiontext"></a><span data-ttu-id="e9cfb-109">descriptionText</span><span class="sxs-lookup"><span data-stu-id="e9cfb-109">descriptionText</span></span>
`@property(nonatomic, copy, nullable) NSString* descriptionText;`

<span data-ttu-id="e9cfb-110">アクティビティの詳細」のタイルの説明テキスト。</span><span class="sxs-lookup"><span data-stu-id="e9cfb-110">The description text for the "details" tile of the activity.</span></span>

### <a name="backgroundcolor"></a><span data-ttu-id="e9cfb-111">BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="e9cfb-111">backgroundColor</span></span>
`@property(nonatomic, copy, nullable) SKColor* backgroundColor;`

<span data-ttu-id="e9cfb-112">アクティビティのタイルの背景色。</span><span class="sxs-lookup"><span data-stu-id="e9cfb-112">The background color for the tile of the activity.</span></span>

### <a name="attribution"></a><span data-ttu-id="e9cfb-113">属性</span><span class="sxs-lookup"><span data-stu-id="e9cfb-113">attribution</span></span>
`@property(nonatomic, retain, nullable) MCDUserActivityAttribution* attribution;`

<span data-ttu-id="e9cfb-114">アクティビティに関するグラフィック情報。</span><span class="sxs-lookup"><span data-stu-id="e9cfb-114">The graphical information about the activity.</span></span>

### <a name="adaptivecardjson"></a><span data-ttu-id="e9cfb-115">adaptiveCardJson</span><span class="sxs-lookup"><span data-stu-id="e9cfb-115">adaptiveCardJson</span></span>
`@property(nonatomic, copy, nullable) NSString* adaptiveCardJson;`

<span data-ttu-id="e9cfb-116">アクティビティの詳細」のタイルのコンテンツのテキスト。</span><span class="sxs-lookup"><span data-stu-id="e9cfb-116">The content text for the "details" tile of the activity.</span></span>

### <a name="attributiondisplaytext"></a><span data-ttu-id="e9cfb-117">attributionDisplayText</span><span class="sxs-lookup"><span data-stu-id="e9cfb-117">attributionDisplayText</span></span>
`@property(nonatomic, copy, nullable) NSString* attributionDisplayText;`

<span data-ttu-id="e9cfb-118">アクティビティのカードの上部にあるバナーに表示されるテキスト。</span><span class="sxs-lookup"><span data-stu-id="e9cfb-118">The text that is shown in the top banner of the activity card.</span></span>