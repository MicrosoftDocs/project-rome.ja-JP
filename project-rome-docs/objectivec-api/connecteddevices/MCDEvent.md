---
title: MCDEvent
description: このインターフェイスは、単純なイベント モデルを提供します。 イベントは、EventListeners によって消費される項目を生成します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: eabe9464a104593b06460153ed30f42f7cc103eb
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907254"
---
# <a name="class-mcdevent"></a>クラス `MCDEvent` 

```
@interface MCDEvent<__covariant SourceType, __covariant ArgsType> : NSObject
```  
 
 このインターフェイスは、単純なイベント モデルを提供します。 イベントは、EventListeners によって消費される項目を生成します。
イベントの項目のフローは、MCDEventSubscription によって制御されます。

## <a name="methods"></a>メソッド

### <a name="subscribe"></a>サブスクライブ (subscribe)
`- (nonnull MCDEventSubscription*)subscribe:(nonnull void (^)(SourceType _Nonnull, ArgsType _Nonnull))listener;`

特定の接続されているデバイス プラットフォームでのイベントをサブスクライブします。

#### <a name="parameters"></a>パラメーター 
* `listener` 

MCDEventSubscriptions をリッスンします。

#### <a name="returns"></a>戻り値
MCDEventSubscription のインスタンス。