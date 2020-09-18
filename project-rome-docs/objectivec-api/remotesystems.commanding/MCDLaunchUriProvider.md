---
title: MCDLaunchUriProvider
description: MCDLaunchUriProvider プロトコルについて説明します。 このプロトコルは、アプリケーションを起動することによって URI の処理を管理するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 3339f9b5c8ab14dddf519618795c4150b69dfe3e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760756"
---
# <a name="protocol-mcdlaunchuriprovider"></a><span data-ttu-id="4b07a-105">プロトコール `MCDLaunchUriProvider`</span><span class="sxs-lookup"><span data-stu-id="4b07a-105">protocol `MCDLaunchUriProvider`</span></span>

```
@protocol MCDLaunchUriProvider <NSObject>
```

<span data-ttu-id="4b07a-106">このクラスは、アプリケーションの起動によって URI の処理を管理します。</span><span class="sxs-lookup"><span data-stu-id="4b07a-106">This class manages the handling of a URI through the launching of an application.</span></span>

## <a name="properties"></a><span data-ttu-id="4b07a-107">Properties</span><span class="sxs-lookup"><span data-stu-id="4b07a-107">Properties</span></span> 
### <a name="supportedurischemes"></a><span data-ttu-id="4b07a-108">supportedUriSchemes</span><span class="sxs-lookup"><span data-stu-id="4b07a-108">supportedUriSchemes</span></span>
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

<span data-ttu-id="4b07a-109">サポートされている URI スキームを表す文字列の配列。</span><span class="sxs-lookup"><span data-stu-id="4b07a-109">An array of strings representing supported URI schemes.</span></span>

## <a name="methods"></a><span data-ttu-id="4b07a-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="4b07a-110">Methods</span></span>

### <a name="onlaunchuriasync"></a><span data-ttu-id="4b07a-111">onLaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="4b07a-111">onLaunchUriAsync</span></span>
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

<span data-ttu-id="4b07a-112">このメソッドは、リモートデバイスがこのデバイスで URI を起動しようとしたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4b07a-112">This method is called when a remote device attempts to launch a URI on this device.</span></span>

#### <a name="parameters"></a><span data-ttu-id="4b07a-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4b07a-113">Parameters</span></span> 
* <span data-ttu-id="4b07a-114">`uri` 起動する URI。</span><span class="sxs-lookup"><span data-stu-id="4b07a-114">`uri` The URI to launch.</span></span>
* <span data-ttu-id="4b07a-115">`options` URI を起動するためのオプションのセット。</span><span class="sxs-lookup"><span data-stu-id="4b07a-115">`options` A set of options for launching the URI.</span></span> <span data-ttu-id="4b07a-116">フォールバック URI は、設定可能なオプションの1つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="4b07a-116">The fallback URI is only one of the possible options that can be set.</span></span>
* <span data-ttu-id="4b07a-117">`completionBlock` 完了時に実行するコードブロック。</span><span class="sxs-lookup"><span data-stu-id="4b07a-117">`completionBlock` The code block to execute upon completion.</span></span>