---
title: MCDUserNotificationReader
description: このクラスは、新しいユーザー通知の受信およびユーザーへの通知は提供します。 更新します。 ユーザーが接続されているデバイスのプラットフォームで永続化の通知のコレクションへのアクセスも提供します。
keywords: microsoft、windows、リレーのデバイス、iOS に関する「方法」に関する「方法」の iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800734"
---
# <a name="class-mcdusernotificationreader"></a><span data-ttu-id="ecdee-105">クラス `MCDUserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="ecdee-105">class `MCDUserNotificationReader`</span></span>

```
@interface MCDUserNotificationReader : NSObject
```

<span data-ttu-id="ecdee-106">このクラスは、新しいユーザー通知の受信およびユーザーへの通知は提供します。 更新します。</span><span class="sxs-lookup"><span data-stu-id="ecdee-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="ecdee-107">ユーザーが接続されているデバイスのプラットフォームで永続化の通知のコレクションへのアクセスも提供します。</span><span class="sxs-lookup"><span data-stu-id="ecdee-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="properties"></a><span data-ttu-id="ecdee-108">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ecdee-108">Properties</span></span>

### <a name="serializedstate"></a><span data-ttu-id="ecdee-109">serializedState</span><span class="sxs-lookup"><span data-stu-id="ecdee-109">serializedState</span></span>
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

<span data-ttu-id="ecdee-110">変更のリーダーの現在の状態を返します。</span><span class="sxs-lookup"><span data-stu-id="ecdee-110">Returns the current state of the change reader.</span></span> <span data-ttu-id="ecdee-111">同じ状態から、新しいリーダーを構築するために使用します。</span><span class="sxs-lookup"><span data-stu-id="ecdee-111">Can be used to construct a new reader starting from the same state.</span></span>
<span data-ttu-id="ecdee-112">通知の変更 (または、初期状態を [なし] が正常に完了した場合) の最後に完了したバッチに基づいています。</span><span class="sxs-lookup"><span data-stu-id="ecdee-112">Based upon the last completed batch of notification changes (or initial state, if none have completed successfully).</span></span>

### <a name="datachanged"></a><span data-ttu-id="ecdee-113">DataChanged</span><span class="sxs-lookup"><span data-stu-id="ecdee-113">dataChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

<span data-ttu-id="ecdee-114">MCDUserNotificationReader のイベント サブスクリプションを変更します。</span><span class="sxs-lookup"><span data-stu-id="ecdee-114">Event subscription for MCDUserNotificationReader changed.</span></span>

## <a name="methods"></a><span data-ttu-id="ecdee-115">メソッド</span><span class="sxs-lookup"><span data-stu-id="ecdee-115">Methods</span></span>

### <a name="readbatchasyncwithmaxsize"></a><span data-ttu-id="ecdee-116">readBatchAsyncWithMaxSize</span><span class="sxs-lookup"><span data-stu-id="ecdee-116">readBatchAsyncWithMaxSize</span></span>
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="ecdee-117">読み取り通知は、新しい受信の通知などを変更し、バッチ内の既存の通知を更新します。</span><span class="sxs-lookup"><span data-stu-id="ecdee-117">Read notification changes including new incoming notifications and updates on existing notifications in batch.</span></span>