---
title: 発行およびユーザー アクティビティ (Android) の読み取り
description: このガイドでは、作成、発行、および Android アプリでの Windows ベースのユーザー アクティビティを読み取る方法を示します。
ms.topic: article
keywords: microsoft、windows、ローマ、ユーザー アクティビティ、android をプロジェクトします。
ms.assetid: 8cfb7544-913c-48c0-8528-52b93ba8b0c6
ms.localizationpriority: medium
ms.openlocfilehash: 67f793341a108853d5b36e062fd04f441efff473
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801534"
---
# <a name="implementing-user-activities-for-android"></a><span data-ttu-id="c3f7a-104">Android 用のユーザー アクティビティの実装</span><span class="sxs-lookup"><span data-stu-id="c3f7a-104">Implementing User Activities for Android</span></span>

<span data-ttu-id="c3f7a-105">ユーザー アクティビティとは、アプリケーション内のユーザーのタスクを表すデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="c3f7a-106">できることに、後に続くタスクのスナップショットを保存します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-106">They make it possible to save a snapshot of a task to be continued at a later time.</span></span> <span data-ttu-id="c3f7a-107">[Windows タイムライン](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/)機能では、スクロール可能なすべての最近のアクティビティの一覧、テキストとグラフィックス カードとして表される Windows ユーザーを表示します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="c3f7a-108">ユーザー アクティビティの詳細については一般に、表示[デバイス間であってもユーザーの利用状況を引き続き](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities)します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-108">For more information about User Activities in general, see [Continue user activity, even across devices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="c3f7a-109">活動を作成または更新する場合の推奨事項を参照してください、[ユーザー アクティビティのベスト プラクティス](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices)ガイド。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-109">For recommendations on when to create or update Activities, see the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="c3f7a-110">プロジェクト ローマ sdk では、Android アプリだけでなくタイムラインなどの Windows 機能で使用するためのユーザー アクティビティの公開ことができますもエンドポイントとして機能してタイムラインは、Windows デバイス上と同様に、ユーザーにアクティビティを読み取り。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-110">With the Project Rome SDK, your Android app can not only publish User Activities for use in Windows features such as Timeline, but can also act as an endpoint and read Activities back to the user just as Timeline does on Windows devices.</span></span> <span data-ttu-id="c3f7a-111">これにより、クロス デバイス アプリに、プラットフォームを出し抜くからして、次のデバイスではなく、ユーザー エクスペリエンスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-111">This allows cross-device apps to transcend their platforms and provide experiences that follow users rather than devices.</span></span>  

<span data-ttu-id="c3f7a-112">参照してください、 [API リファレンス](api-reference-for-android.md)これらのシナリオに関連するリファレンス ドキュメントへのリンクについてのページ。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-112">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to these scenarios.</span></span>

<span data-ttu-id="c3f7a-113">この手順はからコードを参照、[プロジェクト ローマ Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-113">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="c3f7a-114">プラットフォームを使用します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-114">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="c3f7a-115">ユーザー アクティビティのチャネルを初期化します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-115">Initialize a User Activity channel</span></span>

<span data-ttu-id="c3f7a-116">アプリでは、ユーザー アクティビティの機能を実装するには、ユーザー アクティビティを UserActivityChannel を作成してフィードを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-116">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a UserActivityChannel.</span></span> <span data-ttu-id="c3f7a-117">これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-117">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="c3f7a-118">Microsoft 開発者向けダッシュ ボードの登録の過程で取得したクロス プラットフォーム アプリ ID を取得するも必要になります。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-118">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="c3f7a-119">次のメソッドは、UserActivityChannel を初期化します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-119">The following methods initialize a UserActivityChannel.</span></span>

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

<span data-ttu-id="c3f7a-120">この時点では、mActivityChannel で UserActivityChannel の参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-120">At this point, you should have a UserActivityChannel reference in mActivityChannel.</span></span>


### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="c3f7a-121">作成して、ユーザー アクティビティを発行します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-121">Create and publish a User Activity</span></span>

<span data-ttu-id="c3f7a-122">次に、新しい対象の ID、DisplayText ActivationURI データを設定**UserActivity**します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-122">Next, set the ID, DisplayText and ActivationURI data of what will be a new **UserActivity**.</span></span> <span data-ttu-id="c3f7a-123">ID は一意の文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-123">The ID should be a unique String.</span></span> <span data-ttu-id="c3f7a-124">(Windows タイムラインで、たとえば)、アクティビティを表示したときにその、DisplayText が他のデバイスで表示されるので、アクティビティの簡潔な説明は使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-124">The DisplayText will be shown on other devices when they view the Activity (in Windows Timeline, for example), so it should be a concise description of the activity.</span></span> <span data-ttu-id="c3f7a-125">どのようなアクションが実行されるときに、ActivationUri が決定されます、 **UserActivity** (たとえば、タイムラインで選択した) ときにアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-125">The ActivationUri will determine what action is taken when the **UserActivity** is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="c3f7a-126">次のコードは、サンプル データをこれらのフィールドに格納します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-126">The following code fills in sample data for these fields.</span></span>


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

<span data-ttu-id="c3f7a-127">次に、新たに作成するメソッドを提供**UserActivity**インスタンス。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-127">Next, provide a method that creates a new **UserActivity** instance.</span></span>

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
<span data-ttu-id="c3f7a-128">作成したら、 **UserActivity**インスタンス、上記で定義されたデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-128">Once you have the **UserActivity** instance, populate it with the data defined above.</span></span>

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

<span data-ttu-id="c3f7a-129">最後に、アクティビティをクラウドに発行します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-129">Finally, publish the Activity to the cloud.</span></span> 

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
> <span data-ttu-id="c3f7a-130">上記のプロパティでは、構成できるその他の多くの機能があります。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-130">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="c3f7a-131">UserActivity をカスタマイズできるさまざまな方法の詳細について、次を参照してください、 **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)** 、 **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)。** 、および **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** クラス。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-131">For a complete look at the different ways that a UserActivity can be customized, see the **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, and **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** classes.</span></span> <span data-ttu-id="c3f7a-132">参照してください、[ユーザー アクティビティのベスト プラクティス](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices)ユーザー アクティビティをデザインする方法の詳細な推奨事項のガイド。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-132">See the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

### <a name="update-an-existing-user-activity"></a><span data-ttu-id="c3f7a-133">既存のユーザー アクティビティを更新します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-133">Update an existing User Activity</span></span>

<span data-ttu-id="c3f7a-134">既存のアクティビティ (新しい engagement、変更されたページで、およびなど) 発生時に、その情報を更新する場合、これを行うを使用して、 **UserActivitySession**します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-134">If you have an existing Activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **UserActivitySession**.</span></span>

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

<span data-ttu-id="c3f7a-135">アプリのプロパティに、必要な変更を行うセッションを作成したら、 **UserActivity**します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-135">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="c3f7a-136">変更を完了すると、セッションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-136">When you're done making changes, close the session.</span></span> 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

<span data-ttu-id="c3f7a-137">A **UserActivitySession**を作成する方法として考えることができます、 **UserActivitySessionHistoryItem** (次のセクションで説明)。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-137">A **UserActivitySession** can be thought of as a way to create a **UserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="c3f7a-138">新しいを作成するのではなく**UserActivity**ページごとに新しいセッションを作成するユーザーは、新しいページに移動するたびに単純にできます。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-138">Rather than create a new **UserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="c3f7a-139">これにより、読みやすいより直感的な構成されたアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-139">This will make for a more intuitive and organized activity reading experience.</span></span>

### <a name="read-user-activities"></a><span data-ttu-id="c3f7a-140">ユーザー アクティビティを読み取り</span><span class="sxs-lookup"><span data-stu-id="c3f7a-140">Read User Activities</span></span>

<span data-ttu-id="c3f7a-141">アプリは、ユーザー アクティビティを読み取るし、タイムラインの Windows 機能と同様、ユーザーに提示します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-141">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="c3f7a-142">ユーザー アクティビティの読み取りを設定すると同じ使用**UserActivityChannel**前のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-142">To set up User Activity reading, use the same **UserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="c3f7a-143">このインスタンスを公開できます**UserActivitySessionHistoryItem**インスタンスで、ユーザーの関与を特定の期間中に、特定のアクティビティを表します。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-143">This instance can expose **UserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

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

<span data-ttu-id="c3f7a-144">アプリが設定されている一覧を指定する必要がありますので**UserActivitySessionHistoryItem**秒。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-144">Now your app should have a populated list of **UserActivitySessionHistoryItem**s.</span></span> <span data-ttu-id="c3f7a-145">基になるこれらの各配信できます**UserActivity** (を参照してください **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** 詳細については)、これをユーザーに表示できます。</span><span class="sxs-lookup"><span data-stu-id="c3f7a-145">Each of these can deliver the underlying **UserActivity** (see **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** for details), which you can then display to the user.</span></span>
