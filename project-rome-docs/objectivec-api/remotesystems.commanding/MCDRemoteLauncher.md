---
title: MCDRemoteLauncher
description: URI を使用してリモート デバイス上のアプリを起動するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: aa0211c1edc33e8a277c4954d94fbcbb6565c923
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907384"
---
# <a name="class-mcdremotelauncher"></a><span data-ttu-id="55df9-104">クラス `MCDRemoteLauncher`</span><span class="sxs-lookup"><span data-stu-id="55df9-104">class `MCDRemoteLauncher`</span></span> 

```
@interface MCDRemoteLauncher : NSObject
```  

<span data-ttu-id="55df9-105">URI を使用してリモート デバイス上のアプリを起動するために使用するクラスです。</span><span class="sxs-lookup"><span data-stu-id="55df9-105">A class used to launch an app on a remote device using a URI.</span></span>


## <a name="methods"></a><span data-ttu-id="55df9-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="55df9-106">Methods</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="55df9-107">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="55df9-107">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="55df9-108">指定されたリモート システムに対して URI を起動、 [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)します。</span><span class="sxs-lookup"><span data-stu-id="55df9-108">Launches a URI against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="55df9-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55df9-109">Parameters</span></span>
* <span data-ttu-id="55df9-110">`uri` これにより、アプリを起動するための URI。</span><span class="sxs-lookup"><span data-stu-id="55df9-110">`uri` The URI which will cause the launching of an app.</span></span>  <span data-ttu-id="55df9-111">ターゲットが Windows の場合は、対象となるアプリをスキームに基づいて選択するされます。</span><span class="sxs-lookup"><span data-stu-id="55df9-111">If the target is Windows, the target app will be chosen based on scheme.</span></span> <span data-ttu-id="55df9-112">ターゲットが Windows 以外の場合は、対象となるアプリを MCDRemoteSystemConnectionRequest に基づいて選択するされます。</span><span class="sxs-lookup"><span data-stu-id="55df9-112">If the target is non-Windows, the target app will be chosen based on the MCDRemoteSystemConnectionRequest.</span></span>

* <span data-ttu-id="55df9-113">`connection` どのリモート システムまたはアプリケーションへの接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="55df9-113">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="55df9-114">`completionBlock` 完了時に呼び出すブロックします。</span><span class="sxs-lookup"><span data-stu-id="55df9-114">`completionBlock` The block to invoke upon completion.</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="55df9-115">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="55df9-115">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="55df9-116">指定されたリモート システムに対してオプションを使用して URI を起動、 [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)します。</span><span class="sxs-lookup"><span data-stu-id="55df9-116">Launches a URI with options against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="55df9-117">パラメーター</span><span class="sxs-lookup"><span data-stu-id="55df9-117">Parameters</span></span>
* <span data-ttu-id="55df9-118">`uri` これにより、スキームに従って、アプリを起動するための URI。</span><span class="sxs-lookup"><span data-stu-id="55df9-118">`uri` The URI which will cause the launching of an app, according to its scheme.</span></span>
* <span data-ttu-id="55df9-119">`connection` どのリモート システムまたはアプリケーションへの接続を指定します。</span><span class="sxs-lookup"><span data-stu-id="55df9-119">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="55df9-120">`options` アプリの起動の仕様。</span><span class="sxs-lookup"><span data-stu-id="55df9-120">`options` The launch specifications for the app.</span></span>
* <span data-ttu-id="55df9-121">`completionBlock` 完了時に呼び出すブロックします。</span><span class="sxs-lookup"><span data-stu-id="55df9-121">`completionBlock` The block to invoke upon completion.</span></span>