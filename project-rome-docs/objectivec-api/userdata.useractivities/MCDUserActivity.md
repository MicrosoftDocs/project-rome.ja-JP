---
title: MCDUserActivity
description: MCDUserActivity クラスとそのプロパティについて説明します。 このクラスは、1つのユーザーアクティビティインスタンスを表します。
keywords: microsoft、windows、ユーザーアクティビティ、iOS、iPhone、、接続デバイス、プロジェクトローマ
ms.openlocfilehash: 8bdaf553611e868a5c37a9e033e2ba3126151967
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760146"
---
# <a name="class-mcduseractivity"></a><span data-ttu-id="e42ca-105">講義 `MCDUserActivity`</span><span class="sxs-lookup"><span data-stu-id="e42ca-105">class `MCDUserActivity`</span></span>

```
@interface MCDUserActivity : NSObject
```

<span data-ttu-id="e42ca-106">このクラスは、1つのユーザーアクティビティインスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-106">This class represents a single user activity instance.</span></span> <span data-ttu-id="e42ca-107">ユーザーアクティビティは、実行中にアプリによって作成され、別のデバイスまたは同じデバイス上の別のデバイスで続行できるユーザー作業ストリームをシステムに通知します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-107">A user activity is created by an app during its execution to notify the system of a user work stream that can be continued on another device or at another time on the same device.</span></span> <span data-ttu-id="e42ca-108">これは、ユーザーが関与しているタスクに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-108">It provides information about a task the user is engaged in.</span></span>

><span data-ttu-id="e42ca-109">**注:** MCDUserActivity インスタンスには、100 KB のサイズ制限があります。この値を超えるとパブリッシュできません。</span><span class="sxs-lookup"><span data-stu-id="e42ca-109">**Note:** MCDUserActivity instances have a size limit of 100KB, above which they cannot be published.</span></span>

## <a name="properties"></a><span data-ttu-id="e42ca-110">Properties</span><span class="sxs-lookup"><span data-stu-id="e42ca-110">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="e42ca-111">activityId</span><span class="sxs-lookup"><span data-stu-id="e42ca-111">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="e42ca-112">このアクティビティの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="e42ca-112">The unique ID for this activity.</span></span>

### <a name="state"></a><span data-ttu-id="e42ca-113">状態</span><span class="sxs-lookup"><span data-stu-id="e42ca-113">state</span></span>
`@property(nonatomic, readonly) MCDUserActivityState state;`

<span data-ttu-id="e42ca-114">このアクティビティの状態。</span><span class="sxs-lookup"><span data-stu-id="e42ca-114">The state of this activity.</span></span>

### <a name="activationuri"></a><span data-ttu-id="e42ca-115">activationUri</span><span class="sxs-lookup"><span data-stu-id="e42ca-115">activationUri</span></span>
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

<span data-ttu-id="e42ca-116">このユーザーアクティビティがアクティブになったときに従う URI。</span><span class="sxs-lookup"><span data-stu-id="e42ca-116">The URI to follow when this user activity is activated.</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="e42ca-117">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="e42ca-117">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="e42ca-118">プライマリ URI が失敗した場合に使用される、このアクティビティによって保持されている web フレンドリ URI。</span><span class="sxs-lookup"><span data-stu-id="e42ca-118">The web-friendly URI held by this activity, to be used if the primary URI fails.</span></span>

### <a name="contenturi"></a><span data-ttu-id="e42ca-119">contentUri</span><span class="sxs-lookup"><span data-stu-id="e42ca-119">contentUri</span></span>
`@property(nonatomic, copy, nullable) NSString* contentUri;`

<span data-ttu-id="e42ca-120">このアクティビティのコンテンツ URI (別のデバイス上のアクティビティを表すために使用されるイメージの URI)。</span><span class="sxs-lookup"><span data-stu-id="e42ca-120">The content URI for this activity (the URI of the image that will be used to represent the activity on another device).</span></span>

### <a name="contenttype"></a><span data-ttu-id="e42ca-121">contentType</span><span class="sxs-lookup"><span data-stu-id="e42ca-121">contentType</span></span>
`@property(nonatomic, copy, nullable) NSString* contentType;`

<span data-ttu-id="e42ca-122">**Contenturi**に格納されているコンテンツの MIME (Multipurpose Internet Mail Extensions) の種類。</span><span class="sxs-lookup"><span data-stu-id="e42ca-122">the MIME (Multipurpose Internet Mail Extensions) type of the content stored in **contentUri**.</span></span> <span data-ttu-id="e42ca-123">たとえば、"text/plain" のようになります。</span><span class="sxs-lookup"><span data-stu-id="e42ca-123">For example, "text/plain".</span></span>

### <a name="contentinfojson"></a><span data-ttu-id="e42ca-124">contentInfoJson</span><span class="sxs-lookup"><span data-stu-id="e42ca-124">contentInfoJson</span></span>
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

<span data-ttu-id="e42ca-125">このアクティビティの基本コンテンツ情報。</span><span class="sxs-lookup"><span data-stu-id="e42ca-125">The basic content info for this activity.</span></span> <span data-ttu-id="e42ca-126">たとえば、アクティビティが RSS フィードを読み取っている場合、コンテンツ文字列には、アーティクルとその作成者の名前が含まれている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e42ca-126">For example, if your activity was reading an RSS feed, the content string might include the name of the article and its author.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="e42ca-127">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="e42ca-127">appDisplayName</span></span>
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

<span data-ttu-id="e42ca-128">このアクティビティのアプリの表示名。</span><span class="sxs-lookup"><span data-stu-id="e42ca-128">The app display name for this activity.</span></span>

### <a name="visualelements"></a><span data-ttu-id="e42ca-129">visualElements</span><span class="sxs-lookup"><span data-stu-id="e42ca-129">visualElements</span></span>
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

<span data-ttu-id="e42ca-130">このアクティビティのビジュアル要素 (アクティビティの "詳細" タイルに使用できる情報)。</span><span class="sxs-lookup"><span data-stu-id="e42ca-130">The visual elements for this activity (information that can be used for the "details" tile of the activity).</span></span>

### <a name="roamable"></a><span data-ttu-id="e42ca-131">ローミング</span><span class="sxs-lookup"><span data-stu-id="e42ca-131">roamable</span></span>
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

<span data-ttu-id="e42ca-132">このアクティビティが他のエンドポイントにローミングされているかどうかを取得または設定します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-132">Gets or sets whether this activity is roamed to other endpoints.</span></span>

## <a name="constructors"></a><span data-ttu-id="e42ca-133">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="e42ca-133">Constructors</span></span>

### <a name="activitywithactivityid"></a><span data-ttu-id="e42ca-134">activityWithActivityId</span><span class="sxs-lookup"><span data-stu-id="e42ca-134">activityWithActivityId</span></span>
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="e42ca-135">指定した ID を使用して、このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-135">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="e42ca-136">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e42ca-136">Parameters</span></span>
* `activityId` 

<span data-ttu-id="e42ca-137">このアクティビティの識別子 (一意の文字列である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="e42ca-137">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="e42ca-138">戻り値</span><span class="sxs-lookup"><span data-stu-id="e42ca-138">Returns</span></span>
<span data-ttu-id="e42ca-139">このクラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-139">Returns an instance of this class.</span></span>

### <a name="initwithactivityid"></a><span data-ttu-id="e42ca-140">initWithActivityId</span><span class="sxs-lookup"><span data-stu-id="e42ca-140">initWithActivityId</span></span>
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="e42ca-141">指定した ID を使用して、このクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-141">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="e42ca-142">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e42ca-142">Parameters</span></span>
* `activityId`

<span data-ttu-id="e42ca-143">このアクティビティの識別子 (一意の文字列である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="e42ca-143">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="e42ca-144">戻り値</span><span class="sxs-lookup"><span data-stu-id="e42ca-144">Returns</span></span>
<span data-ttu-id="e42ca-145">このクラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-145">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="e42ca-146">メソッド</span><span class="sxs-lookup"><span data-stu-id="e42ca-146">Methods</span></span>

### <a name="createsession"></a><span data-ttu-id="e42ca-147">createSession</span><span class="sxs-lookup"><span data-stu-id="e42ca-147">createSession</span></span>
`- (nonnull MCDUserActivitySession*)createSession;`

<span data-ttu-id="e42ca-148">この MCDUserActivity が関連付けられるユーザーアクティビティセッションを作成します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-148">Creates a user activity session that this MCDUserActivity will be associated with.</span></span> <span data-ttu-id="e42ca-149">関連付けられた MCDUserActivitySession は、ユーザーが現在アクティビティに関与していることを示します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-149">An associated MCDUserActivitySession indicates that the user is currently engaged in the activity.</span></span>

#### <a name="returns"></a><span data-ttu-id="e42ca-150">戻り値</span><span class="sxs-lookup"><span data-stu-id="e42ca-150">Returns</span></span>
<span data-ttu-id="e42ca-151">作成されたセッション。</span><span class="sxs-lookup"><span data-stu-id="e42ca-151">The created session.</span></span>

### <a name="saveasync"></a><span data-ttu-id="e42ca-152">saveAsync</span><span class="sxs-lookup"><span data-stu-id="e42ca-152">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="e42ca-153">ユーザーアクティビティを発行します。</span><span class="sxs-lookup"><span data-stu-id="e42ca-153">Publishes the user activity.</span></span> <span data-ttu-id="e42ca-154">このメソッドが呼び出される前に、MCDUserActivity には、アクティベーション URI と VisualElements メンバーが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e42ca-154">The MCDUserActivity must have an activation URI and a VisualElements member with set display text before this method is called.</span></span> <span data-ttu-id="e42ca-155">このメソッドは、アプリが MCDUserActivity のプロパティを変更するたびに呼び出される必要があります (更新プログラムを発行するため)。</span><span class="sxs-lookup"><span data-stu-id="e42ca-155">This method should be called whenever the app modifies a property of the MCDUserActivity (in order to publish the update).</span></span>

#### <a name="parameters"></a><span data-ttu-id="e42ca-156">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e42ca-156">Parameters</span></span>
* <span data-ttu-id="e42ca-157">`completionBlock` 完了時に実行するコードブロック。</span><span class="sxs-lookup"><span data-stu-id="e42ca-157">`completionBlock` The code block to execute upon completion.</span></span>