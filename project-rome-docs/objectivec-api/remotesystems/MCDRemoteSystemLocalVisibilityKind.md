---
title: MCDRemoteSystemLocalVisibilityKind
description: リモート システムの探索時に、ローカル アプリケーションの可視性の基本設定を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908864"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a>列挙型 `MCDRemoteSystemLocalVisibilityKind` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
リモート システムの探索時に、ローカル アプリケーションの可視性の基本設定を記述する値が含まれています。

## <a name="fields"></a>フィールド

| 名前                              | 値 | 説明                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemLocalVisibilityKindShowAll | 0 | 呼び出し元のアプリを含むすべての探索可能なアプリケーションを表示します。
| MCDRemoteSystemLocalVisibilityKindHideLocalApp | 1 | 呼び出し元のアプリケーションを非表示にします。