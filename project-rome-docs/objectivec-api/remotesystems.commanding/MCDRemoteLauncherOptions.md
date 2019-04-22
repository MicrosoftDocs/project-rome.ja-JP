---
title: MCDRemoteLauncherOptions
description: リモート起動機能のオプションを表すクラス。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 628bf1659dfb4ce50e20631622d8a78a322bb2f5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801264"
---
# <a name="class-mcdremotelauncheroptions"></a>クラス `MCDRemoteLauncherOptions` 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

リモート起動機能のオプションを表すクラス。

## <a name="properties"></a>プロパティ

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

Web アプリ URI を起動する場合の起動にフォールバックの URI は失敗します。

### <a name="preferredpackageids"></a>preferredPackageIds
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

一連の**NSString**この URI を使用して起動できるようにするアプリの Id を表すオブジェクト。 Windows のアプリ ID は、アプリのパッケージ ファミリ名になります。

## <a name="constructors"></a>コンストラクター

### <a name="optionswithfallbackuri"></a>optionsWithFallbackUri
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

作成し、このクラスの新しいインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター
* `fallbackUri` 

Web アプリ URI を起動する場合の起動にフォールバックの URI は失敗します。

* `preferredPackageIds` 

一連の**NSString**この URI を使用して起動できるようにするアプリの Id を表すオブジェクト。 Windows のアプリ ID は、アプリのパッケージ ファミリ名になります。

#### <a name="returns"></a>戻り値
返しますが、初期化された[MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md)成功した場合、それ以外の場合の nil します。

### <a name="initwithfallbackuri"></a>initWithFallbackUri
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

作成し、このクラスの新しいインスタンスを初期化します。

#### <a name="parameters"></a>パラメーター
* `fallbackUri` 

Web アプリ URI を起動する場合の起動にフォールバックの URI は失敗します。

* `preferredPackageIds` 

一連の**NSString**この URI を使用して起動できるようにするアプリの Id を表すオブジェクト。 Windows のアプリ ID は、アプリのパッケージ ファミリ名になります。

#### <a name="returns"></a>戻り値
返しますが、初期化された[MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md)成功した場合、それ以外の場合の nil します。