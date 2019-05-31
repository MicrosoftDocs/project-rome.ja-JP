---
title: 発行およびユーザー アクティビティ (iOS) の読み取り
description: このガイドでは、作成、発行、および iOS アプリでの Windows ベースのユーザー アクティビティを読み取る方法を示します。
ms.topic: article
keywords: microsoft、windows、ローマ、ユーザー アクティビティ、ios をプロジェクトします。
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 3cc19463a5e036ab76288760aa70d86f1861675b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801674"
---
# <a name="implementing-user-activities-for-ios"></a>IOS 用のユーザー アクティビティの実装

ユーザー アクティビティとは、アプリケーション内のユーザーのタスクを表すデータ構造です。 これらによってようには後で続行するのには現在のタスクのスナップショットを保存します。 [Windows タイムライン](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/)機能では、スクロール可能なすべての最近のアクティビティの一覧、テキストとグラフィックス カードとして表される Windows ユーザーを表示します。 ユーザー アクティビティの詳細については一般に、表示[デバイス間であってもユーザーの利用状況を引き続き](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities)します。 活動を作成または更新する場合の推奨事項を参照してください、[ユーザー アクティビティのベスト プラクティス](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices)ガイド。

プロジェクト ローマ sdk では、iOS アプリではのみにユーザー アクティビティ タイムラインなどの Windows 機能で使用するために発行しないことができますが、エンドポイントとして機能、タイムラインと同様に、ユーザーにアクティビティを読み取ることができます。 これにより、クロス デバイス アプリ、プラットフォームとデバイスではなく、ユーザーの存在のエクスペリエンスを完全に克服できます。

プロジェクトのローマの機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームでサポートされます。 このガイドでは、接続されているデバイス プラットフォームの使用を開始するために必要な手順について説明し、プラットフォームを使用して、ユーザー アクティビティの関連機能を実装する方法を説明します。

この手順はからコードを参照、[プロジェクト ローマ iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)GitHub に用意されています。  

参照してください、 [API リファレンス](api-reference-for-ios.md)これらのシナリオに関連するリファレンス ドキュメントへのリンクについてのページ。

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>接続されているデバイス プラットフォームと通知を設定します。

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームを使用します。

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>ユーザー アクティビティのチャネルを初期化します。

アプリでは、ユーザー アクティビティの機能を実装するには、ユーザー アクティビティを MCDUserActivityChannel を作成してフィードを初期化する必要があります。 これを上記のプラットフォーム初期化手順のように扱う必要があります: チェックし、場合によって、アプリがフォア グラウンドに (ただし、プラットフォーム初期化前にいない) されるたびを再実行する必要があります。

サインイン ユーザーのアカウントは、この手順の必要があります。 上記としてに、MCDUserAccount(s) を簡単に取得するのに認証プロバイダーのサンプルからクラスを使用できます。 Microsoft 開発者向けダッシュ ボードの登録の過程で取得したクロス プラットフォーム アプリ ID を取得するも必要になります。
サンプル アプリから次のメソッドには、MCDUserActivityChannel を初期化します。

サンプル アプリから次のメソッドには、MCDUserActivityChannel を初期化します。

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
この時点では、チャネルで、MCDUserActivityChannel 参照が必要です。

### <a name="create-and-publish-a-user-activity"></a>作成して、ユーザー アクティビティを発行します。

次のサンプル コードに示す、新しい**MCDUserActivity**インスタンスが作成されます。

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

次のメソッドのビジュアルのデータで、 **MCDUserActivity**アクティビティを発行する前に設定されます。 アクティブ化の URI は、アクティビティが (たとえば、タイムラインで選択した) ときにアクティブになったときに実行するアクションを決定します。 表示テキスト表示されます他のデバイスで表示したとき (たとえば Windows タイムライン) のアクティビティ。 IconUri は、web リンク アイコン イメージです。


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

1 回、 **MCDUserActivity**設定は、このデータは、発行操作が行わします。

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
> 上記のプロパティでは、構成できるその他の多くの機能があります。 UserActivity をカスタマイズできるさまざまな方法の詳細について、次を参照してください、 **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)** 、 **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)。** 、 および **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** クラス。 参照してください、[ユーザー アクティビティのベスト プラクティス](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices)ユーザー アクティビティをデザインする方法の詳細な推奨事項のガイド。

## <a name="update-an-existing-user-activity"></a>既存のユーザー アクティビティを更新します。

既存のアクティビティ (新しい engagement、変更されたページで、およびなど) 発生時に、その情報を更新する場合、これを行うを使用して、 **MCDUserActivitySession**します。 

アプリのプロパティに、必要な変更を行うセッションを作成したら、 **UserActivity**します。 変更を完了すると、セッションを閉じます。 

サンプル アプリから次のメソッドは、オンとオフのセッションを切り替えます。

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


**MCDUserActivitySession**を作成する方法として考えることができます、 **MCDUserActivitySessionHistoryItem** (次のセクションで説明)。 新しいを作成するのではなく**MCDUserActivity**ページごとに新しいセッションを作成するユーザーは、新しいページに移動するたびに単純にできます。 これにより、読みやすいより直感的な構成されたアクティビティ。

## <a name="read-user-activities"></a>ユーザー アクティビティを読み取り

アプリは、ユーザー アクティビティを読み取るし、タイムラインの Windows 機能と同様、ユーザーに提示します。 同一のユーザー アクティビティの読み取りを設定するに使用する**MCDUserActivityChannel**前のインスタンス。 このインスタンスを公開できます**MCDUserActivitySessionHistoryItem**インスタンスで、ユーザーの関与を特定の期間中に、特定のアクティビティを表します。

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

アプリが設定されている一覧を指定する必要がありますので**MCDUserActivitySessionHistoryItem**秒。 基になるこれらの各配信できます **MCDUserActivity** (を参照してください **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** 詳細については)、これをユーザーに表示できます。
