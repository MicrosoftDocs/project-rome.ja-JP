---
title: ユーザー アクティビティの発行と読み取り (Android)
description: このガイドでは、Android アプリで Windows ベースのユーザー アクティビティの作成、発行、読み取りを行う方法を示します。
ms.topic: article
keywords: microsoft, windows, project rome, ユーザー アクティビティ, android
ms.assetid: 8cfb7544-913c-48c0-8528-52b93ba8b0c6
ms.localizationpriority: medium
ms.openlocfilehash: ab9cd29451ca9af511b2bd5f94e423f1ba01b46e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901670"
---
# <a name="implementing-user-activities-for-android"></a><span data-ttu-id="51542-104">Android のユーザー アクティビティの実装</span><span class="sxs-lookup"><span data-stu-id="51542-104">Implementing User Activities for Android</span></span>

<span data-ttu-id="51542-105">ユーザー アクティビティは、アプリケーション内でのユーザーのタスクを表すデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="51542-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="51542-106">タスクのスナップショットを保存して後で続行することを可能にします。</span><span class="sxs-lookup"><span data-stu-id="51542-106">They make it possible to save a snapshot of a task to be continued at a later time.</span></span> <span data-ttu-id="51542-107">[Windows タイムライン](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/)機能は Windows ユーザーに、ユーザーの最近のアクティビティすべてを、テキストとグラフィックスを使ったカードで表現したスクロール可能リストで表示します。</span><span class="sxs-lookup"><span data-stu-id="51542-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="51542-108">ユーザー アクティビティ全般の詳細については、[デバイス間でのユーザー アクティビティの継続](/windows/uwp/launch-resume/useractivities)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51542-108">For more information about User Activities in general, see [Continue user activity, even across devices](/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="51542-109">アクティビティの作成または更新の推奨されるタイミングについては、[ユーザー アクティビティのベスト プラクティス](/windows/uwp/launch-resume/useractivities-best-practices) ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51542-109">For recommendations on when to create or update Activities, see the [User Activities best practices](/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="51542-110">Android アプリは Project Rome SDK によって、タイムラインなどの Windows 機能で使用するユーザー アクティビティを発行できるだけでなく、エンドポイントとして機能して、Windows デバイス上のタイムラインと同様にアクティビティをユーザーに読み戻すこともできます。</span><span class="sxs-lookup"><span data-stu-id="51542-110">With the Project Rome SDK, your Android app can not only publish User Activities for use in Windows features such as Timeline, but can also act as an endpoint and read Activities back to the user just as Timeline does on Windows devices.</span></span> <span data-ttu-id="51542-111">これによりクロスデバイス アプリは、プラットフォームの枠を超えて、デバイスではなくユーザーをフォローするエクスペリエンスを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="51542-111">This allows cross-device apps to transcend their platforms and provide experiences that follow users rather than devices.</span></span>  

<span data-ttu-id="51542-112">これらのシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-android.md)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51542-112">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to these scenarios.</span></span>

<span data-ttu-id="51542-113">この手順では、[Project Rome Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)のコードを参照します。</span><span class="sxs-lookup"><span data-stu-id="51542-113">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="51542-114">プラットフォームの使用</span><span class="sxs-lookup"><span data-stu-id="51542-114">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="51542-115">ユーザー アクティビティ チャネルの初期化</span><span class="sxs-lookup"><span data-stu-id="51542-115">Initialize a User Activity channel</span></span>

<span data-ttu-id="51542-116">ユーザー アクティビティ機能をアプリで実装するには、まず、UserActivityChannel を作成することでユーザー アクティビティ フィードを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="51542-116">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a UserActivityChannel.</span></span> <span data-ttu-id="51542-117">これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="51542-117">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="51542-118">Microsoft デベロッパー ダッシュボードへの登録時に取得したクロスプラットフォーム アプリ ID も必要になります。</span><span class="sxs-lookup"><span data-stu-id="51542-118">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="51542-119">次のメソッドは UserActivityChannel を初期化します。</span><span class="sxs-lookup"><span data-stu-id="51542-119">The following methods initialize a UserActivityChannel.</span></span>

```Java
private UserActivityChannel mActivityChannel;
private UserDataFeed mUserDataFeed;

// ...

/**
 * Initializes the UserActivityFeed.
 */
public void initializeUserActivityFeed() {

    // define what scope of data this app needs
    SyncScope[] scopes = { UserActivityChannel.getSyncScope(), UserNotificationChannel.getSyncScope() };

    // Get a reference to the UserDataFeed. This method is defined below
    mUserDataFeed = getUserDataFeed(scopes, new EventListener<UserDataFeed, Void>() {
        @Override
        public void onEvent(UserDataFeed userDataFeed, Void aVoid) {
            if (userDataFeed.getSyncStatus() == UserDataSyncStatus.SYNCHRONIZED) {
                // log synchronized.
            } else {
                // log synchronization not completed.
            }
        }
    });

    // this method is defined below
    mActivityChannel = getUserActivityChannel();
}

// instantiate the UserDataFeed
private UserDataFeed getUserDataFeed(SyncScope[] scopes, EventListener<UserDataFeed, Void> listener) {
    UserAccount[] accounts = AccountProviderBroker.getSignInHelper().getUserAccounts();
    if (accounts.length <= 0) {
        // notify the user that sign-in is required
        return null;
    }

    // use the initialized Platform instance, along with the cross-device app ID.
    UserDataFeed feed = UserDataFeed.getForAccount(accounts[0], PlatformBroker.getPlatform(), Secrets.APP_HOST_NAME);
    feed.addSyncStatusChangedListener(listener);
    feed.addSyncScopes(scopes);
    // sync data with the server
    feed.startSync();
    return feed;
}

// use the UserDataFeed reference to create a UserActivityChannel
@Nullable
private UserActivityChannel getUserActivityChannel() {
    UserActivityChannel channel = null;
    try {
        // create a UserActivityChannel for the signed in account
        channel = new UserActivityChannel(mUserDataFeed);
    } catch (Exception e) {
        e.printStackTrace();
        // handle exception
    }
    return channel;
}
```

<span data-ttu-id="51542-120">この時点で、UserActivityChannel の参照が mActivityChannel にあるはずです。</span><span class="sxs-lookup"><span data-stu-id="51542-120">At this point, you should have a UserActivityChannel reference in mActivityChannel.</span></span>


### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="51542-121">ユーザー アクティビティの作成と発行</span><span class="sxs-lookup"><span data-stu-id="51542-121">Create and publish a User Activity</span></span>

<span data-ttu-id="51542-122">次に、新しい **UserActivity** になるものの ID、DisplayText、および ActivationURI データを設定します。</span><span class="sxs-lookup"><span data-stu-id="51542-122">Next, set the ID, DisplayText and ActivationURI data of what will be a new **UserActivity**.</span></span> <span data-ttu-id="51542-123">ID は一意の文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="51542-123">The ID should be a unique String.</span></span> <span data-ttu-id="51542-124">DisplayText は、(たとえば Windows タイムラインで) アクティビティを表示するときに他のデバイス上で表示されるため、アクティビティの簡潔な説明にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="51542-124">The DisplayText will be shown on other devices when they view the Activity (in Windows Timeline, for example), so it should be a concise description of the activity.</span></span> <span data-ttu-id="51542-125">ActivationUri は、**UserActivity** がアクティブ化されたとき (たとえば、タイムラインで選択されたとき) にどのようなアクションが実行されるかを決定します。</span><span class="sxs-lookup"><span data-stu-id="51542-125">The ActivationUri will determine what action is taken when the **UserActivity** is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="51542-126">次のコードは、サンプル データをこれらのフィールドに格納します。</span><span class="sxs-lookup"><span data-stu-id="51542-126">The following code fills in sample data for these fields.</span></span>


```Java
private UserActivity mActivity;
private String mActivityId;
private String mDisplayText;
private String mActivationUri;

// ...

mActivityId = UUID.randomUUID().toString();
mDisplayText = "Created by OneSDK Sample App";
mActivationUri = "http://contoso.com");
```

<span data-ttu-id="51542-127">次に、新しい **UserActivity** インスタンスを作成するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="51542-127">Next, provide a method that creates a new **UserActivity** instance.</span></span>

```Java
// Create the UserActivity (with unique ID) using a custom method. 
mActivity = createUserActivity(mActivityChannel, mActivityId);

// ...

// Custom method for creating a new UserActivity
@Nullable
private UserActivity createUserActivity(UserActivityChannel channel, String activityId)
{
    UserActivity activity = null;
    AsyncOperation<UserActivity> activityOperation = channel.getOrCreateUserActivityAsync(activityId);
    try {
        activity = activityOperation.get();
        Log.d("UserActivityFragment","Created user activity successfully");
    } catch (Exception e) {
        e.printStackTrace();
        Log.d("UserActivityFragment","Created user activity successfully");
    }
    return activity;
}
```
<span data-ttu-id="51542-128">**UserActivity** インスタンスを作成したら、上記で定義したデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="51542-128">Once you have the **UserActivity** instance, populate it with the data defined above.</span></span>

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

<span data-ttu-id="51542-129">最後に、アクティビティをクラウドに発行します。</span><span class="sxs-lookup"><span data-stu-id="51542-129">Finally, publish the Activity to the cloud.</span></span> 

```Java
// This code saves and publishes the activity
AsyncOperation<Void> operation = mActivity.saveAsync();
operation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<Void, Throwable>() {
    @Override
    public void accept(Void aVoid, Throwable throwable) throws Throwable {
        if (throwable != null)
        {
            Log.d("UserActivityFragment", "Failed to save");
        } else {
            Log.d("UserActivityFragment", "User activity saved");
        }
    }
});
```

> [!TIP] 
> <span data-ttu-id="51542-130">上記のプロパティに加えて、他にも多くの機能を構成できます。</span><span class="sxs-lookup"><span data-stu-id="51542-130">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="51542-131">UserActivity のさまざまなカスタマイズ方法の詳細については、**[UserActivity](/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**、**[UserActivityVisualElements](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**、および **[UserActivityAttribution](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** の各クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51542-131">For a complete look at the different ways that a UserActivity can be customized, see the **[UserActivity](/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, and **[UserActivityAttribution](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** classes.</span></span> <span data-ttu-id="51542-132">ユーザー アクティビティの設計方法に関する推奨事項の詳細については、[ユーザー アクティビティのベスト プラクティス](/windows/uwp/launch-resume/useractivities-best-practices) ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="51542-132">See the [User Activities best practices](/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

### <a name="update-an-existing-user-activity"></a><span data-ttu-id="51542-133">既存のユーザー アクティビティの更新</span><span class="sxs-lookup"><span data-stu-id="51542-133">Update an existing User Activity</span></span>

<span data-ttu-id="51542-134">既存のアクティビティがあり、(新しいエンゲージメントがあった、ページが変更されたなどの理由で) その情報を更新したい場合、**UserActivitySession** を使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="51542-134">If you have an existing Activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **UserActivitySession**.</span></span>

```Java
private UserActivitySession mActivitySession;

// ...

if (mActivity != null)
{
    // create a session from a previous UserActivity instance.
    mActivitySession = mActivity.createSession();
    Log.d("UserActivityFragment", "Starting");
}
```

<span data-ttu-id="51542-135">セッションを作成したら、アプリで **UserActivity** のプロパティに必要な変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="51542-135">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="51542-136">変更が完了したら、セッションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="51542-136">When you're done making changes, close the session.</span></span> 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

<span data-ttu-id="51542-137">**UserActivitySession** は、**UserActivitySessionHistoryItem** (次のセクションで説明します) を作成する方法と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="51542-137">A **UserActivitySession** can be thought of as a way to create a **UserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="51542-138">ユーザーが新しいページに移動するたびに新しい **UserActivity** を作成する代わりに、ページごとに新しいセッションを作成するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="51542-138">Rather than create a new **UserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="51542-139">これにより、より直感的で整ったアクティビティ読み取りエクスペリエンスが実現します。</span><span class="sxs-lookup"><span data-stu-id="51542-139">This will make for a more intuitive and organized activity reading experience.</span></span>

### <a name="read-user-activities"></a><span data-ttu-id="51542-140">ユーザー アクティビティの読み取り</span><span class="sxs-lookup"><span data-stu-id="51542-140">Read User Activities</span></span>

<span data-ttu-id="51542-141">アプリは Windows タイムライン機能と同様に、ユーザー アクティビティを読み取ってユーザーに表示できます。</span><span class="sxs-lookup"><span data-stu-id="51542-141">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="51542-142">ユーザー アクティビティの読み取りを設定するには、以前と同じ **UserActivityChannel** インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="51542-142">To set up User Activity reading, use the same **UserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="51542-143">このインスタンスは **UserActivitySessionHistoryItem** インスタンスを公開することができ、これは、特定のアクティビティにおける特定期間中のユーザーのエンゲージメントを表します。</span><span class="sxs-lookup"><span data-stu-id="51542-143">This instance can expose **UserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

```Java
private ArrayList<UserActivitySessionHistoryItem> mHistoryItems; 

// ...

mHistoryItems.clear();

Log.d("UserActivityFragment", "Read");
//Async method to read activities. Last (most recent) 5 activities will be returned
AsyncOperation<UserActivitySessionHistoryItem[]> operation = mActivityChannel.getRecentUserActivitiesAsync(5);

operation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<UserActivitySessionHistoryItem[], Throwable>() {
    @Override
    public void accept(UserActivitySessionHistoryItem[] result, Throwable throwable) throws Throwable {
        if (throwable != null)
        {
            Log.d("UserActivityFragment", "Failed to read user activity!" + throwable.getMessage() + " " + throwable.getStackTrace());
        } else {
            // get the returned UserActivitySessionHistoryItems
            for (UserActivitySessionHistoryItem item : result)
            {
                mHistoryItems.add(item);
            }
        }
    }
});
```

<span data-ttu-id="51542-144">この時点で、アプリには **UserActivitySessionHistoryItem** の設定済みリストがあるはずです。</span><span class="sxs-lookup"><span data-stu-id="51542-144">Now your app should have a populated list of **UserActivitySessionHistoryItem** s.</span></span> <span data-ttu-id="51542-145">これらはそれぞれ、基になる **UserActivity** を提供でき (詳細は **[UserActivitySessionHistoryItem](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** を参照)、これをユーザーに表示することができます。</span><span class="sxs-lookup"><span data-stu-id="51542-145">Each of these can deliver the underlying **UserActivity** (see **[UserActivitySessionHistoryItem](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** for details), which you can then display to the user.</span></span>