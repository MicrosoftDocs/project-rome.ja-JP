---
title: MCDUserNotificationReader
description: このクラスは、新しい受信ユーザー通知とユーザー通知の更新を提供します。 また、接続されているデバイスプラットフォームに保持されているユーザー通知のコレクションにアクセスすることもできます。
keywords: microsoft、windows、device relay、how to iOS、how to iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800734"
---
# <a name="class-mcdusernotificationreader"></a><span data-ttu-id="b465a-105">講義`MCDUserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="b465a-105">class `MCDUserNotificationReader`</span></span>

```
@interface MCDUserNotificationReader : NSObject
```

<span data-ttu-id="b465a-106">このクラスは、新しい受信ユーザー通知とユーザー通知の更新を提供します。</span><span class="sxs-lookup"><span data-stu-id="b465a-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="b465a-107">また、接続されているデバイスプラットフォームに保持されているユーザー通知のコレクションにアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b465a-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="properties"></a><span data-ttu-id="b465a-108">Properties</span><span class="sxs-lookup"><span data-stu-id="b465a-108">Properties</span></span>

### <a name="serializedstate"></a><span data-ttu-id="b465a-109">serializedState</span><span class="sxs-lookup"><span data-stu-id="b465a-109">serializedState</span></span>
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

<span data-ttu-id="b465a-110">変更リーダーの現在の状態を返します。</span><span class="sxs-lookup"><span data-stu-id="b465a-110">Returns the current state of the change reader.</span></span> <span data-ttu-id="b465a-111">は、同じ状態から新しいリーダーを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="b465a-111">Can be used to construct a new reader starting from the same state.</span></span>
<span data-ttu-id="b465a-112">通知の変更が最後に完了したバッチに基づく (または、正常に完了しなかった場合は初期状態)。</span><span class="sxs-lookup"><span data-stu-id="b465a-112">Based upon the last completed batch of notification changes (or initial state, if none have completed successfully).</span></span>

### <a name="datachanged"></a><span data-ttu-id="b465a-113">dataChanged</span><span class="sxs-lookup"><span data-stu-id="b465a-113">dataChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

<span data-ttu-id="b465a-114">MCDUserNotificationReader のイベントサブスクリプションが変更されました。</span><span class="sxs-lookup"><span data-stu-id="b465a-114">Event subscription for MCDUserNotificationReader changed.</span></span>

## <a name="methods"></a><span data-ttu-id="b465a-115">メソッド</span><span class="sxs-lookup"><span data-stu-id="b465a-115">Methods</span></span>

### <a name="readbatchasyncwithmaxsize"></a><span data-ttu-id="b465a-116">readBatchAsyncWithMaxSize</span><span class="sxs-lookup"><span data-stu-id="b465a-116">readBatchAsyncWithMaxSize</span></span>
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="b465a-117">新しい受信通知や既存の通知をバッチで更新するなど、通知の変更を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="b465a-117">Read notification changes including new incoming notifications and updates on existing notifications in batch.</span></span>