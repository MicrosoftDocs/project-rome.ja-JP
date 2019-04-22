---
title: MCDRemoteSystemDiscoveryType
description: 含むリモート システムを記述する値が検出されることができます。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: dc94b92311cb666fd2ffd3949b3d4d66a49e6e5b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800504"
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

