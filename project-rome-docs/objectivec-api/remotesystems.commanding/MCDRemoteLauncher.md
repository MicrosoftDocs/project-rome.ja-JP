---
title: MCDRemoteLauncher
description: MCDRemoteLauncher クラスについて説明します。 このクラスは、URI を使用してリモートデバイスでアプリを起動するために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: e5231897241e54c44b4f3fb299adf68af396cac9
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760746"
---
# <a name="class-mcdremotelauncher"></a><span data-ttu-id="374ab-105">講義 `MCDRemoteLauncher`</span><span class="sxs-lookup"><span data-stu-id="374ab-105">class `MCDRemoteLauncher`</span></span> 

```
@interface MCDRemoteLauncher : NSObject
```  

<span data-ttu-id="374ab-106">URI を使用してリモートデバイスでアプリを起動するために使用されるクラス。</span><span class="sxs-lookup"><span data-stu-id="374ab-106">A class used to launch an app on a remote device using a URI.</span></span>


## <a name="methods"></a><span data-ttu-id="374ab-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="374ab-107">Methods</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="374ab-108">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="374ab-108">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="374ab-109">[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)で指定されたリモートシステムに対して URI を起動します。</span><span class="sxs-lookup"><span data-stu-id="374ab-109">Launches a URI against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="374ab-110">パラメーター</span><span class="sxs-lookup"><span data-stu-id="374ab-110">Parameters</span></span>
* <span data-ttu-id="374ab-111">`uri` アプリの起動の原因となる URI。</span><span class="sxs-lookup"><span data-stu-id="374ab-111">`uri` The URI which will cause the launching of an app.</span></span>  <span data-ttu-id="374ab-112">ターゲットが Windows の場合は、スキームに基づいてターゲットアプリが選択されます。</span><span class="sxs-lookup"><span data-stu-id="374ab-112">If the target is Windows, the target app will be chosen based on scheme.</span></span> <span data-ttu-id="374ab-113">ターゲットが Windows 以外の場合は、MCDRemoteSystemConnectionRequest に基づいてターゲットアプリが選択されます。</span><span class="sxs-lookup"><span data-stu-id="374ab-113">If the target is non-Windows, the target app will be chosen based on the MCDRemoteSystemConnectionRequest.</span></span>

* <span data-ttu-id="374ab-114">`connection` 接続先のリモートシステムまたはアプリケーションを指定します。</span><span class="sxs-lookup"><span data-stu-id="374ab-114">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="374ab-115">`completionBlock` 完了時に呼び出すブロック。</span><span class="sxs-lookup"><span data-stu-id="374ab-115">`completionBlock` The block to invoke upon completion.</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="374ab-116">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="374ab-116">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="374ab-117">[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)で指定されたリモートシステムに対するオプションを含む URI を起動します。</span><span class="sxs-lookup"><span data-stu-id="374ab-117">Launches a URI with options against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="374ab-118">パラメーター</span><span class="sxs-lookup"><span data-stu-id="374ab-118">Parameters</span></span>
* <span data-ttu-id="374ab-119">`uri` スキームに従ってアプリの起動を引き起こす URI。</span><span class="sxs-lookup"><span data-stu-id="374ab-119">`uri` The URI which will cause the launching of an app, according to its scheme.</span></span>
* <span data-ttu-id="374ab-120">`connection` 接続先のリモートシステムまたはアプリケーションを指定します。</span><span class="sxs-lookup"><span data-stu-id="374ab-120">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="374ab-121">`options` アプリの起動仕様。</span><span class="sxs-lookup"><span data-stu-id="374ab-121">`options` The launch specifications for the app.</span></span>
* <span data-ttu-id="374ab-122">`completionBlock` 完了時に呼び出すブロック。</span><span class="sxs-lookup"><span data-stu-id="374ab-122">`completionBlock` The block to invoke upon completion.</span></span>