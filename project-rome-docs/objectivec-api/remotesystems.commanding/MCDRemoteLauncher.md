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
# <a name="class-mcdremotelauncher"></a>講義 `MCDRemoteLauncher` 

```
@interface MCDRemoteLauncher : NSObject
```  

URI を使用してリモートデバイスでアプリを起動するために使用されるクラス。


## <a name="methods"></a>メソッド

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)で指定されたリモートシステムに対して URI を起動します。

#### <a name="parameters"></a>パラメーター
* `uri` アプリの起動の原因となる URI。  ターゲットが Windows の場合は、スキームに基づいてターゲットアプリが選択されます。 ターゲットが Windows 以外の場合は、MCDRemoteSystemConnectionRequest に基づいてターゲットアプリが選択されます。

* `connection` 接続先のリモートシステムまたはアプリケーションを指定します。
* `completionBlock` 完了時に呼び出すブロック。

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

[MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md)で指定されたリモートシステムに対するオプションを含む URI を起動します。

#### <a name="parameters"></a>パラメーター
* `uri` スキームに従ってアプリの起動を引き起こす URI。
* `connection` 接続先のリモートシステムまたはアプリケーションを指定します。
* `options` アプリの起動仕様。
* `completionBlock` 完了時に呼び出すブロック。