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
# <a name="implementing-user-activities-for-android"></a>Android のユーザー アクティビティの実装

ユーザー アクティビティは、アプリケーション内でのユーザーのタスクを表すデータ構造です。 タスクのスナップショットを保存して後で続行することを可能にします。 [Windows タイムライン](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/)機能は Windows ユーザーに、ユーザーの最近のアクティビティすべてを、テキストとグラフィックスを使ったカードで表現したスクロール可能リストで表示します。 ユーザー アクティビティ全般の詳細については、[デバイス間でのユーザー アクティビティの継続](/windows/uwp/launch-resume/useractivities)に関する記事を参照してください。 アクティビティの作成または更新の推奨されるタイミングについては、[ユーザー アクティビティのベスト プラクティス](/windows/uwp/launch-resume/useractivities-best-practices) ガイドを参照してください。

Android アプリは Project Rome SDK によって、タイムラインなどの Windows 機能で使用するユーザー アクティビティを発行できるだけでなく、エンドポイントとして機能して、Windows デバイス上のタイムラインと同様にアクティビティをユーザーに読み戻すこともできます。 これによりクロスデバイス アプリは、プラットフォームの枠を超えて、デバイスではなくユーザーをフォローするエクスペリエンスを提供することができます。  

これらのシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-android.md)のページを参照してください。

この手順では、[Project Rome Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)のコードを参照します。

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームの使用

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>ユーザー アクティビティ チャネルの初期化

ユーザー アクティビティ機能をアプリで実装するには、まず、UserActivityChannel を作成することでユーザー アクティビティ フィードを初期化する必要があります。 これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。

Microsoft デベロッパー ダッシュボードへの登録時に取得したクロスプラットフォーム アプリ ID も必要になります。
次のメソッドは UserActivityChannel を初期化します。

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

この時点で、UserActivityChannel の参照が mActivityChannel にあるはずです。


### <a name="create-and-publish-a-user-activity"></a>ユーザー アクティビティの作成と発行

次に、新しい **UserActivity** になるものの ID、DisplayText、および ActivationURI データを設定します。 ID は一意の文字列である必要があります。 DisplayText は、(たとえば Windows タイムラインで) アクティビティを表示するときに他のデバイス上で表示されるため、アクティビティの簡潔な説明にする必要があります。 ActivationUri は、**UserActivity** がアクティブ化されたとき (たとえば、タイムラインで選択されたとき) にどのようなアクションが実行されるかを決定します。 次のコードは、サンプル データをこれらのフィールドに格納します。


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

次に、新しい **UserActivity** インスタンスを作成するメソッドを提供します。

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
**UserActivity** インスタンスを作成したら、上記で定義したデータを入力します。

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
> 上記のプロパティに加えて、他にも多くの機能を構成できます。 UserActivity のさまざまなカスタマイズ方法の詳細については、**[UserActivity](/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**、**[UserActivityVisualElements](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**、および **[UserActivityAttribution](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** の各クラスを参照してください。 ユーザー アクティビティの設計方法に関する推奨事項の詳細については、[ユーザー アクティビティのベスト プラクティス](/windows/uwp/launch-resume/useractivities-best-practices) ガイドを参照してください。

### <a name="update-an-existing-user-activity"></a>既存のユーザー アクティビティの更新

既存のアクティビティがあり、(新しいエンゲージメントがあった、ページが変更されたなどの理由で) その情報を更新したい場合、**UserActivitySession** を使用して行うことができます。

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

セッションを作成したら、アプリで **UserActivity** のプロパティに必要な変更を加えることができます。 変更が完了したら、セッションを閉じます。 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

**UserActivitySession** は、**UserActivitySessionHistoryItem** (次のセクションで説明します) を作成する方法と考えることができます。 ユーザーが新しいページに移動するたびに新しい **UserActivity** を作成する代わりに、ページごとに新しいセッションを作成するだけで済みます。 これにより、より直感的で整ったアクティビティ読み取りエクスペリエンスが実現します。

### <a name="read-user-activities"></a>ユーザー アクティビティの読み取り

アプリは Windows タイムライン機能と同様に、ユーザー アクティビティを読み取ってユーザーに表示できます。 ユーザー アクティビティの読み取りを設定するには、以前と同じ **UserActivityChannel** インスタンスを使用します。 このインスタンスは **UserActivitySessionHistoryItem** インスタンスを公開することができ、これは、特定のアクティビティにおける特定期間中のユーザーのエンゲージメントを表します。

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

この時点で、アプリには **UserActivitySessionHistoryItem** の設定済みリストがあるはずです。 これらはそれぞれ、基になる **UserActivity** を提供でき (詳細は **[UserActivitySessionHistoryItem](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** を参照)、これをユーザーに表示することができます。