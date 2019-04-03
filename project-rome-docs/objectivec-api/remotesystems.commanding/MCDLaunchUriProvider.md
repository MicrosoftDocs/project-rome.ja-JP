---
title: MCDLaunchUriProvider
description: ''
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 4cbfaa9fd1e88345f4ce35987508b061e479854e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907464"
---
# <a name="protocol-mcdlaunchuriprovider"></a><span data-ttu-id="b814b-103">プロトコル `MCDLaunchUriProvider`</span><span class="sxs-lookup"><span data-stu-id="b814b-103">protocol `MCDLaunchUriProvider`</span></span>

```
@protocol MCDLaunchUriProvider <NSObject>
```

<span data-ttu-id="b814b-104">このクラスは、アプリケーションの起動を通じて、URI の処理を管理します。</span><span class="sxs-lookup"><span data-stu-id="b814b-104">This class manages the handling of a URI through the launching of an application.</span></span>

## <a name="properties"></a><span data-ttu-id="b814b-105">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b814b-105">Properties</span></span> 
### <a name="supportedurischemes"></a><span data-ttu-id="b814b-106">supportedUriSchemes</span><span class="sxs-lookup"><span data-stu-id="b814b-106">supportedUriSchemes</span></span>
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

<span data-ttu-id="b814b-107">表す文字列の配列には、URI スキームがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b814b-107">An array of strings representing supported URI schemes.</span></span>

## <a name="methods"></a><span data-ttu-id="b814b-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="b814b-108">Methods</span></span>

### <a name="onlaunchuriasync"></a><span data-ttu-id="b814b-109">onLaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="b814b-109">onLaunchUriAsync</span></span>
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

<span data-ttu-id="b814b-110">リモート デバイスがこのデバイス上の URI を起動しようとした場合、このメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b814b-110">This method is called when a remote device attempts to launch a URI on this device.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b814b-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b814b-111">Parameters</span></span> 
* <span data-ttu-id="b814b-112">`uri` 起動する URI。</span><span class="sxs-lookup"><span data-stu-id="b814b-112">`uri` The URI to launch.</span></span>
* <span data-ttu-id="b814b-113">`options` URI を起動するためのオプションのセット。</span><span class="sxs-lookup"><span data-stu-id="b814b-113">`options` A set of options for launching the URI.</span></span> <span data-ttu-id="b814b-114">フォールバック URI は、設定できる有効なオプションの 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="b814b-114">The fallback URI is only one of the possible options that can be set.</span></span>
* <span data-ttu-id="b814b-115">`completionBlock` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="b814b-115">`completionBlock` The code block to execute upon completion.</span></span>