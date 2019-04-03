---
title: MCDConnectedDevicesProcessNotificationOperation
description: ローマ プラットフォームへの通知を与える処理の結果。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: cb482e7b00cd5fe090de1708388d140cfd45777b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909894"
---
# <a name="class-mcdconnecteddevicesprocessnotificationoperation"></a>クラス `MCDConnectedDevicesProcessNotificationOperation` 

```
@interface MCDConnectedDevicesProcessNotificationOperation : NSObject
```  
処理のために接続しているデバイス プラットフォームに APNS 通知を提供することが結果。

> [!NOTE] 
> MCDConnectedDevicesNotification を代わりに使用するこのクラスが非推奨とされます。 

## <a name="properties"></a>プロパティ

### <a name="connecteddevicesnotification"></a>connectedDevicesNotification
`@property(nonatomic, readonly, getter=isConnectedDevicesNotification) BOOL connectedDevicesNotification;`

これは、通知が接続されているデバイス プラットフォームのためのものかどうかを示すフラグです。

## <a name="methods"></a>メソッド

### <a name="waitforcompletionasync"></a>waitForCompletionAsync
`- (void)waitForCompletionAsync:(nonnull void (^)(NSError* _Nullable error))callback;`

 通知処理を完了するまで待ちます。

#### <a name="parameters"></a>パラメーター 
* `callback` 

完了の通知コールバックの結果です。
