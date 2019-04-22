---
title: MCDRemoteSystemWatcherError
description: エラーの説明は、検出プロセス中に、リモート システムの監視オブジェクトで発生した値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 3f65614396377b154b2a37493b8271ac54afb6fd
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801724"
---
# <a name="enum-mcdremotesystemwatchererror"></a><span data-ttu-id="c0344-104">列挙型 `MCDRemoteSystemWatcherError`</span><span class="sxs-lookup"><span data-stu-id="c0344-104">enum `MCDRemoteSystemWatcherError`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemWatcherError)
```  
 <span data-ttu-id="c0344-105">エラーの説明は、検出プロセス中に、リモート システムの監視オブジェクトで発生した値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c0344-105">Contains values that the describe an error encountered by a remote system watcher object during the discovery process.</span></span>

## <a name="fields"></a><span data-ttu-id="c0344-106">フィールド</span><span class="sxs-lookup"><span data-stu-id="c0344-106">Fields</span></span>

| <span data-ttu-id="c0344-107">名前</span><span class="sxs-lookup"><span data-stu-id="c0344-107">Name</span></span>                              | <span data-ttu-id="c0344-108">値</span><span class="sxs-lookup"><span data-stu-id="c0344-108">Value</span></span> | <span data-ttu-id="c0344-109">説明</span><span class="sxs-lookup"><span data-stu-id="c0344-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="c0344-110">MCDRemoteSystemWatcherErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="c0344-110">MCDRemoteSystemWatcherErrorUnknown</span></span> | <span data-ttu-id="c0344-111">0</span><span class="sxs-lookup"><span data-stu-id="c0344-111">0</span></span> | <span data-ttu-id="c0344-112">ウォッチャーには、不明なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c0344-112">The watcher encountered an unknown error.</span></span> |
| <span data-ttu-id="c0344-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span><span class="sxs-lookup"><span data-stu-id="c0344-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span></span> | <span data-ttu-id="c0344-114">1</span><span class="sxs-lookup"><span data-stu-id="c0344-114">1</span></span> | <span data-ttu-id="c0344-115">インターネット接続が失われたため、エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c0344-115">The error occurred because the Internet connection was lost.</span></span> |
| <span data-ttu-id="c0344-116">MCDRemoteSystemWatcherErrorAuthenticationError</span><span class="sxs-lookup"><span data-stu-id="c0344-116">MCDRemoteSystemWatcherErrorAuthenticationError</span></span> | <span data-ttu-id="c0344-117">2</span><span class="sxs-lookup"><span data-stu-id="c0344-117">2</span></span> | <span data-ttu-id="c0344-118">検出を実行するために使用されている ConnectedDevicesAccount を認証されていないため、エラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c0344-118">The error occurred because a ConnectedDevicesAccount being used to run the discovery could not be authenticated.</span></span> | 
