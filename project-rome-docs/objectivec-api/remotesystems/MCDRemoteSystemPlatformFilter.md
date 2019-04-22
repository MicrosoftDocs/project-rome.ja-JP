---
title: MCDRemoteSystemPlatformFilter
description: リモート システムが実行されている OS プラットフォームに基づくフィルター処理するために使用するクラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 1b82d7b3a1626489a83196bf949567b3ce7b94f0
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801224"
---
# <a name="class-mcdremotesystemplatformfilter"></a>クラス `MCDRemoteSystemPlatformFilter` 

```
@interface MCDRemoteSystemPlatformFilter : NSObject<MCDRemoteSystemFilter> 
```  

リモート システムが実行されている OS プラットフォームに基づくフィルター処理するために使用するクラスです。

## <a name="properties"></a>プロパティ

### <a name="platform"></a>プラットフォーム
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

フィルター処理するためのプラットフォームを示す MCDRemoteSystemPlatform 値。

## <a name="constructors"></a>コンストラクター

### <a name="filterwithplatform"></a>filterWithPlatform
`+ (nullable instancetype)filterWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a>パラメーター 
* `platform` 

フィルター処理するためのプラットフォームを示す MCDRemoteSystemPlatform 値。

#### <a name="returns"></a>戻り値
プラットフォームでフィルター処理された MCDRemoteSystemPlatformFilter オブジェクトを返します。

### <a name="initwithplatform"></a>initWithPlatform
`- (nullable instancetype)initWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a>パラメーター 
* `platform` 

フィルター処理するためのプラットフォームを示す MCDRemoteSystemPlatform 値。

#### <a name="returns"></a>戻り値
プラットフォームでフィルターを使用した初期化 MCDRemoteSystemPlatformFilter オブジェクトを返します。