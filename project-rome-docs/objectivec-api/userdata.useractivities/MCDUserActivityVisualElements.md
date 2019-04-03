---
title: MCDUserActivityVisualElements
description: このクラスには、説明、アイコンを MCDUserActivity を"details"タイルを表示するなど、visual 情報が含まれています。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: c969b8a52bc6d2a22fd0a00808f9bb374c63cd8a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907414"
---
# <a name="class-mcduseractivityvisualelements"></a><span data-ttu-id="0c745-104">クラス `MCDUserActivityVisualElements`</span><span class="sxs-lookup"><span data-stu-id="0c745-104">class `MCDUserActivityVisualElements`</span></span>

```
@interface MCDUserActivityVisualElements : NSObject 
```

<span data-ttu-id="0c745-105">このクラスには、説明、アイコンを MCDUserActivity を"details"タイルを表示するなど、visual 情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c745-105">This class contains the visual information, such as the description and icon, that can be shown in the "details" tile for a MCDUserActivity.</span></span>

## <a name="properties"></a><span data-ttu-id="0c745-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0c745-106">Properties</span></span>

### <a name="displaytext"></a><span data-ttu-id="0c745-107">displayText</span><span class="sxs-lookup"><span data-stu-id="0c745-107">displayText</span></span>
`@property(nonatomic, copy, nonnull) NSString* displayText;`

<span data-ttu-id="0c745-108">アクティビティの詳細」のタイルの表示テキスト。</span><span class="sxs-lookup"><span data-stu-id="0c745-108">The display text for the "details" tile of the activity.</span></span>

### <a name="descriptiontext"></a><span data-ttu-id="0c745-109">descriptionText</span><span class="sxs-lookup"><span data-stu-id="0c745-109">descriptionText</span></span>
`@property(nonatomic, copy, nullable) NSString* descriptionText;`

<span data-ttu-id="0c745-110">アクティビティの詳細」のタイルの説明テキスト。</span><span class="sxs-lookup"><span data-stu-id="0c745-110">The description text for the "details" tile of the activity.</span></span>

### <a name="backgroundcolor"></a><span data-ttu-id="0c745-111">BackgroundColor</span><span class="sxs-lookup"><span data-stu-id="0c745-111">backgroundColor</span></span>
`@property(nonatomic, copy, nullable) SKColor* backgroundColor;`

<span data-ttu-id="0c745-112">アクティビティのタイルの背景色。</span><span class="sxs-lookup"><span data-stu-id="0c745-112">The background color for the tile of the activity.</span></span>

### <a name="attribution"></a><span data-ttu-id="0c745-113">属性</span><span class="sxs-lookup"><span data-stu-id="0c745-113">attribution</span></span>
`@property(nonatomic, retain, nullable) MCDUserActivityAttribution* attribution;`

<span data-ttu-id="0c745-114">アクティビティに関するグラフィック情報。</span><span class="sxs-lookup"><span data-stu-id="0c745-114">The graphical information about the activity.</span></span>

### <a name="adaptivecardjson"></a><span data-ttu-id="0c745-115">adaptiveCardJson</span><span class="sxs-lookup"><span data-stu-id="0c745-115">adaptiveCardJson</span></span>
`@property(nonatomic, copy, nullable) NSString* adaptiveCardJson;`

<span data-ttu-id="0c745-116">アクティビティの詳細」のタイルのコンテンツのテキスト。</span><span class="sxs-lookup"><span data-stu-id="0c745-116">The content text for the "details" tile of the activity.</span></span>

### <a name="attributiondisplaytext"></a><span data-ttu-id="0c745-117">attributionDisplayText</span><span class="sxs-lookup"><span data-stu-id="0c745-117">attributionDisplayText</span></span>
`@property(nonatomic, copy, nullable) NSString* attributionDisplayText;`

<span data-ttu-id="0c745-118">アクティビティのカードの上部にあるバナーに表示されるテキスト。</span><span class="sxs-lookup"><span data-stu-id="0c745-118">The text that is shown in the top banner of the activity card.</span></span>