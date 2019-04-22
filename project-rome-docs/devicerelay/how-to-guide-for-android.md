---
title: コマンドのリモート デバイスとアプリ (Android)
description: このガイドでは、リモート デバイスとアプリを検出してアプリを起動し、またはアプリ サービスと対話する方法を説明します。
ms.topic: article
keywords: microsoft、windows、プロジェクト、ローマをコマンド、android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: 78cb712d3b1cbbd3d613a45cd42af491eaa33afc
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907764"
---
# <a name="implementing-device-relay-for-android"></a>Android 用のデバイスのリレーの実装

プロジェクト ローマのデバイスのリレー機能は、2 つの主な機能をサポートする Api のセットで構成されています。 リモートの起動 (コマンドの実行とも呼ばれます) と app services。

リモート起動の Api は、ローカル デバイスからリモート デバイス上のプロセスが開始されるシナリオをサポートします。 たとえば、ユーザーは、携帯電話、車のラジオをリッスンする可能性がありますが自宅のステレオにフックされているが、Xbox に再生を転送する電話を使用するホーム取得すると。

App Services Api により、任意のコンテンツを含むメッセージを送信できる 2 つのデバイス間で永続的なパイプラインを確立するために使用できます。 などの写真をモバイル デバイスで実行されているアプリを共有では、写真を取得するために、ユーザーの PC に接続を確立する可能性があります。

プロジェクトのローマの機能は、接続されているデバイス プラットフォームと呼ばれる、基になるプラットフォームでサポートされます。 このガイドは、接続されているデバイス プラットフォームの使用を開始するために必要な手順について説明し、プラットフォームを使用して、デバイスのリレーを実装する方法を説明します機能に関連します。

この手順はからコードを参照、[プロジェクト ローマ Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)します。

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームを使用します。

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>リモート デバイスとアプリを検出します。

A **RemoteSystemWatcher**インスタンスは、このセクションのコア機能を処理します。 リモート システムを検出するには、クラスで宣言します。

```Java
private RemoteSystemWatcher mWatcher = null;
```

ウォッチャーを作成して、デバイスの検出を開始する前にどのような種類のデバイスのアプリの対象を決定する検索フィルターを追加したい場合があります。 これらは、ユーザーの入力またはユース ケースに応じて、アプリにハードコーディングで決定できます。

```Java
private void onStartWatcherClicked() {
    // RemoteSystemWatcher cannot be started unless the platform is 
    // initialized and the user is logged in. It may be helpful to use
    // methods like these to track the state of the application.
    // See the sample app for their implementations.
    if (!getMainActivity().isSignedIn()) {
        return;
    }
    if (!getMainActivity().isPlatformInitialized()) {
        return;
    }

    // create and populate a list of filters. The filter choices below are arbitrary.
    ArrayList<RemoteSystemFilter> filters = new ArrayList<>();

    /*  RemoteSystemDiscoveryType filters can be used to filter the types of Remote Systems you discover.
    Possible values:
        ANY(0),
        PROXIMAL(1),
        CLOUD(2),
        SPATIALLY_PROXIMAL(3)
    */
    filters.add(new RemoteSystemDiscoveryTypeFilter(RemoteSystemDiscoveryType.ANY));

    /*  RemoteSystemStatusType filters can be used to filter the status of Remote Systems you discover.
    Possible values:
        ANY(0),
        AVAILABLE(1)
    */
    filters.add(new RemoteSystemStatusTypeFilter(RemoteSystemStatusType.AVAILABLE));


    /*  RemoteSystemKindFilter can filter the types of devices you want to discover.
    Possible values are members of the RemoteSystemKinds class.
    */
    String[] kinds = new String[] { RemoteSystemKinds.Phone(), RemoteSystemKinds.Tablet() };

    RemoteSystemKindFilter kindFilter = new RemoteSystemKindFilter(kinds);
    filters.add(kindFilter);

    /*  RemoteSystemAuthorizationKind determines the category of user whose system(s) you want to discover.
    Possible values:
        SAME_USER(0),
        ANONYMOUS(1)
    */
    filters.add(new RemoteSystemAuthorizationKindFilter(RemoteSystemAuthorizationKind.SAME_USER)); 
    // ...
```

この時点では、アプリは、アプリが解析し、検出されたデバイスと対話する方法を決定する監視オブジェクトを初期化できます。

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

アプリが検出されたデバイスのセットを保持することをお勧め (によって表される**RemoteSystem**インスタンス) と、UI で使用可能なデバイスと (表示名とデバイスの種類) などのアプリに関する情報を表示します。 

次のクラスのスタブは、watcher のインスタンスのイベント リスナーとして使用できます。

```Java
private class RemoteSystemAddedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // add instance "remoteSystem" to program memory. See sample for full implementation.
    }
}

private class RemoteSystemUpdatedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // update instance "remoteSystem" in program memory. See sample for full implementation.
    }
}

private class RemoteSystemRemovedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // remove instance "remoteSystem" from program memory. See sample for full implementation.
    }
}

private class RemoteSystemWatcherErrorOccurredListener implements EventListener<RemoteSystemWatcher, RemoteSystemWatcherError> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystemWatcherError remoteSystemWatcherError) {
        // handle the error
    }
}
```

1 回`mWatcher.start`が呼び出されると、リモート システムの使用状況の監視を開始してデバイスの検出、更新、または検出されたデバイスのセットから削除されるときにイベントを発生させます。 これはスキャン継続的に、バック グラウンドでため不要なネットワーク通信とバッテリの消耗を回避するためにこれが不要になったときに、監視を停止することをお勧めします。

```Java
// if you call this from the activity's onPause method, you ensure that
// it will stop when the activity exits the foreground.
public void stopWatcher() {
    if (mWatcher == null) {
        return;
    }
    mWatcher.stop();
}
```
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>ユース ケースの例: リモート起動して、リモート アプリ サービスを実装します。

この時点で、コードにしておくの作業一覧**RemoteSystem**使用可能なデバイスを参照するオブジェクト。 これらのデバイスで何は、アプリの機能によって異なります。 相互作用の主な型では、リモート起動してリモート アプリのサービスが。 これらは、次のセクションで説明します。

### <a name="a-remote-launching"></a>A) リモート起動

次のコードは、これらのデバイス (理想的にはこれは、UI コントロールを介して) のいずれかを選択し、使用する方法を示しています。 **RemoteLauncher**を、アプリと互換性のある URI を渡すことによって、上のアプリを起動します。 

リモートからの起動 (である場合、ホスト デバイスが起動する URI スキーム用の既定のアプリで指定された URI) リモート デバイスを対象にできることを確認することが重要_または_にそのデバイスにリモート アプリケーションを特定します。 

検出をデバイス レベルで最初に実行前のセクションで示したように、(、 **RemoteSystem**デバイスを表します)、呼び出すことができますが、`getApplications`メソッドを**RemoteSystem**インスタンスを取得する、配列**RemoteSystemApp** (上記の準備手順では、独自のアプリを登録) と同様に、接続されているデバイス プラットフォームを使用する登録されているリモート デバイスでアプリを表すオブジェクト。 両方**RemoteSystem**と**RemoteSystemApp**作成に使用できます、 **RemoteSystemConnectionRequest**URI の起動に必要なものであります。

```java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the launch operation
// is called.
private RemoteSystem target; 

// ...

/**
* Responsible for calling into the Rome API to launch the given URI and provides
* the logic to handle the RemoteLaunchUriStatus response.
* @param uri URI to launch
* @param target The target for the launch URI request
*/
private void launchUri(final String uri, final RemoteSystem target, final long messageId)
{
    RemoteLauncher remoteLauncher = new RemoteLauncher();

    AsyncOperation<RemoteLaunchUriStatus> resultOperation = remoteLauncher.launchUriAsync(new RemoteSystemConnectionRequest(target), uri);
    // ...
```
使用して、返された**AsyncOperation**起動試行の結果を処理します。

```Java
    // ...
    resultOperation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<RemoteLaunchUriStatus, Throwable>() {
        @Override
        public void accept(RemoteLaunchUriStatus status, Throwable throwable) throws Throwable {
            if (throwable != null) {
                // handle the exception, referencing "throwable"
            } else {
                if (status == RemoteLaunchUriStatus.SUCCESS) {
                    // report the success case
                } else {
                    // report the non-success case, referencing "status"
                }
            }
        }
    });
}
```
によって送信される URI は、特定の状態またはリモート デバイス上の構成でのアプリを起動できます。 これにより、中断することがなく別のデバイスで映画を見てなど、ユーザーのタスクを継続する能力。 

ユース ケースに応じてを対象となるシステム上のアプリを取り扱うことが、URI の場合を対象にする必要があります。 または複数のアプリで処理できます。 **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** クラスと**[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** クラスは、これを行う方法を説明します。

### <a name="b-remote-app-services"></a>B) リモート アプリ サービス

Android アプリで接続されているデバイス ポータルを使用できるその他のデバイス上の app services と対話します。 これにより、他のデバイスと通信する方法は多数&mdash;ホスト デバイスの前面にアプリを表示する必要はありませんすべて。 

#### <a name="set-up-the-app-service-on-the-target-device"></a>ターゲット デバイスでアプリ サービスをセットアップする
このガイドを使用して、 [Roman テスト アプリの Windows](http://aka.ms/romeapp)そのターゲット アプリケーションのサービスとして。 そのため、次のコードは、特定のリモート システムでは、その特定のアプリ サービスを検索する Android アプリになります。 このシナリオをテストする場合は、Windows デバイスで Roman テスト アプリをダウンロードし、同じ MSA または前の準備手順で使用する AAD でサインインしているかどうかを確認します。 

UWP アプリ サービスを作成する方法に関する手順については、次を参照してください。[を作成する (UWP) アプリ サービスの使用と](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)します。 接続されたデバイスと互換性のあるサービスを作成するには、いくつか変更する必要があります。 参照してください、[リモート アプリ サービスの UWP ガイド](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)これを行う方法の詳細について。 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>クライアント デバイスにアプリ サービスの接続を開く
Android アプリでは、リモート デバイスまたはアプリケーションへの参照を取得する必要があります。 このシナリオの起動セクションなどを使用する必要を**RemoteSystemConnectionRequest**、いずれかから構築できますが、 **RemoteSystem**または**RemoteSystemApp**システムで利用可能なアプリを表します。


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
アプリは 2 つの文字列を使用して、対象となるアプリ サービスを特定する必要がありますさらに、: *app service の名前*と*パッケージ識別子*します。 アプリのサービス プロバイダーのソース コードにあるこれらは (を参照してください[を作成する (UWP) アプリ サービスの使用と](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)Windows app services についてこの文字列を取得する方法の詳細について)。 これらの文字列を構築して、 **AppServiceDescription**にフィードするが、 **AppServiceConnection**インスタンス。

```Java
// this is defined below
private AppServiceConnection connection = null; 


/**
* Creates an AppService connection with the current identifier and service name and opens the
* app service connection.
*/
private void onNewConnectionButtonClicked()
{
    connection = new AppServiceConnection();

    // these hard-coded strings must be defined elsewhere in the app
    connection.setAppServiceDescription(new AppServiceDescription(mAppServiceName, mPackageIdentifier));

    // this method is defined below
    openAppServiceConnection();
}
```
```Java
/**
* Establish an app service connection.
* Opens the given AppService connection using the connection request. Once the connection is
* opened, it adds the listeners for request-received and close. Catches all exceptions
* to show behavior of API surface exceptions.
*/
private void openAppServiceConnection()
{
    // optionally report outbound request
    // ...

    RemoteSystemConnectionRequest connectionRequest = new RemoteSystemConnectionRequest(target));

    /* Will asynchronously open the app service connection using the given connection request
    * When this is done, we log the traffic in the UI for visibility to the user (for sample purposes)
    * We can check the status of the connection to determine whether or not it was successful, and show 
    * some UI if it wasn't (in this case it is part of the list item).
    */
    connection.openRemoteAsync(connectionRequest)
        .thenAcceptAsync(new AsyncOperation.ResultConsumer<AppServiceConnectionStatus>() {
            @Override
            public void accept(AppServiceConnectionStatus appServiceConnectionStatus) throws Throwable {
                // optionally report inbound response
                // ...

                if (appServiceConnectionStatus != AppServiceConnectionStatus.SUCCESS) {
                    // report the error, referencing "appServiceConnectionStatus"
                    return;
                }
            }
        })
        .exceptionally(new AsyncOperation.ResultFunction<Throwable, Void>() {
            @Override
            public Void apply(Throwable throwable) throws Throwable {
                // report the exception
                return null;
            }
        });
}
```

#### <a name="create-a-message-to-send-to-the-app-service"></a>App service に送信するメッセージを作成します。

送信するメッセージを格納する変数を宣言します。 Android では、リモート アプリ サービスに送信するメッセージはで、**マップ**型。

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> 接続されているデバイス プラットフォームを変換、アプリが他のプラットフォーム上の app services を通信する場合、**マップ**受信側のプラットフォームに一致するコンス トラクターにします。 たとえば、 **[マップ](https://developer.android.com/reference/java/util/Map)** アプリ サービスに変換します Windows にこのアプリから送信される、 [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) (.NET Framework にある) のオブジェクト。これは、app service でし解釈できます。 その他の方向に渡された情報には、逆の変換が行われます。

次のメソッドは、Windows 用の欧文テスト アプリの app service で解釈できるメッセージを作成します。

```Java
/**
* Send the current message payload through all selected AppService connections on a non-UI
* thread as to not block user interaction, a result of the delay between API calls.
*/
private void onMessageButtonClicked()
{
    mMessagePayload = new HashMap<>();
    // Add the required fields of RomanApp on Windows
    DateFormat df = new SimpleDateFormat(DATE_FORMAT);
    mMessagePayload.put("Type", "ping");
    mMessagePayload.put("CreationDate", df.format(new Date()));
    mMessagePayload.put("TargetId", "check if this field needs to be included");

    // this method is defined below.
    sendMessage(connection, mMessagePayload);
}
```

> [!IMPORTANT]
> **マップ**アプリとアプリのリモート サービスのシナリオでのサービス間で渡されることは、次の形式に従う必要があります。キーは、文字列である必要があり、値があります。文字列、ブール値、android.graphics.Point、android.graphics.Rect、java.util.Date、java.util.UUID、これらの型、またはその他のいずれかの同種の配列 (整数または浮動小数点)、ボックス化された数値の型がボックス化**マップ**オブジェクトこの仕様を満たしています。

#### <a name="send-message-to-the-app-service"></a>App service へのメッセージを送信します。

アプリ サービスの接続が確立され、メッセージが作成された、app service に送信は単純なとでアプリを app service の接続インスタンスおよびメッセージへの参照を持つ任意の場所から実行できます。


```java

// When assigning message IDs, use an incremental counter
private AtomicInteger mMessageIdAppServices = new AtomicInteger(0);

// ...

/**
* Send a message using the app service connection
* Send the given Map object through the given AppServiceConnection. Uses an internal messageId
* for logging purposes.
* @param connection AppServiceConnection to send the Map payload
* @param message Payload to be translated to a ValueSet
*/
private void sendMessage(final AppServiceConnection connection, Map<String, Object> message)
{
    final long messageId = mMessageIdAppServices.incrementAndGet();

    connection.sendMessageAsync(message)
        .thenAcceptAsync(new AsyncOperation.ResultConsumer<AppServiceResponse>() {
            @Override
            public void accept(AppServiceResponse appServiceResponse) throws Throwable {
                // optionally report an inbound response

                // this method is defined below
                handleAppServiceResponse(appServiceResponse, messageId);
            }
        })
        .exceptionally(new AsyncOperation.ResultFunction<Throwable, Void>() {
            @Override
            public Void apply(Throwable throwable) throws Throwable {
                // report the exception, referencing "throwable"

                return null;
            }
        });

    // optionally log the outbound message request here, referencing 
    // connection.getAppServiceDescription().getName() as the recipient.
}
```

アプリ サービスの応答を受信して、次の方法で解釈されます。

```Java
private void handleAppServiceResponse(AppServiceResponse appServiceResponse, long messageId)
{
    AppServiceResponseStatus status = appServiceResponse.getStatus();
    if (status == AppServiceResponseStatus.SUCCESS)
    {
        // the message was delivered successfully; interpret the response.
        Map<String, Object> response;
        response = appServiceResponse.getMessage();

        // in the Roman App case, the response contains the date it was created.
        String dateStr = (String)response.get("CreationDate");
        DateFormat df = new SimpleDateFormat(DATE_FORMAT, Locale.getDefault());

        // in this very simple use case, we compare the dates to get the total
        // transit time of the message response.
        try {
            Date startDate = df.parse(dateStr);
            Date nowDate = new Date();
            long diff = nowDate.getTime() - startDate.getTime();
            // do something with "diff"
        } catch (ParseException e) { e.printStackTrace(); }
    }
}
```
ローマ アプリの場合、応答には、この非常に単純なユース ケースでは、メッセージの応答の転送中の合計時間を取得する日付を比較できるように、作成された日付が含まれます。

これは、リモート アプリ サービスで、1 つのメッセージ交換を終了します。

#### <a name="finish-app-service-communication"></a>アプリ サービスの通信を完了します。

アプリが終了すると、ターゲット デバイスのアプリのサービスと対話する 2 つのデバイス間の接続を閉じます。

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a>関連トピック
* [API リファレンスのページ](api-reference-for-android.md) 
* [Android のサンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [(UWP) アプリのリモート サービスと通信します。](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [作成し、app service (UWP) を使用する](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)します。
