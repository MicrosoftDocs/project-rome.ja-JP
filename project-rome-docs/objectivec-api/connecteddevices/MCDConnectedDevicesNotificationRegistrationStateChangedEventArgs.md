---
title: MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs
description: MCDConnectedDevicesNotificationRegistration 状態変更イベントのイベント引数クラスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 83b59cc884cc0e8d59387b95388b4b7b2b5fa273
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800694"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatechangedeventargs"></a><span data-ttu-id="d07c4-104">クラス `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="d07c4-104">class `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs : NSObject
```  
<span data-ttu-id="d07c4-105">MCDConnectedDevicesNotificationRegistration 状態変更イベントのイベント引数クラスです。</span><span class="sxs-lookup"><span data-stu-id="d07c4-105">Event Args class for the MCDConnectedDevicesNotificationRegistration State Changed event.</span></span> <span data-ttu-id="d07c4-106">これは、適切な通知メカニズムを使用して新しい接続しているデバイス プラットフォームのメッセージについて、アプリケーションが通知を取得することを確認に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d07c4-106">This is used to ensure that the application gets informed about new Connected Devices platform messages via the correct notification mechanism.</span></span>

## <a name="properties"></a><span data-ttu-id="d07c4-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d07c4-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="d07c4-108">アカウント</span><span class="sxs-lookup"><span data-stu-id="d07c4-108">account</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="d07c4-109">変更が通知の登録状態のアカウント。</span><span class="sxs-lookup"><span data-stu-id="d07c4-109">The Account for which the notification registration state has changed for.</span></span>

### <a name="registration"></a><span data-ttu-id="d07c4-110">登録</span><span class="sxs-lookup"><span data-stu-id="d07c4-110">registration</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistration* registration;`

<span data-ttu-id="d07c4-111">状態が変化した登録インスタンスの情報。</span><span class="sxs-lookup"><span data-stu-id="d07c4-111">The information for registration instance whose state has changed.</span></span>

### <a name="state"></a><span data-ttu-id="d07c4-112">state</span><span class="sxs-lookup"><span data-stu-id="d07c4-112">state</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationState state;`

<span data-ttu-id="d07c4-113">新しい登録状態。</span><span class="sxs-lookup"><span data-stu-id="d07c4-113">The new registration state.</span></span>