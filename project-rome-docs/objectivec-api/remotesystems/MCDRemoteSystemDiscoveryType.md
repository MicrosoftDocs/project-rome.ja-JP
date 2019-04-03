---
title: MCDRemoteSystemDiscoveryType
description: 含むリモート システムを記述する値が検出されることができます。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: dc94b92311cb666fd2ffd3949b3d4d66a49e6e5b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907034"
---
# <a name="enum-mcdremotesystemdiscoverytype"></a>列挙型 `MCDRemoteSystemDiscoveryType` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemDiscoveryType)
```  

含むリモート システムを記述する値が検出されることができます。 

## <a name="fields"></a>フィールド

| 名前                              | 値 | 説明                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemDiscoveryTypeAny   | 0     | リモート システムでは、任意の接続を探索可能です。  |
| MCDRemoteSystemDiscoveryTypeProximal | 1     | リモート システムは、ローカルなどの位接続検出のみ
ネットワーク接続または Bluetooth 接続します。 |
| MCDRemoteSystemDiscoveryTypeCloud | 2     | リモート システムでは、クラウド接続検出のみです。 |
| MCDRemoteSystemDiscoveryTypeSpatiallyProximal | 3     | リモート システムが、位接続を介してといる必要があります。
(たとえば Bluetooth 範囲) でクライアント デバイス空間的に近い。  |

