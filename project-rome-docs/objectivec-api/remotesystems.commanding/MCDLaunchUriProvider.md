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
# <a name="protocol-mcdlaunchuriprovider"></a>プロトコル `MCDLaunchUriProvider`

```
@protocol MCDLaunchUriProvider <NSObject>
```

このクラスは、アプリケーションの起動を通じて、URI の処理を管理します。

## <a name="properties"></a>プロパティ 
### <a name="supportedurischemes"></a>supportedUriSchemes
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

表す文字列の配列には、URI スキームがサポートされています。

## <a name="methods"></a>メソッド

### <a name="onlaunchuriasync"></a>onLaunchUriAsync
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

リモート デバイスがこのデバイス上の URI を起動しようとした場合、このメソッドが呼び出されます。

#### <a name="parameters"></a>パラメーター 
* `uri` 起動する URI。
* `options` URI を起動するためのオプションのセット。 フォールバック URI は、設定できる有効なオプションの 1 つだけです。
* `completionBlock` 完了時に実行するコード ブロックです。