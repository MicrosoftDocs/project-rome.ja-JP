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
# <a name="class-mcdconnecteddevicesprocessnotificationoperation"></a><span data-ttu-id="d4472-104">クラス `MCDConnectedDevicesProcessNotificationOperation`</span><span class="sxs-lookup"><span data-stu-id="d4472-104">class `MCDConnectedDevicesProcessNotificationOperation`</span></span> 

```
@interface MCDConnectedDevicesProcessNotificationOperation : NSObject
```  
<span data-ttu-id="d4472-105">処理のために接続しているデバイス プラットフォームに APNS 通知を提供することが結果。</span><span class="sxs-lookup"><span data-stu-id="d4472-105">The result of giving an APNS notification to the Connected Devices platform for processing.</span></span>

> [!NOTE] 
> <span data-ttu-id="d4472-106">MCDConnectedDevicesNotification を代わりに使用するこのクラスが非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="d4472-106">This class is deprecated, use MCDConnectedDevicesNotification instead.</span></span> 

## <a name="properties"></a><span data-ttu-id="d4472-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d4472-107">Properties</span></span>

### <a name="connecteddevicesnotification"></a><span data-ttu-id="d4472-108">connectedDevicesNotification</span><span class="sxs-lookup"><span data-stu-id="d4472-108">connectedDevicesNotification</span></span>
`@property(nonatomic, readonly, getter=isConnectedDevicesNotification) BOOL connectedDevicesNotification;`

<span data-ttu-id="d4472-109">これは、通知が接続されているデバイス プラットフォームのためのものかどうかを示すフラグです。</span><span class="sxs-lookup"><span data-stu-id="d4472-109">This is a flag indicating whether the notification was intended for the Connected Devices platform.</span></span>

## <a name="methods"></a><span data-ttu-id="d4472-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="d4472-110">Methods</span></span>

### <a name="waitforcompletionasync"></a><span data-ttu-id="d4472-111">waitForCompletionAsync</span><span class="sxs-lookup"><span data-stu-id="d4472-111">waitForCompletionAsync</span></span>
`- (void)waitForCompletionAsync:(nonnull void (^)(NSError* _Nullable error))callback;`

 <span data-ttu-id="d4472-112">通知処理を完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="d4472-112">Wait for the notification to finish being handled.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d4472-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4472-113">Parameters</span></span> 
* `callback` 

<span data-ttu-id="d4472-114">完了の通知コールバックの結果です。</span><span class="sxs-lookup"><span data-stu-id="d4472-114">The callback result for notification completion.</span></span>
