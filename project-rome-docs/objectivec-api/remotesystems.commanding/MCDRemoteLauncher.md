---
title: MCDRemoteLauncher
description: URI を使用してリモート デバイス上のアプリを起動するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: aa0211c1edc33e8a277c4954d94fbcbb6565c923
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907384"
---
# <a name="class-mcdremotelauncher"></a>クラス `MCDRemoteLauncher` 

```
@interface MCDRemoteLauncher : NSObject
```  

URI を使用してリモート デバイス上のアプリを起動するために使用するクラスです。


## <a name="methods"></a>メソッド

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

指定されたリモート システムに対して URI を起動、 [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)します。

#### <a name="parameters"></a>パラメーター
* `uri` これにより、アプリを起動するための URI。  ターゲットが Windows の場合は、対象となるアプリをスキームに基づいて選択するされます。 ターゲットが Windows 以外の場合は、対象となるアプリを MCDRemoteSystemConnectionRequest に基づいて選択するされます。

* `connection` どのリモート システムまたはアプリケーションへの接続を指定します。
* `completionBlock` 完了時に呼び出すブロックします。

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

指定されたリモート システムに対してオプションを使用して URI を起動、 [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)します。

#### <a name="parameters"></a>パラメーター
* `uri` これにより、スキームに従って、アプリを起動するための URI。
* `connection` どのリモート システムまたはアプリケーションへの接続を指定します。
* `options` アプリの起動の仕様。
* `completionBlock` 完了時に呼び出すブロックします。