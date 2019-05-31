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
# <a name="implementing-user-activities-for-android"></a>Android 用のユーザー アクティビティの実装

ユーザー アクティビティとは、アプリケーション内のユーザーのタスクを表すデータ構造です。 できることに、後に続くタスクのスナップショットを保存します。 [Windows タイムライン](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/)機能では、スクロール可能なすべての最近のアクティビティの一覧、テキストとグラフィックス カードとして表される Windows ユーザーを表示します。 ユーザー アクティビティの詳細については一般に、表示[デバイス間であってもユーザーの利用状況を引き続き](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities)します。 活動を作成または更新する場合の推奨事項を参照してください、[ユーザー アクティビティのベスト プラクティス](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices)ガイド。

プロジェクト ローマ sdk では、Android アプリだけでなくタイムラインなどの Windows 機能で使用するためのユーザー アクティビティの公開ことができますもエンドポイントとして機能してタイムラインは、Windows デバイス上と同様に、ユーザーにアクティビティを読み取り。 これにより、クロス デバイス アプリに、プラットフォームを出し抜くからして、次のデバイスではなく、ユーザー エクスペリエンスを提供できます。  

参照してください、 [API リファレンス](api-reference-for-android.md)これらのシナリオに関連するリファレンス ドキュメントへのリンクについてのページ。

この手順はからコードを参照、[プロジェクト ローマ Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)します。

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームを使用します。

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>ユーザー アクティビティのチャネルを初期化します。

アプリでは、ユーザー アクティビティの機能を実装するには、ユーザー アクティビティを UserActivityChannel を作成してフィードを初期化する必要があります。 これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。

Microsoft 開発者向けダッシュ ボードの登録の過程で取得したクロス プラットフォーム アプリ ID を取得するも必要になります。
次のメソッドは、UserActivityChannel を初期化します。

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

この時点では、mActivityChannel で UserActivityChannel の参照が必要です。


### <a name="create-and-publish-a-user-activity"></a>作成して、ユーザー アクティビティを発行します。

次に、新しい対象の ID、DisplayText ActivationURI データを設定**UserActivity**します。 ID は一意の文字列である必要があります。 (Windows タイムラインで、たとえば)、アクティビティを表示したときにその、DisplayText が他のデバイスで表示されるので、アクティビティの簡潔な説明は使用する必要があります。 どのようなアクションが実行されるときに、ActivationUri が決定されます、 **UserActivity** (たとえば、タイムラインで選択した) ときにアクティブにします。 次のコードは、サンプル データをこれらのフィールドに格納します。


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

次に、新たに作成するメソッドを提供**UserActivity**インスタンス。

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
作成したら、 **UserActivity**インスタンス、上記で定義されたデータを入力します。

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

最後に、アクティビティをクラウドに発行します。 

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
> 上記のプロパティでは、構成できるその他の多くの機能があります。 UserActivity をカスタマイズできるさまざまな方法の詳細について、次を参照してください、 **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)** 、 **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)。** 、および **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** クラス。 参照してください、[ユーザー アクティビティのベスト プラクティス](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices)ユーザー アクティビティをデザインする方法の詳細な推奨事項のガイド。

### <a name="update-an-existing-user-activity"></a>既存のユーザー アクティビティを更新します。

既存のアクティビティ (新しい engagement、変更されたページで、およびなど) 発生時に、その情報を更新する場合、これを行うを使用して、 **UserActivitySession**します。

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

アプリのプロパティに、必要な変更を行うセッションを作成したら、 **UserActivity**します。 変更を完了すると、セッションを閉じます。 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

A **UserActivitySession**を作成する方法として考えることができます、 **UserActivitySessionHistoryItem** (次のセクションで説明)。 新しいを作成するのではなく**UserActivity**ページごとに新しいセッションを作成するユーザーは、新しいページに移動するたびに単純にできます。 これにより、読みやすいより直感的な構成されたアクティビティ。

### <a name="read-user-activities"></a>ユーザー アクティビティを読み取り

アプリは、ユーザー アクティビティを読み取るし、タイムラインの Windows 機能と同様、ユーザーに提示します。 ユーザー アクティビティの読み取りを設定すると同じ使用**UserActivityChannel**前のインスタンス。 このインスタンスを公開できます**UserActivitySessionHistoryItem**インスタンスで、ユーザーの関与を特定の期間中に、特定のアクティビティを表します。

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

アプリが設定されている一覧を指定する必要がありますので**UserActivitySessionHistoryItem**秒。 基になるこれらの各配信できます**UserActivity** (を参照してください **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** 詳細については)、これをユーザーに表示できます。
