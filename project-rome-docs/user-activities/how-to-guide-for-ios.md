---
title: 発行およびユーザー アクティビティ (iOS) の読み取り
description: このガイドでは、作成、発行、および iOS アプリでの Windows ベースのユーザー アクティビティを読み取る方法を示します。
ms.topic: article
keywords: microsoft、windows、ローマ、ユーザー アクティビティ、ios をプロジェクトします。
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 3cc19463a5e036ab76288760aa70d86f1861675b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909434"
---
# <a name="implementing-user-activities-for-ios"></a><span data-ttu-id="33c13-104">IOS 用のユーザー アクティビティの実装</span><span class="sxs-lookup"><span data-stu-id="33c13-104">Implementing User Activities for iOS</span></span>

<span data-ttu-id="33c13-105">ユーザー アクティビティとは、アプリケーション内のユーザーのタスクを表すデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="33c13-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="33c13-106">これらによってようには後で続行するのには現在のタスクのスナップショットを保存します。</span><span class="sxs-lookup"><span data-stu-id="33c13-106">They make it possible to save a snapshot of a current task to be continued at a later time.</span></span> <span data-ttu-id="33c13-107">[Windows タイムライン](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/)機能では、スクロール可能なすべての最近のアクティビティの一覧、テキストとグラフィックス カードとして表される Windows ユーザーを表示します。</span><span class="sxs-lookup"><span data-stu-id="33c13-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="33c13-108">ユーザー アクティビティの詳細については一般に、表示[デバイス間であってもユーザーの利用状況を引き続き](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities)します。</span><span class="sxs-lookup"><span data-stu-id="33c13-108">For more information about User Activities in general, see [Continue user activity, even across devices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="33c13-109">活動を作成または更新する場合の推奨事項を参照してください、[ユーザー アクティビティのベスト プラクティス](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices)ガイド。</span><span class="sxs-lookup"><span data-stu-id="33c13-109">For recommendations on when to create or update Activities, see the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="33c13-110">プロジェクト ローマ sdk では、iOS アプリではのみにユーザー アクティビティ タイムラインなどの Windows 機能で使用するために発行しないことができますが、エンドポイントとして機能、タイムラインと同様に、ユーザーにアクティビティを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="33c13-110">With the Project Rome SDK, your iOS app can not only publish User Activities for use in Windows features such as Timeline, but it can also act as an endpoint and read Activities back to the user just as Timeline does.</span></span> <span data-ttu-id="33c13-111">これにより、クロス デバイス アプリ、プラットフォームとデバイスではなく、ユーザーの存在のエクスペリエンスを完全に克服できます。</span><span class="sxs-lookup"><span data-stu-id="33c13-111">This allows cross-device apps to completely transcend their platforms and present experiences that follow users rather than devices.</span></span>

<span data-ttu-id="33c13-112">プロジェクトのローマの機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="33c13-112">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="33c13-113">このガイドでは、接続されているデバイス プラットフォームの使用を開始するために必要な手順について説明し、プラットフォームを使用して、ユーザー アクティビティの関連機能を実装する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="33c13-113">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement user activities related features.</span></span>

<span data-ttu-id="33c13-114">この手順はからコードを参照、[プロジェクト ローマ iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)GitHub に用意されています。</span><span class="sxs-lookup"><span data-stu-id="33c13-114">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="33c13-115">参照してください、 [API リファレンス](api-reference-for-ios.md)これらのシナリオに関連するリファレンス ドキュメントへのリンクについてのページ。</span><span class="sxs-lookup"><span data-stu-id="33c13-115">See the [API reference](api-reference-for-ios.md) page for links to the reference docs relevant to these scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="33c13-116">接続されているデバイス プラットフォームと通知を設定します。</span><span class="sxs-lookup"><span data-stu-id="33c13-116">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="33c13-117">プラットフォームを使用します。</span><span class="sxs-lookup"><span data-stu-id="33c13-117">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="33c13-118">ユーザー アクティビティのチャネルを初期化します。</span><span class="sxs-lookup"><span data-stu-id="33c13-118">Initialize a User Activity channel</span></span>

<span data-ttu-id="33c13-119">アプリでは、ユーザー アクティビティの機能を実装するには、ユーザー アクティビティを MCDUserActivityChannel を作成してフィードを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33c13-119">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a MCDUserActivityChannel.</span></span> <span data-ttu-id="33c13-120">これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33c13-120">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="33c13-121">サインイン ユーザーのアカウントは、この手順の必要があります。</span><span class="sxs-lookup"><span data-stu-id="33c13-121">You will need a signed-in user account for this step.</span></span> <span data-ttu-id="33c13-122">上記としてに、MCDUserAccount(s) を簡単に取得するのに認証プロバイダーのサンプルからクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="33c13-122">As above, you may use a class from the authentication provider sample to easily acquire the MCDUserAccount(s).</span></span> <span data-ttu-id="33c13-123">Microsoft 開発者向けダッシュ ボードの登録の過程で取得したクロス プラットフォーム アプリ ID を取得するも必要になります。</span><span class="sxs-lookup"><span data-stu-id="33c13-123">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="33c13-124">サンプル アプリから次のメソッドには、MCDUserActivityChannel を初期化します。</span><span class="sxs-lookup"><span data-stu-id="33c13-124">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

<span data-ttu-id="33c13-125">サンプル アプリから次のメソッドには、MCDUserActivityChannel を初期化します。</span><span class="sxs-lookup"><span data-stu-id="33c13-125">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

```ObjectiveC

    // Get a UserActivity channel, getting the default channel        
    NSLog(@"Creating UserActivityChannel");
    NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
    MCDUserDataFeed* userDataFeed = [MCDUserDataFeed userDataFeedForAccount:accounts[0]
        platform:[AppDataSource sharedInstance].platform
        activitySourceHost:CROSS_PLATFORM_APP_ID];
    NSArray<MCDSyncScope*>* syncScopes = @[ [MCDUserActivityChannel syncScope] ];
    [userDataFeed addSyncScopes:syncScopes];
    self.channel = [MCDUserActivityChannel userActivityChannelWithUserDataFeed:userDataFeed];
}
else
{
    NSLog(@"Must have an active account to publish activities!");
    self.createActivityStatusField.text = @"Need to be logged in!";
}
```
<span data-ttu-id="33c13-126">この時点では、チャネルで、MCDUserActivityChannel 参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="33c13-126">At this point, you should have an MCDUserActivityChannel reference in channel.</span></span>

### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="33c13-127">作成して、ユーザー アクティビティを発行します。</span><span class="sxs-lookup"><span data-stu-id="33c13-127">Create and publish a User Activity</span></span>

<span data-ttu-id="33c13-128">次のサンプル コードに示す、新しい**MCDUserActivity**インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="33c13-128">The following sample code shows how a new **MCDUserActivity** instance is created.</span></span>

```ObjectiveC
- (IBAction)createActivityButton:(id)sender
{
    // Step #2: Create a UserActivity
    [self.channel getOrCreateUserActivityAsync:[[NSUUID UUID] UUIDString]
        completion:^(MCDUserActivity* activity, NSError* error) {
            if (error)
            {
                NSLog(@"%@", error);
                self.createActivityStatusField.text = @"Error creating activity!";
            }
            else if (!activity)
            {
                NSLog(@"No activity created!");
            }
            else
            {
                dispatch_async(dispatch_get_main_queue(), ^{
                    self.activity = activity;

                    // Create an activityId so the app knows so you know how to get back
                    self.activityId.text = activity.activityId;
                    self.createActivityStatusField.text = @"Created by iOSSample";
                    // Create a deep link so the app can get right back to where it was
                    self.activationUri.text = @"roman-app:";
                    self.createActivityStatusField.text = @"Activity created";
                });
            }
        }];
}
```

<span data-ttu-id="33c13-129">次のメソッドのビジュアルのデータで、 **MCDUserActivity**アクティビティを発行する前に設定されます。</span><span class="sxs-lookup"><span data-stu-id="33c13-129">In the next method, the visual data of the **MCDUserActivity** is set before the Activity is published.</span></span> <span data-ttu-id="33c13-130">アクティブ化の URI は、アクティビティが (たとえば、タイムラインで選択した) ときにアクティブになったときに実行するアクションを決定します。</span><span class="sxs-lookup"><span data-stu-id="33c13-130">The activation URI will determine what action is taken when the Activity is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="33c13-131">表示テキスト表示されます他のデバイスで表示したとき (たとえば Windows タイムライン) のアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="33c13-131">The display text will be shown on other devices when they view the Activity (in Windows Timeline, for example).</span></span> <span data-ttu-id="33c13-132">IconUri は、web リンク アイコン イメージです。</span><span class="sxs-lookup"><span data-stu-id="33c13-132">The iconUri is a web link to an icon image.</span></span>


```ObjectiveC
- (IBAction)publishActivityButton:(id)sender
{
    self.createActivityStatusField.text = @"Saving";
    self.activity.activationUri = self.activationUri.text;
    // Set the display text for your activity.
    self.activity.visualElements.displayText = @"Visual Element, like an Adaptive Card";
    self.activity.visualElements.attribution.iconUri = @"https://www.microsoft.com/favicon.ico";

    // ...
```

<span data-ttu-id="33c13-133">1 回、 **MCDUserActivity**設定は、このデータは、発行操作が行わします。</span><span class="sxs-lookup"><span data-stu-id="33c13-133">Once the **MCDUserActivity** is populated with this data, the publish operation takes place.</span></span>

```ObjectiveC
    // ...

    // Publish the Activity
    [self.activity saveAsync:^(NSError* error) {
        dispatch_async(dispatch_get_main_queue(), ^{
            if (error)
            {
                NSLog(@"%@", error);
                self.createActivityStatusField.text = @"Error saving activity";
            }
            else
            {
                self.createActivityStatusField.text = @"Saved successfully!";
                [self.sessionButton setTitle:@"Start Session" forState:normal];
            }
        });
    }];
}

mActivityId = UUID.randomUUID().toString();
mDisplayText = "Created by OneSDK Sample App";
mActivationUri = "http://contoso.com");
```
> [!TIP] 
> <span data-ttu-id="33c13-134">上記のプロパティでは、構成できるその他の多くの機能があります。</span><span class="sxs-lookup"><span data-stu-id="33c13-134">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="33c13-135">UserActivity をカスタマイズできるさまざまな方法の詳細について、次を参照してください、  **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**、  **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md) 。**、および**[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** クラス。</span><span class="sxs-lookup"><span data-stu-id="33c13-135">For a complete look at the different ways that a UserActivity can be customized, see the **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, and **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** classes.</span></span> <span data-ttu-id="33c13-136">参照してください、[ユーザー アクティビティのベスト プラクティス](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices)ユーザー アクティビティをデザインする方法の詳細な推奨事項のガイド。</span><span class="sxs-lookup"><span data-stu-id="33c13-136">See the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

## <a name="update-an-existing-user-activity"></a><span data-ttu-id="33c13-137">既存のユーザー アクティビティを更新します。</span><span class="sxs-lookup"><span data-stu-id="33c13-137">Update an existing User Activity</span></span>

<span data-ttu-id="33c13-138">既存のアクティビティ (新しい engagement、変更されたページで、およびなど) 発生時に、その情報を更新する場合、これを行うを使用して、 **MCDUserActivitySession**します。</span><span class="sxs-lookup"><span data-stu-id="33c13-138">If you have an existing activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **MCDUserActivitySession**.</span></span> 

<span data-ttu-id="33c13-139">アプリのプロパティに、必要な変更を行うセッションを作成したら、 **UserActivity**します。</span><span class="sxs-lookup"><span data-stu-id="33c13-139">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="33c13-140">変更を完了すると、セッションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="33c13-140">When you're done making changes, close the session.</span></span> 

<span data-ttu-id="33c13-141">サンプル アプリから次のメソッドは、オンとオフのセッションを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="33c13-141">The following method from the sample app toggles a session on and off.</span></span>

```ObjectiveC
- (IBAction)manageSessionButton:(id)sender
{

    // Start a new a session for the UserActivity
    if (self.session == nil)
    {
       self.session = [self.activity createSession];
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"UserActivitySession has started %@", self.session);
            self.session = [self.activity createSession];
            dispatch_async(dispatch_get_main_queue(), ^{ [self.sessionButton setTitle:@"Stop Session" forState:normal]; });
        });
    }
    else
    {
        // Stop the UserActivitySession
        [self.session close];
        self.session = nil;
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"UserActivitySession has stopped %@", self.session);
            [self.sessionButton setTitle:@"Start Session" forState:normal];
        });
    }
}
```


<span data-ttu-id="33c13-142">**MCDUserActivitySession**を作成する方法として考えることができます、 **MCDUserActivitySessionHistoryItem** (次のセクションで説明)。</span><span class="sxs-lookup"><span data-stu-id="33c13-142">An **MCDUserActivitySession** can be thought of as a way to create a **MCDUserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="33c13-143">新しいを作成するのではなく**MCDUserActivity**ページごとに新しいセッションを作成するユーザーは、新しいページに移動するたびに単純にできます。</span><span class="sxs-lookup"><span data-stu-id="33c13-143">Rather than create a new **MCDUserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="33c13-144">これにより、読みやすいより直感的な構成されたアクティビティ。</span><span class="sxs-lookup"><span data-stu-id="33c13-144">This will make for a more intuitive and organized activity reading experience.</span></span>

## <a name="read-user-activities"></a><span data-ttu-id="33c13-145">ユーザー アクティビティを読み取り</span><span class="sxs-lookup"><span data-stu-id="33c13-145">Read User Activities</span></span>

<span data-ttu-id="33c13-146">アプリは、ユーザー アクティビティを読み取るし、タイムラインの Windows 機能と同様、ユーザーに提示します。</span><span class="sxs-lookup"><span data-stu-id="33c13-146">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="33c13-147">同一のユーザー アクティビティの読み取りを設定するに使用する**MCDUserActivityChannel**前のインスタンス。</span><span class="sxs-lookup"><span data-stu-id="33c13-147">To set up User Activity reading, you use the same **MCDUserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="33c13-148">このインスタンスを公開できます**MCDUserActivitySessionHistoryItem**インスタンスで、ユーザーの関与を特定の期間中に、特定のアクティビティを表します。</span><span class="sxs-lookup"><span data-stu-id="33c13-148">This instance can expose **MCDUserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

```ObjectiveC
- (IBAction)readActivityButton:(id)sender
{

    // Read/sync your UserActivities
    [self.channel getRecentUserActivitiesAsync:(NSInteger)5
        completion:^(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull result, NSError* _Nullable error) {
            dispatch_async(dispatch_get_main_queue(), ^{
                if (error)
                {
                    self.readActivityStatusField.text = @"Error reading activity!";
                }
                else if (result.count == 0)
                {
                    self.readActivityStatusField.text = @"Read completed, no activities returned";
                }
                else
                {
                    self.readActivityStatusField.text = @"Read completed!";
                    MCDUserActivitySessionHistoryItem* item = result.firstObject;
                    self.activityList.text = item.userActivity.activityId;
                    self.activityDisplay.text = item.userActivity.visualElements.displayText;
                }
            });
        }];
}
```

<span data-ttu-id="33c13-149">アプリが設定されている一覧を指定する必要がありますので**MCDUserActivitySessionHistoryItem**秒。</span><span class="sxs-lookup"><span data-stu-id="33c13-149">Now your app should have a populated list of **MCDUserActivitySessionHistoryItem**s.</span></span> <span data-ttu-id="33c13-150">基になるこれらの各配信できます**MCDUserActivity** (を参照してください**[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** 詳細については)、これをユーザーに表示できます。</span><span class="sxs-lookup"><span data-stu-id="33c13-150">Each of these can deliver the underlying **MCDUserActivity** (see **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** for details), which you can then display to the user.</span></span>
