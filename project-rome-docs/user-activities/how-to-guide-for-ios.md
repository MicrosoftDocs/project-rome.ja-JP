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
# <a name="implementing-user-activities-for-ios"></a>iOS のユーザー アクティビティの実装

ユーザー アクティビティは、アプリケーション内でのユーザーのタスクを表すデータ構造です。 現在のタスクのスナップショットを保存して後で続行することを可能にします。 [Windows タイムライン](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/)機能は Windows ユーザーに、ユーザーの最近のアクティビティすべてを、テキストとグラフィックスを使ったカードで表現したスクロール可能リストで表示します。 ユーザー アクティビティ全般の詳細については、[デバイス間でのユーザー アクティビティの継続](/windows/uwp/launch-resume/useractivities)に関する記事を参照してください。 アクティビティの作成または更新の推奨されるタイミングについては、[ユーザー アクティビティのベスト プラクティス](/windows/uwp/launch-resume/useractivities-best-practices) ガイドを参照してください。

iOS アプリは Project Rome SDK によって、タイムラインなどの Windows 機能で使用するユーザー アクティビティを発行できるだけでなく、エンドポイントとして機能して、タイムラインと同様にアクティビティをユーザーに読み戻すこともできます。 これによりクロスデバイス アプリは、プラットフォームの枠を完全に超えて、デバイスではなくユーザーをフォローするエクスペリエンスを提示することができます。

Project Rome の機能は、Connected Devices Platform と呼ばれる基盤プラットフォームによってサポートされます。 このガイドでは、Connected Devices Platform を初めて使用するために必要な手順と、このプラットフォームを使用してユーザー アクティビティ関連機能を実装する方法について説明します。

この手順では、GitHub から入手できる [Project Rome iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples)のコードを参照します。  

これらのシナリオに関連したリファレンス ドキュメントへのリンクは、[API リファレンス](api-reference-for-ios.md)のページを参照してください。

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Connected Devices Platform と通知の設定

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームの使用

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>ユーザー アクティビティ チャネルの初期化

ユーザー アクティビティ機能をアプリで実装するには、まず、MCDUserActivityChannel を作成することでユーザー アクティビティ フィードを初期化する必要があります。 これは、前述したプラットフォーム初期化手順のように扱う必要があります。(プラットフォーム初期化の前ではないタイミングで) アプリがフォアグラウンドになるたびにチェックし、場合によってはやり直す必要があります。

この手順にはサインインしたユーザー アカウントが必要になります。 上記のように、認証プロバイダー サンプルのクラスを使用して MCDUserAccount を簡単に取得できます。 Microsoft デベロッパー ダッシュボードへの登録時に取得したクロスプラットフォーム アプリ ID も必要になります。
サンプル アプリの次のメソッドは MCDUserActivityChannel を初期化します。

サンプル アプリの次のメソッドは MCDUserActivityChannel を初期化します。

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
この時点で、MCDUserActivityChannel の参照がチャネルにあるはずです。

### <a name="create-and-publish-a-user-activity"></a>ユーザー アクティビティの作成と発行

次のサンプル コードは、新しい **MCDUserActivity** インスタンスがどのように作成されるかを示しています。

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

次のメソッドでは、アクティビティが発行される前に **MCDUserActivity** の視覚的データが設定されます。 アクティブ化 URI は、アクティビティがアクティブ化されたとき (たとえば、タイムラインで選択されたとき) にどのようなアクションが実行されるかを決定します。 表示テキストは、(たとえば Windows タイムラインで) アクティビティを表示するときに他のデバイス上で表示されます。 iconUri はアイコン画像への Web リンクです。


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

このデータが **MCDUserActivity** に設定されると、発行操作が行われます。

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
> 上記のプロパティに加えて、他にも多くの機能を構成できます。 UserActivity のさまざまなカスタマイズ方法の詳細については、**[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**、**[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**、および **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** の各クラスを参照してください。 ユーザー アクティビティの設計方法に関する推奨事項の詳細については、[ユーザー アクティビティのベスト プラクティス](/windows/uwp/launch-resume/useractivities-best-practices) ガイドを参照してください。

## <a name="update-an-existing-user-activity"></a>既存のユーザー アクティビティの更新

既存のアクティビティがあり、(新しいエンゲージメントがあった、ページが変更されたなどの理由で) その情報を更新したい場合、**MCDUserActivitySession** を使用して行うことができます。 

セッションを作成したら、アプリで **UserActivity** のプロパティに必要な変更を加えることができます。 変更が完了したら、セッションを閉じます。 

サンプル アプリの次のメソッドは、セッションのオンとオフを切り替えます。

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


**MCDUserActivitySession** は、**MCDUserActivitySessionHistoryItem** (次のセクションで説明します) を作成する方法と考えることができます。 ユーザーが新しいページに移動するたびに新しい **MCDUserActivity** を作成する代わりに、ページごとに新しいセッションを作成するだけで済みます。 これにより、より直感的で整ったアクティビティ読み取りエクスペリエンスが実現します。

## <a name="read-user-activities"></a>ユーザー アクティビティの読み取り

アプリは Windows タイムライン機能と同様に、ユーザー アクティビティを読み取ってユーザーに表示できます。 ユーザー アクティビティの読み取りを設定するには、以前と同じ **MCDUserActivityChannel** インスタンスを使用します。 このインスタンスは **MCDUserActivitySessionHistoryItem** インスタンスを公開することができ、これは、特定のアクティビティにおける特定期間中のユーザーのエンゲージメントを表します。

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

この時点で、アプリには **MCDUserActivitySessionHistoryItem** の設定済みリストがあるはずです。 これらはそれぞれ、基になる **MCDUserActivity** を提供でき (詳細は **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** を参照)、これをユーザーに表示することができます。