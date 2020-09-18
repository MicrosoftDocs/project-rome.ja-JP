---
title: MCDRemoteSystem
description: MCDRemoteSystem クラスとそのプロパティについて説明します。 このクラスは、リモートシステムを表すために使用されます。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: e211de33117f48cc221152cf40645015693dcddc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760996"
---
# <a name="class-mcdremotesystem"></a>講義 `MCDRemoteSystem` 

```
@interface MCDRemoteSystem : NSObject
```  

リモートシステムを表すクラス。

## <a name="properties"></a>Properties

### <a name="kind"></a>kind
`@property(nonatomic, readonly, nonnull) NSString* kind;`

このリモートシステムのデバイスの種類。

### <a name="systemid"></a>systemId
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

このリモートシステムの識別子。

### <a name="displayname"></a>displayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

指定されたリモートシステムの名前。

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

このリモートシステムの可用性の状態。

> [!NOTE]
WNS プレゼンスは、通知の種類として WNS を使用する Windows デバイスとアプリの可用性をレポートするために使用されます。  デバイスが使用可能と見なされた場合 (Windows の場合)、または基になるアプリの1つが利用可能として表示される場合 (iOS と Android)、RemoteSystem は "利用可能" とマークされます。 

### <a name="manufacturerdisplayname"></a>manufacturerDisplayName
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

指定されたリモートシステムの製造元名。

### <a name="modeldisplayname"></a>modelDisplayName
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

指定されたリモートシステムのモデル名。

### <a name="apps"></a>アプリ
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

このリモートシステム上の接続に使用できるアプリケーションの配列。

### <a name="platform"></a>platform
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

リモートシステムアクティビティを管理する MCDRemoteSystemPlatform。