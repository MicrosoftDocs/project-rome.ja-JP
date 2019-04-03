---
title: MCDEventSubscription
description: このインターフェイスは、単純なイベントのサブスクリプションを提供します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: ce5a5782f80b54e78a6e3890cd68d9e92c52226c
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909474"
---
# <a name="class-mcdeventsubscription"></a>クラス `MCDEventSubscription` 

```
@interface MCDEventSubscription : NSObject
```  
このインターフェイスは、単純なイベントのサブスクリプションを提供します。

## <a name="methods"></a>メソッド

### <a name="cancel"></a>キャンセル
`- (void)cancel;`

イベントのサブスクリプションを取り消します。 この呼び出しを行った後、アタッチされた EventListener はこれ以上のイベント (Already in フライト イベントを配信も可能性があります) を受信しません。
ConnectedDevices 機能の多くは、ネイティブ コードで行われる、ためにが確実か、常に、キャンセルが呼び出されるか、弱参照は、EventListener によって保持されているリソースの適切なクリーンアップすることを確認するために使用する重要です。
