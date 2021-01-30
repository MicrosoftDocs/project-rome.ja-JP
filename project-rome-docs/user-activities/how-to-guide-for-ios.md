---
title: ユーザー アクティビティの発行と読み取り (iOS)
description: このガイドでは、iOS アプリで Windows ベースのユーザー アクティビティの作成、発行、読み取りを行う方法を示します。
ms.topic: article
keywords: microsoft, windows, project rome, ユーザー アクティビティ, ios
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 95345d8fb4d8dd600ec0dc447ea38c29612402d1
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901680"
---
# <a name="implementing-user-activities-for-ios"></a><span data-ttu-id="65e77-104">iOS のユーザー アクティビティの実装</span><span class="sxs-lookup"><span data-stu-id="65e77-104">Implementing User Activities for iOS</span></span>

<span data-ttu-id="65e77-105">ユーザー アクティビティは、アプリケーション内でのユーザーのタスクを表すデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="65e77-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="65e77-106">現在のタスクのスナップショットを保存して後で続行することを可能にします。</span><span class="sxs-lookup"><span data-stu-id="65e77-106">They make it possible to save a snapshot of a current task to be continued at a later time.</span></span> <span data-ttu-id="65e77-107">[Windows タイムライン](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/)機能は Windows ユーザーに、ユーザーの最近のアクティビティすべてを、テキストとグラフィックスを使ったカードで表現したスクロール可能リストで表示します。</span><span class="sxs-lookup"><span data-stu-id="65e77-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="65e77-108">ユーザー アクティビティ全般の詳細については、[デバイス間でのユーザー アクティビティの継続](/windows/uwp/launch-resume/useractivities)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65e77-108">For more information about User Activities in general, see [Continue user activity, even across devices](/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="65e77-109">アクティビティの作成または更新の推奨されるタイミングについては、[ユーザー アクティビティのベスト プラクティス](/windows/uwp/launch-resume/useractivities-best-practices) ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65e77-109">For recommendations on when to create or update Activities, see the [User Activities best practices](/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="65e77-110">iOS アプリは Project Rome SDK によって、タイムラインなどの Windows 機能で使用するユーザー アクティビティを発行できるだけでなく、エンドポイントとして機能して、タイムラインと同様にアクティビティをユーザーに読み戻すこともできます。</span><span class="sxs-lookup"><span data-stu-id="65e77-110">With the Project Rome SDK, your iOS app can not only publish User Activities for use in Windows features such as Timeline, but it can also act as an endpoint and read Activities back to the user just as Timeline does.</span></span> <span data-ttu-id="65e77-111">これによりクロスデバイス アプリは、プラットフォームの枠を完全に超えて、デバイスではなくユーザーをフォローするエクスペリエンスを提示することができます。</span><span class="sxs-lookup"><span data-stu-id="65e77-111">This allows cross-device apps to completely transcend their platforms and present experiences that follow users rather than devices.</span></span>

<span data-ttu-id="65e77-112">Project Rome の機能は、Connected Devices Platform と呼ばれる基盤プラットフォームによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="65e77-112">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="65e77-113">このガイドでは、Connected Devices Platform を初めて使用するために必要な手順と、このプラットフォームを使用してユーザー アクティビティ関連機能を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="65e77-113">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement user activities related features.</span></span>

<span data-ttu-id="65e77-114">この手順では、GitHub から入手できる [Project Rome iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)のコードを参照します。</span><span class="sxs-lookup"><span data-stu-id="65e77-114">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="65e77-115">これらのシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-ios.md)のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65e77-115">See the [API reference](api-reference-for-ios.md) page for links to the reference docs relevant to these scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="65e77-116">Connected Devices Platform と通知の設定</span><span class="sxs-lookup"><span data-stu-id="65e77-116">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="65e77-117">プラットフォームの使用</span><span class="sxs-lookup"><span data-stu-id="65e77-117">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="65e77-118">ユーザー アクティビティ チャネルの初期化</span><span class="sxs-lookup"><span data-stu-id="65e77-118">Initialize a User Activity channel</span></span>

<span data-ttu-id="65e77-119">ユーザー アクティビティ機能をアプリで実装するには、まず、MCDUserActivityChannel を作成することでユーザー アクティビティ フィードを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="65e77-119">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a MCDUserActivityChannel.</span></span> <span data-ttu-id="65e77-120">これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="65e77-120">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="65e77-121">この手順にはサインインしたユーザー アカウントが必要になります。</span><span class="sxs-lookup"><span data-stu-id="65e77-121">You will need a signed-in user account for this step.</span></span> <span data-ttu-id="65e77-122">上記のように、認証プロバイダー サンプルのクラスを使用して MCDUserAccount を簡単に取得できます。</span><span class="sxs-lookup"><span data-stu-id="65e77-122">As above, you may use a class from the authentication provider sample to easily acquire the MCDUserAccount(s).</span></span> <span data-ttu-id="65e77-123">Microsoft デベロッパー ダッシュボードへの登録時に取得したクロスプラットフォーム アプリ ID も必要になります。</span><span class="sxs-lookup"><span data-stu-id="65e77-123">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="65e77-124">サンプル アプリの次のメソッドは MCDUserActivityChannel を初期化します。</span><span class="sxs-lookup"><span data-stu-id="65e77-124">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

<span data-ttu-id="65e77-125">サンプル アプリの次のメソッドは MCDUserActivityChannel を初期化します。</span><span class="sxs-lookup"><span data-stu-id="65e77-125">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

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
<span data-ttu-id="65e77-126">この時点で、MCDUserActivityChannel の参照がチャネルにあるはずです。</span><span class="sxs-lookup"><span data-stu-id="65e77-126">At this point, you should have an MCDUserActivityChannel reference in channel.</span></span>

### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="65e77-127">ユーザー アクティビティの作成と発行</span><span class="sxs-lookup"><span data-stu-id="65e77-127">Create and publish a User Activity</span></span>

<span data-ttu-id="65e77-128">次のサンプル コードは、新しい **MCDUserActivity** インスタンスがどのように作成されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="65e77-128">The following sample code shows how a new **MCDUserActivity** instance is created.</span></span>

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

<span data-ttu-id="65e77-129">次のメソッドでは、アクティビティが発行される前に **MCDUserActivity** の視覚的データが設定されます。</span><span class="sxs-lookup"><span data-stu-id="65e77-129">In the next method, the visual data of the **MCDUserActivity** is set before the Activity is published.</span></span> <span data-ttu-id="65e77-130">アクティブ化 URI は、アクティビティがアクティブ化されたとき (たとえば、タイムラインで選択されたとき) にどのようなアクションが実行されるかを決定します。</span><span class="sxs-lookup"><span data-stu-id="65e77-130">The activation URI will determine what action is taken when the Activity is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="65e77-131">表示テキストは、(たとえば Windows タイムラインで) アクティビティを表示するときに他のデバイス上で表示されます。</span><span class="sxs-lookup"><span data-stu-id="65e77-131">The display text will be shown on other devices when they view the Activity (in Windows Timeline, for example).</span></span> <span data-ttu-id="65e77-132">iconUri はアイコン画像への Web リンクです。</span><span class="sxs-lookup"><span data-stu-id="65e77-132">The iconUri is a web link to an icon image.</span></span>


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

<span data-ttu-id="65e77-133">このデータが **MCDUserActivity** に設定されると、発行操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="65e77-133">Once the **MCDUserActivity** is populated with this data, the publish operation takes place.</span></span>

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
> <span data-ttu-id="65e77-134">上記のプロパティに加えて、他にも多くの機能を構成できます。</span><span class="sxs-lookup"><span data-stu-id="65e77-134">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="65e77-135">UserActivity のさまざまなカスタマイズ方法の詳細については、**[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**、**[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**、および **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** の各クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65e77-135">For a complete look at the different ways that a UserActivity can be customized, see the **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, and **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** classes.</span></span> <span data-ttu-id="65e77-136">ユーザー アクティビティの設計方法に関する推奨事項の詳細については、[ユーザー アクティビティのベスト プラクティス](/windows/uwp/launch-resume/useractivities-best-practices) ガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="65e77-136">See the [User Activities best practices](/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

## <a name="update-an-existing-user-activity"></a><span data-ttu-id="65e77-137">既存のユーザー アクティビティの更新</span><span class="sxs-lookup"><span data-stu-id="65e77-137">Update an existing User Activity</span></span>

<span data-ttu-id="65e77-138">既存のアクティビティがあり、(新しいエンゲージメントがあった、ページが変更されたなどの理由で) その情報を更新したい場合、**MCDUserActivitySession** を使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="65e77-138">If you have an existing activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **MCDUserActivitySession**.</span></span> 

<span data-ttu-id="65e77-139">セッションを作成したら、アプリで **UserActivity** のプロパティに必要な変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="65e77-139">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="65e77-140">変更が完了したら、セッションを閉じます。</span><span class="sxs-lookup"><span data-stu-id="65e77-140">When you're done making changes, close the session.</span></span> 

<span data-ttu-id="65e77-141">サンプル アプリの次のメソッドは、セッションのオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="65e77-141">The following method from the sample app toggles a session on and off.</span></span>

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


<span data-ttu-id="65e77-142">**MCDUserActivitySession** は、**MCDUserActivitySessionHistoryItem** (次のセクションで説明します) を作成する方法と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="65e77-142">An **MCDUserActivitySession** can be thought of as a way to create a **MCDUserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="65e77-143">ユーザーが新しいページに移動するたびに新しい **MCDUserActivity** を作成する代わりに、ページごとに新しいセッションを作成するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="65e77-143">Rather than create a new **MCDUserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="65e77-144">これにより、より直感的で整ったアクティビティ読み取りエクスペリエンスが実現します。</span><span class="sxs-lookup"><span data-stu-id="65e77-144">This will make for a more intuitive and organized activity reading experience.</span></span>

## <a name="read-user-activities"></a><span data-ttu-id="65e77-145">ユーザー アクティビティの読み取り</span><span class="sxs-lookup"><span data-stu-id="65e77-145">Read User Activities</span></span>

<span data-ttu-id="65e77-146">アプリは Windows タイムライン機能と同様に、ユーザー アクティビティを読み取ってユーザーに表示できます。</span><span class="sxs-lookup"><span data-stu-id="65e77-146">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="65e77-147">ユーザー アクティビティの読み取りを設定するには、以前と同じ **MCDUserActivityChannel** インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="65e77-147">To set up User Activity reading, you use the same **MCDUserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="65e77-148">このインスタンスは **MCDUserActivitySessionHistoryItem** インスタンスを公開することができ、これは、特定のアクティビティにおける特定期間中のユーザーのエンゲージメントを表します。</span><span class="sxs-lookup"><span data-stu-id="65e77-148">This instance can expose **MCDUserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

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

<span data-ttu-id="65e77-149">この時点で、アプリには **MCDUserActivitySessionHistoryItem** の設定済みリストがあるはずです。</span><span class="sxs-lookup"><span data-stu-id="65e77-149">Now your app should have a populated list of **MCDUserActivitySessionHistoryItem** s.</span></span> <span data-ttu-id="65e77-150">これらはそれぞれ、基になる **MCDUserActivity** を提供でき (詳細は **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** を参照)、これをユーザーに表示することができます。</span><span class="sxs-lookup"><span data-stu-id="65e77-150">Each of these can deliver the underlying **MCDUserActivity** (see **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** for details), which you can then display to the user.</span></span>