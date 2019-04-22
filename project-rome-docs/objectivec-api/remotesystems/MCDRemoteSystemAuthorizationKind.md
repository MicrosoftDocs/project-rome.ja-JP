---
title: MCDRemoteSystemAuthorizationKind
description: リモート システムの探索の潜在的な承認種類 (ユーザー アカウント ベースの承認スコープ) を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 4f54d187282e946dd2912d1d72eacc02c7ee4077
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801324"
---
# <a name="enum-mcdremotesystemauthorizationkind"></a>列挙型 `MCDRemoteSystemAuthorizationKind` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemAuthorizationKind)
```  

リモート システムの探索の潜在的な承認種類 (ユーザー アカウント ベースの承認スコープ) を記述する値が含まれています。 

## <a name="fields"></a>フィールド

| 名前                              | 値 | 説明                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemAuthorizationKindSameUser   | 0     | システムは検出し、上に同じユーザー アカウントによって署名されたデバイスとの接続のみです。   |
| MCDRemoteSystemAuthorizationKindAnonymous | 1     | システムでは、検出でき、指定の近くでされていて、匿名の検出を許可、他のユーザーのデバイスと接続することができます。  |

