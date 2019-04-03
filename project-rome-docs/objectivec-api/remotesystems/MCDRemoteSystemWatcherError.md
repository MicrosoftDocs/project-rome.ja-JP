---
title: MCDRemoteSystemWatcherError
description: エラーの説明は、検出プロセス中に、リモート システムの監視オブジェクトで発生した値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 3f65614396377b154b2a37493b8271ac54afb6fd
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907704"
---
# <a name="enum-mcdremotesystemwatchererror"></a><span data-ttu-id="f73d4-104">列挙型 `MCDRemoteSystemWatcherError`</span><span class="sxs-lookup"><span data-stu-id="f73d4-104">enum `MCDRemoteSystemWatcherError`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemWatcherError)
```  
 <span data-ttu-id="f73d4-105">エラーの説明は、検出プロセス中に、リモート システムの監視オブジェクトで発生した値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f73d4-105">Contains values that the describe an error encountered by a remote system watcher object during the discovery process.</span></span>

## <a name="fields"></a><span data-ttu-id="f73d4-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="f73d4-106">Fields</span></span>

| <span data-ttu-id="f73d4-107">名前</span><span class="sxs-lookup"><span data-stu-id="f73d4-107">Name</span></span>                              | <span data-ttu-id="f73d4-108">値</span><span class="sxs-lookup"><span data-stu-id="f73d4-108">Value</span></span> | <span data-ttu-id="f73d4-109">説明</span><span class="sxs-lookup"><span data-stu-id="f73d4-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="f73d4-110">MCDRemoteSystemWatcherErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="f73d4-110">MCDRemoteSystemWatcherErrorUnknown</span></span> | <span data-ttu-id="f73d4-111">0</span><span class="sxs-lookup"><span data-stu-id="f73d4-111">0</span></span> | <span data-ttu-id="f73d4-112">ウォッチャーには、不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f73d4-112">The watcher encountered an unknown error.</span></span> |
| <span data-ttu-id="f73d4-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span><span class="sxs-lookup"><span data-stu-id="f73d4-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span></span> | <span data-ttu-id="f73d4-114">1</span><span class="sxs-lookup"><span data-stu-id="f73d4-114">1</span></span> | <span data-ttu-id="f73d4-115">インターネット接続が失われたため、エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f73d4-115">The error occurred because the Internet connection was lost.</span></span> |
| <span data-ttu-id="f73d4-116">MCDRemoteSystemWatcherErrorAuthenticationError</span><span class="sxs-lookup"><span data-stu-id="f73d4-116">MCDRemoteSystemWatcherErrorAuthenticationError</span></span> | <span data-ttu-id="f73d4-117">2</span><span class="sxs-lookup"><span data-stu-id="f73d4-117">2</span></span> | <span data-ttu-id="f73d4-118">検出を実行するために使用されている ConnectedDevicesAccount を認証されていないため、エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f73d4-118">The error occurred because a ConnectedDevicesAccount being used to run the discovery could not be authenticated.</span></span> | 
