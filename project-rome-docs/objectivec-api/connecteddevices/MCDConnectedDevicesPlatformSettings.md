---
title: MCDConnectedDevicesPlatformSettings
description: 特定の場所に格納されるデバイス プラットフォームの接続の設定を許可するインターフェイスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 9753553cefbbeaff598550687b8dfa5100d2006e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908894"
---
# <a name="class-mcdconnecteddevicesplatformsettings"></a>クラス `MCDConnectedDevicesPlatformSettings` 

```
@interface MCDConnectedDevicesPlatformSettings : NSObject
```  
特定の場所に格納されるデバイス プラットフォームの接続の設定を許可するインターフェイスです。  

## <a name="properties"></a>プロパティ

### <a name="storagepath"></a>StoragePath
`@property (nonatomic, readwrite, nonnull) NSString* storagePath;`

接続されているデバイス プラットフォームの設定の格納場所へのパス。