---
title: MCDUserDataFeedSyncScope
description: このクラスは、アプリがユーザー固有接続されたデバイスの特定の機能を使用する場合に接続されているデバイス プラットフォームのバックエンドと同期されるユーザー データを表します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 941381a61c9b17c837c25b089f7c7073d581c4a8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907174"
---
# <a name="class-mcduserdatafeedsyncscope"></a><span data-ttu-id="6e5d7-104">クラス `MCDUserDataFeedSyncScope`</span><span class="sxs-lookup"><span data-stu-id="6e5d7-104">class `MCDUserDataFeedSyncScope`</span></span>

```
@interface MCDUserDataFeedSyncScope : NSObject
```
 <span data-ttu-id="6e5d7-105">このインターフェイスは、アプリがユーザーのアクティビティなど、特定のユーザー固有接続しているデバイス機能を使用する場合に接続されているデバイス プラットフォームのバックエンドと同期されるユーザー データを表します。</span><span class="sxs-lookup"><span data-stu-id="6e5d7-105">This interface represents the user data that is synchronized with the Connected Devices Platform backend when the app uses certain user-specific Connected Devices functionality, such as user activities.</span></span> <span data-ttu-id="6e5d7-106">インスタンスは、このような機能を管理するクラスから静的に取得されます (例: **MCDUserActivityChannel**)、ありの作成に使用されます**MCDUserDataFeed**します。</span><span class="sxs-lookup"><span data-stu-id="6e5d7-106">An instance is retrieved statically from the class that manages such functionality (e.g. **MCDUserActivityChannel**), and it is used in the construction of **MCDUserDataFeed**.</span></span>

## <a name="properties"></a><span data-ttu-id="6e5d7-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6e5d7-107">Properties</span></span>

### <a name="platform"></a><span data-ttu-id="6e5d7-108">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="6e5d7-108">platform</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSString* platform;`

<span data-ttu-id="6e5d7-109">**ConnectedDevicesPlatform**がこのアプリの接続されたデバイスの機能用に初期化されたインスタンス。</span><span class="sxs-lookup"><span data-stu-id="6e5d7-109">The **ConnectedDevicesPlatform** instance that has been initialized for this app's Connected Devices functionality.</span></span>

### <a name="syncscopeflags"></a><span data-ttu-id="6e5d7-110">syncScopeFlags</span><span class="sxs-lookup"><span data-stu-id="6e5d7-110">syncScopeFlags</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSArray<NSString*>* syncScopeFlags;`

<span data-ttu-id="6e5d7-111">受信アクティビティをフィルター処理するためのオプションのフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="6e5d7-111">Set any optional flags for filtering incoming activities.</span></span>

### <a name="notificationtype"></a><span data-ttu-id="6e5d7-112">notificationType</span><span class="sxs-lookup"><span data-stu-id="6e5d7-112">notificationType</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSString* notificationType;`

<span data-ttu-id="6e5d7-113">ユーザー同期スコープのデータ フィードを受信する通知の種類の変更の種類を設定します。</span><span class="sxs-lookup"><span data-stu-id="6e5d7-113">Set type of change notification type to receive for user data feed sync scope</span></span>

```