---
title: MCDRemoteSystem
description: リモート システムを表すクラス。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5f0ab2108d4efa486b992bf7bc8c8847692623da
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801764"
---
# <a name="class-mcdremotesystem"></a>クラス `MCDRemoteSystem` 

```
@interface MCDRemoteSystem : NSObject
```  

リモート システムを表すクラス。

## <a name="properties"></a>プロパティ

### <a name="kind"></a>種類
`@property(nonatomic, readonly, nonnull) NSString* kind;`

このリモート システムのデバイスの種類。

### <a name="systemid"></a>systemId
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

このリモート システムの識別子。

### <a name="displayname"></a>displayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

リモート システムの名前。

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

このリモート システムの可用性の状態です。

> [!NOTE]
WNS プレゼンスは、Windows デバイスと通知の種類として WNS を使用している場合、アプリケーションの可用性をレポートに使用されます。  デバイスは使用可能な (Windows) と見なされる場合、または基になるアプリのいずれかのレポートの自分の存在「使用可能な」とマークされます RemoteSystem 利用可能な (iOS と Android)。 

### <a name="manufacturerdisplayname"></a>manufacturerDisplayName
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

リモート システムの製造元の名前。

### <a name="modeldisplayname"></a>modelDisplayName
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

リモート システムのモデル名。

### <a name="apps"></a>アプリ
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

このリモート システム上の接続で利用可能なアプリケーションの配列。

### <a name="platform"></a>プラットフォーム
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

リモート システムの使用状況を管理する MCDRemoteSystemPlatform します。