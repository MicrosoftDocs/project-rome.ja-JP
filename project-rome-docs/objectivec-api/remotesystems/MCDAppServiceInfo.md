---
title: MCDAppServiceInfo
description: このクラスには、リモート デバイスまたはアプリケーションに属している app service について説明します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5cb01d664a07653387b523eeec68ebd50bbc2798
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907114"
---
# <a name="class-mcdappserviceinfo"></a>クラス `MCDAppServiceInfo` 

```
@interface MCDAppServiceInfo : NSObject<NSCopying>
```  

このクラスには、リモート デバイスまたはアプリケーションに属している app service について説明します。

## <a name="properties"></a>プロパティ

### <a name="name"></a>name
`@property(nonatomic, readonly, nullable) NSString* name;`

記述されている app service の名前。

### <a name="packageid"></a>PackageId
`@property(nonatomic, readonly, nullable) NSString* packageId;`

記述されている app service のパッケージ ID。

## <a name="constructors"></a>コンストラクター

### <a name="infowithname"></a>infoWithName
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name;`

情報と app service の名前を持つクラスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `name` 

記述されている app service の名前。

#### <a name="returns"></a>戻り値
指定された名前を含む MCDAppServiceInfo オブジェクトを返します。

### <a name="initwithname"></a>initWithName
`- (nullable instancetype)initWithName:(nonnull NSString*)name;`

App service の名前のクラスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `name` 

記述されている app service の名前。

#### <a name="returns"></a>戻り値
指定された名前を使用して初期化 MCDAppServiceInfo オブジェクトを返します。

### <a name="infowithname"></a>infoWithName
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

情報と app service の名前を持つクラスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `name` 

記述されている app service の名前。

* `packageId` 

記述されている app service のパッケージ ID。

#### <a name="returns"></a>戻り値
指定された名前を含む MCDAppServiceInfo オブジェクトを返します。

### <a name="initwithname"></a>initWithName
`- (nullable instancetype)initWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

App service の名前のクラスを初期化します。

#### <a name="parameters"></a>パラメーター 
* `name` 

記述されている app service の名前。

* `packageId` 

記述されている app service のパッケージ ID。

#### <a name="returns"></a>戻り値
指定された名前を使用して初期化 MCDAppServiceInfo オブジェクトを返します。
