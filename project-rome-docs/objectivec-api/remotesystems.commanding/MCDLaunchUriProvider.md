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
# <a name="protocol-mcdlaunchuriprovider"></a>プロトコール `MCDLaunchUriProvider`

```
@protocol MCDLaunchUriProvider <NSObject>
```

このクラスは、アプリケーションの起動によって URI の処理を管理します。

## <a name="properties"></a>Properties 
### <a name="supportedurischemes"></a>supportedUriSchemes
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

サポートされている URI スキームを表す文字列の配列。

## <a name="methods"></a>メソッド

### <a name="onlaunchuriasync"></a>onLaunchUriAsync
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

このメソッドは、リモートデバイスがこのデバイスで URI を起動しようとしたときに呼び出されます。

#### <a name="parameters"></a>パラメーター 
* `uri` 起動する URI。
* `options` URI を起動するためのオプションのセット。 フォールバック URI は、設定可能なオプションの1つにすぎません。
* `completionBlock` 完了時に実行するコードブロック。