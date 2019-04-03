---
title: MCDConnectedDevicesAccountType
description: Microsoft 提供のユーザー アカウントの種類を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5461398e3725b7a1e6937172c40336db60432666
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908904"
---
# <a name="enum-mcdconnecteddevicesaccounttype"></a>列挙型 `MCDConnectedDevicesAccountType`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountType)
```  

Microsoft 提供のユーザー アカウントの種類を記述する値が含まれています。

## <a name="fields"></a>フィールド

| 名前                              | 値 | 説明                    |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesAccountTypeAAD       | 0     | Azure Active Directory に社内アカウント  |
| MCDConnectedDevicesAccountTypeMSA       | 1     | Microsoft の個人アカウント |
| MCDConnectedDevicesAccountTypeAnonymous | 2     | 匿名 (ローカル、認証されていない) アカウント |