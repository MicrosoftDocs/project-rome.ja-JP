---
title: MCDEventSubscription
description: MCDEventSubscription クラスについて説明します。 このインターフェイスは、イベントサブスクリプションを簡単に管理する方法を提供します。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: 8f44d1ca75ea247f2cb26fe5b2c136b4db0bd97f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761076"
---
# <a name="class-mcdeventsubscription"></a>講義 `MCDEventSubscription` 

```
@interface MCDEventSubscription : NSObject
```  
このインターフェイスは、単純なイベントサブスクリプションを提供します。

## <a name="methods"></a>メソッド

### <a name="cancel"></a>cancel
`- (void)cancel;`

イベントのサブスクリプションを取り消します。 この呼び出しを行った後、アタッチされた EventListener はそれ以上イベントを受信しません (既にフライトイベントが配信されている可能性があります)。
ConnectedDevices 機能の多くはネイティブコードで実行されるので、EventListener によって保持されているリソースが適切にクリーンアップされるようにするには、常に cancel を呼び出すか、または使用しないことを確認することが重要です。
