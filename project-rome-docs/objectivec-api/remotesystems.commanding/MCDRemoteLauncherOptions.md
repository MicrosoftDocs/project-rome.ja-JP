---
title: MCDRemoteLauncherOptions
description: MCDRemoteLauncherOptions クラスについて説明します。 このクラスは、リモート起動機能のオプションを表します。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 2e698ad71282e44d1447e19085598139b67f9270
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760736"
---
# <a name="class-mcdremotelauncheroptions"></a>講義 `MCDRemoteLauncherOptions` 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

リモート起動機能のオプションを表すクラス。

## <a name="properties"></a>Properties

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

アプリの起動 URI が失敗した場合に web で起動するフォールバック URI。

### <a name="preferredpackageids"></a>Preferredのパッケージ
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

この URI で起動できるアプリの Id を表す **nsstring** オブジェクトのリスト。 Windows アプリの場合、ID はアプリのパッケージファミリ名になります。

## <a name="constructors"></a>コンストラクター

### <a name="optionswithfallbackuri"></a>オプション Withfallbackuri
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

このクラスの新しいインスタンスを作成して初期化します。

#### <a name="parameters"></a>パラメーター
* `fallbackUri` 

アプリの起動 URI が失敗した場合に web で起動するフォールバック URI。

* `preferredPackageIds` 

この URI で起動できるアプリの Id を表す **nsstring** オブジェクトのリスト。 Windows アプリの場合、ID はアプリのパッケージファミリ名になります。

#### <a name="returns"></a>戻り値
成功した場合は初期化された [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) を返し、それ以外の場合は nil を返します。

### <a name="initwithfallbackuri"></a>initWithFallbackUri
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

このクラスの新しいインスタンスを作成して初期化します。

#### <a name="parameters"></a>パラメーター
* `fallbackUri` 

アプリの起動 URI が失敗した場合に web で起動するフォールバック URI。

* `preferredPackageIds` 

この URI で起動できるアプリの Id を表す **nsstring** オブジェクトのリスト。 Windows アプリの場合、ID はアプリのパッケージファミリ名になります。

#### <a name="returns"></a>戻り値
成功した場合は初期化された [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) を返し、それ以外の場合は nil を返します。