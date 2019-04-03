---
title: MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs
description: MCDConnectedDevicesNotificationRegistration 状態変更イベントのイベント引数クラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 83b59cc884cc0e8d59387b95388b4b7b2b5fa273
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908444"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatechangedeventargs"></a><span data-ttu-id="e0adc-104">クラス `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="e0adc-104">class `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs : NSObject
```  
<span data-ttu-id="e0adc-105">MCDConnectedDevicesNotificationRegistration 状態変更イベントのイベント引数クラスです。</span><span class="sxs-lookup"><span data-stu-id="e0adc-105">Event Args class for the MCDConnectedDevicesNotificationRegistration State Changed event.</span></span> <span data-ttu-id="e0adc-106">これは、適切な通知メカニズムを使用して新しい接続しているデバイス プラットフォームのメッセージについて、アプリケーションが通知を取得することを確認に使用されます。</span><span class="sxs-lookup"><span data-stu-id="e0adc-106">This is used to ensure that the application gets informed about new Connected Devices platform messages via the correct notification mechanism.</span></span>

## <a name="properties"></a><span data-ttu-id="e0adc-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e0adc-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="e0adc-108">アカウント</span><span class="sxs-lookup"><span data-stu-id="e0adc-108">account</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="e0adc-109">変更が通知の登録状態のアカウント。</span><span class="sxs-lookup"><span data-stu-id="e0adc-109">The Account for which the notification registration state has changed for.</span></span>

### <a name="registration"></a><span data-ttu-id="e0adc-110">登録</span><span class="sxs-lookup"><span data-stu-id="e0adc-110">registration</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistration* registration;`

<span data-ttu-id="e0adc-111">状態が変化した登録インスタンスの情報。</span><span class="sxs-lookup"><span data-stu-id="e0adc-111">The information for registration instance whose state has changed.</span></span>

### <a name="state"></a><span data-ttu-id="e0adc-112">state</span><span class="sxs-lookup"><span data-stu-id="e0adc-112">state</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationState state;`

<span data-ttu-id="e0adc-113">新しい登録状態。</span><span class="sxs-lookup"><span data-stu-id="e0adc-113">The new registration state.</span></span>