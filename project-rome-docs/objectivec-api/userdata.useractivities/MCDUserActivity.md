---
title: MCDUserActivity
description: このクラスは、1 人のユーザー アクティビティのインスタンスを表します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: f01889f5e41c761fe359ed1fa90befee4a8aca46
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907424"
---
# <a name="class-mcduseractivity"></a><span data-ttu-id="cc259-104">クラス `MCDUserActivity`</span><span class="sxs-lookup"><span data-stu-id="cc259-104">class `MCDUserActivity`</span></span>

```
@interface MCDUserActivity : NSObject
```

<span data-ttu-id="cc259-105">このクラスは、1 人のユーザー アクティビティのインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="cc259-105">This class represents a single user activity instance.</span></span> <span data-ttu-id="cc259-106">ユーザーのアクティビティは、別のデバイスで、または同じデバイス上の別の時に再開できるユーザーのワーク ストリームのシステムに通知するには、その実行中に、アプリによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="cc259-106">A user activity is created by an app during its execution to notify the system of a user work stream that can be continued on another device or at another time on the same device.</span></span> <span data-ttu-id="cc259-107">ユーザーが進行中のタスクに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="cc259-107">It provides information about a task the user is engaged in.</span></span>

><span data-ttu-id="cc259-108">**注:** MCDUserActivity インスタンスでは、100 KB を超えると、パブリッシュできませんのサイズ制限があります。</span><span class="sxs-lookup"><span data-stu-id="cc259-108">**Note:** MCDUserActivity instances have a size limit of 100KB, above which they cannot be published.</span></span>

## <a name="properties"></a><span data-ttu-id="cc259-109">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cc259-109">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="cc259-110">ActivityId</span><span class="sxs-lookup"><span data-stu-id="cc259-110">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="cc259-111">このアクティビティの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="cc259-111">The unique ID for this activity.</span></span>

### <a name="state"></a><span data-ttu-id="cc259-112">state</span><span class="sxs-lookup"><span data-stu-id="cc259-112">state</span></span>
`@property(nonatomic, readonly) MCDUserActivityState state;`

<span data-ttu-id="cc259-113">このアクティビティの状態。</span><span class="sxs-lookup"><span data-stu-id="cc259-113">The state of this activity.</span></span>

### <a name="activationuri"></a><span data-ttu-id="cc259-114">activationUri</span><span class="sxs-lookup"><span data-stu-id="cc259-114">activationUri</span></span>
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

<span data-ttu-id="cc259-115">このユーザーのアクティビティがアクティブ化されるときに実行する URI。</span><span class="sxs-lookup"><span data-stu-id="cc259-115">The URI to follow when this user activity is activated.</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="cc259-116">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="cc259-116">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="cc259-117">プライマリの URI が失敗した場合に使用される、このアクティビティによって保持されている web に適した URI。</span><span class="sxs-lookup"><span data-stu-id="cc259-117">The web-friendly URI held by this activity, to be used if the primary URI fails.</span></span>

### <a name="contenturi"></a><span data-ttu-id="cc259-118">contentUri</span><span class="sxs-lookup"><span data-stu-id="cc259-118">contentUri</span></span>
`@property(nonatomic, copy, nullable) NSString* contentUri;`

<span data-ttu-id="cc259-119">このアクティビティ (別のデバイスでのアクティビティを表すために使用されるイメージの URI) のコンテンツの URI。</span><span class="sxs-lookup"><span data-stu-id="cc259-119">The content URI for this activity (the URI of the image that will be used to represent the activity on another device).</span></span>

### <a name="contenttype"></a><span data-ttu-id="cc259-120">contentType</span><span class="sxs-lookup"><span data-stu-id="cc259-120">contentType</span></span>
`@property(nonatomic, copy, nullable) NSString* contentType;`

<span data-ttu-id="cc259-121">格納されているコンテンツの MIME (Multipurpose Internet Mail Extensions) 種類**contentUri**します。</span><span class="sxs-lookup"><span data-stu-id="cc259-121">the MIME (Multipurpose Internet Mail Extensions) type of the content stored in **contentUri**.</span></span> <span data-ttu-id="cc259-122">たとえば、「テキスト/プレーン」。</span><span class="sxs-lookup"><span data-stu-id="cc259-122">For example, "text/plain".</span></span>

### <a name="contentinfojson"></a><span data-ttu-id="cc259-123">contentInfoJson</span><span class="sxs-lookup"><span data-stu-id="cc259-123">contentInfoJson</span></span>
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

<span data-ttu-id="cc259-124">このアクティビティの基本的なコンテンツ情報。</span><span class="sxs-lookup"><span data-stu-id="cc259-124">The basic content info for this activity.</span></span> <span data-ttu-id="cc259-125">たとえば、アクティビティが RSS フィードを読み取って、コンテンツの文字列は、情報の記事と、作成者の名前を含める可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc259-125">For example, if your activity was reading an RSS feed, the content string might include the name of the article and its author.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="cc259-126">AppDisplayName</span><span class="sxs-lookup"><span data-stu-id="cc259-126">appDisplayName</span></span>
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

<span data-ttu-id="cc259-127">このアクティビティのアプリの表示名。</span><span class="sxs-lookup"><span data-stu-id="cc259-127">The app display name for this activity.</span></span>

### <a name="visualelements"></a><span data-ttu-id="cc259-128">VisualElements</span><span class="sxs-lookup"><span data-stu-id="cc259-128">visualElements</span></span>
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

<span data-ttu-id="cc259-129">このアクティビティ (アクティビティの詳細」のタイルを使用できる情報) のビジュアル要素。</span><span class="sxs-lookup"><span data-stu-id="cc259-129">The visual elements for this activity (information that can be used for the "details" tile of the activity).</span></span>

### <a name="roamable"></a><span data-ttu-id="cc259-130">移動</span><span class="sxs-lookup"><span data-stu-id="cc259-130">roamable</span></span>
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

<span data-ttu-id="cc259-131">取得またはこのアクティビティは他のエンドポイントにローミングするかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="cc259-131">Gets or sets whether this activity is roamed to other endpoints.</span></span>

## <a name="constructors"></a><span data-ttu-id="cc259-132">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="cc259-132">Constructors</span></span>

### <a name="activitywithactivityid"></a><span data-ttu-id="cc259-133">activityWithActivityId</span><span class="sxs-lookup"><span data-stu-id="cc259-133">activityWithActivityId</span></span>
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="cc259-134">指定した ID に置き換えます。 このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cc259-134">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="cc259-135">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc259-135">Parameters</span></span>
* `activityId` 

<span data-ttu-id="cc259-136">(一意の文字列にする必要があります)、このアクティビティの識別子。</span><span class="sxs-lookup"><span data-stu-id="cc259-136">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="cc259-137">戻り値</span><span class="sxs-lookup"><span data-stu-id="cc259-137">Returns</span></span>
<span data-ttu-id="cc259-138">このクラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="cc259-138">Returns an instance of this class.</span></span>

### <a name="initwithactivityid"></a><span data-ttu-id="cc259-139">initWithActivityId</span><span class="sxs-lookup"><span data-stu-id="cc259-139">initWithActivityId</span></span>
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="cc259-140">指定した ID に置き換えます。 このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cc259-140">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="cc259-141">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc259-141">Parameters</span></span>
* `activityId`

<span data-ttu-id="cc259-142">(一意の文字列にする必要があります)、このアクティビティの識別子。</span><span class="sxs-lookup"><span data-stu-id="cc259-142">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="cc259-143">戻り値</span><span class="sxs-lookup"><span data-stu-id="cc259-143">Returns</span></span>
<span data-ttu-id="cc259-144">このクラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="cc259-144">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="cc259-145">メソッド</span><span class="sxs-lookup"><span data-stu-id="cc259-145">Methods</span></span>

### <a name="createsession"></a><span data-ttu-id="cc259-146">CreateSession</span><span class="sxs-lookup"><span data-stu-id="cc259-146">createSession</span></span>
`- (nonnull MCDUserActivitySession*)createSession;`

<span data-ttu-id="cc259-147">この MCDUserActivity の関連付けられているユーザー アクティビティのセッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="cc259-147">Creates a user activity session that this MCDUserActivity will be associated with.</span></span> <span data-ttu-id="cc259-148">関連付けられている MCDUserActivitySession では、ユーザーが現在、アクティビティに関与していることを示します。</span><span class="sxs-lookup"><span data-stu-id="cc259-148">An associated MCDUserActivitySession indicates that the user is currently engaged in the activity.</span></span>

#### <a name="returns"></a><span data-ttu-id="cc259-149">戻り値</span><span class="sxs-lookup"><span data-stu-id="cc259-149">Returns</span></span>
<span data-ttu-id="cc259-150">作成されたセッションです。</span><span class="sxs-lookup"><span data-stu-id="cc259-150">The created session.</span></span>

### <a name="saveasync"></a><span data-ttu-id="cc259-151">saveAsync</span><span class="sxs-lookup"><span data-stu-id="cc259-151">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="cc259-152">ユーザー アクティビティを発行します。</span><span class="sxs-lookup"><span data-stu-id="cc259-152">Publishes the user activity.</span></span> <span data-ttu-id="cc259-153">MCDUserActivity は、このメソッドが呼び出される前に、アクティブ化 URI と設定の表示テキストを持つ VisualElements メンバーが必要です。</span><span class="sxs-lookup"><span data-stu-id="cc259-153">The MCDUserActivity must have an activation URI and a VisualElements member with set display text before this method is called.</span></span> <span data-ttu-id="cc259-154">アプリは、(更新プログラムの発行) するために、MCDUserActivity のプロパティを変更するたびに、このメソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc259-154">This method should be called whenever the app modifies a property of the MCDUserActivity (in order to publish the update).</span></span>

#### <a name="parameters"></a><span data-ttu-id="cc259-155">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc259-155">Parameters</span></span>
* <span data-ttu-id="cc259-156">`completionBlock` 完了時に実行するコード ブロックです。</span><span class="sxs-lookup"><span data-stu-id="cc259-156">`completionBlock` The code block to execute upon completion.</span></span>