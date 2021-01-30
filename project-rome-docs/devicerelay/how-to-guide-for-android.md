---
title: リモートのデバイスとアプリのコマンド実行 (Android)
description: このガイドでは、リモートのデバイスやアプリを検出してから、アプリを起動したり、アプリ サービスと対話したりする方法について説明します。
ms.topic: article
keywords: microsoft, windows, project rome, コマンド実行, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: ce261c6571e4606ddcb8e1c2b75d989db51d8d9f
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901573"
---
# <a name="implementing-device-relay-for-android"></a>Android のデバイス リレーの実装

Project Rome のデバイス リレー機能は、2 つの主な機能であるリモート起動 (コマンド実行とも呼びます) とアプリ サービスをサポートする一連の API で構成されています。

リモート起動 API は、リモート デバイス上のプロセスがローカル デバイスから開始されるシナリオをサポートします。 たとえば、ユーザーが車に乗りながら電話でラジオを聴きますが、帰宅したらホーム ステレオに接続した Xbox に電話を使用して再生を転送することがあります。

アプリケーションは App Services API を使用して 2 つのデバイス間に永続的なパイプラインを確立し、任意の内容を含むメッセージをこのパイプライン経由で送信することができます。 たとえば、モバイル デバイス上で実行されている写真共有アプリが、写真を取得するためにユーザーの PC との接続を確立することができます。

Project Rome の機能は、Connected Devices Platform と呼ばれる基盤プラットフォームによってサポートされます。 このガイドでは、Connected Devices Platform を初めて使用するために必要な手順と、このプラットフォームを使用してデバイス リレー関連機能を実装する方法について説明します。

この手順では、[Project Rome Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)のコードを参照します。

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>プラットフォームの使用

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>リモートのデバイスとアプリの検出

**RemoteSystemWatcher** インスタンスは、このセクションのコア機能を処理します。 これは、リモート システムを検出するクラスの中で宣言します。

```Java
private RemoteSystemWatcher mWatcher = null;
```

ウォッチャーを作成してデバイスの検出を開始する前に、検出フィルターを追加して、どのような種類のデバイスをアプリでターゲットにするかを決定することができます。 ユース ケースに応じて、これらはユーザーの入力によって決定、またはアプリにハードコードすることができます。

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

この時点で、アプリはウォッチャー オブジェクトを初期化できます。これによって、検出されたデバイスをアプリで解析する方法、またそれらのデバイスとアプリが対話する方法が決まります。

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

(**RemoteSystem** インスタンスで表される) 検出されたデバイスのセットをアプリで管理し、利用可能なデバイスとそのアプリについての情報 (表示名やデバイスの種類など) を UI に表示することをお勧めします。 

次のクラス スタブは、ウォッチャー インスタンスのイベント リスナーとして使用できます。

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

`mWatcher.start` が呼び出されると、リモート システムのアクティビティの監視が始まります。デバイスが検出、更新、または検出済みデバイスのセットから削除されると、イベントが発生します。 バックグラウンドで継続的にスキャンされるため、不必要なネットワーク通信やバッテリの消耗を避けるために、不要になったらウォッチャーを停止することをお勧めします。

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
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>ユース ケースの例: リモート起動とリモート アプリ サービスの実装

コードのこの時点で、利用可能なデバイスを参照する **RemoteSystem** オブジェクトの有効な一覧があるはずです。 これらのデバイスに対して何をするかは、アプリの機能によって異なります。 主な種類の対話は、リモート起動とリモート アプリ サービスです。 これらについては、以降のセクションで説明します。

### <a name="a-remote-launching"></a>A) リモート起動

次のコードは、これらのデバイスのいずれかを選択し (UI コントロールを使って行われるのが理想的です)、**RemoteLauncher** を使用して、アプリと互換性のある URI を渡してそのデバイス上でアプリを起動する方法を示しています。 

重要な注意点として、リモート起動でターゲットにできるのはリモート デバイス _または_ そのデバイス上の特定のリモート アプリケーションであり、前者の場合、指定された URI を、ホスト デバイスがその URI スキーム用の既定のアプリで起動します。 

前のセクションで説明したように、検出はまずデバイス レベルで行われます (**RemoteSystem** はデバイスを表します) が、**RemoteSystem** インスタンスの `getApplications` メソッドを呼び出して **RemoteSystemApp** オブジェクトの配列を取得することができます。これらのオブジェクトが表すのは、(前述の準備手順で独自のアプリを登録したのと同様に) Connected Devices Platform を使用するように登録されている、リモート デバイス上のアプリです。 **RemoteSystem** と **RemoteSystemApp** のどちらを使用しても、URI を起動するために必要な **RemoteSystemConnectionRequest** を作成できます。

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
起動試行の結果を処理するには、返された **AsyncOperation** を使用します。

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
送信する URI に応じて、特定の状態または構成でリモート デバイス上でアプリを起動できます。 これにより、映画を観るなどのユーザー タスクを、中断することなく別のデバイス上で継続することができます。 

ユース ケースによっては、ターゲット システム上のどのアプリも URI を処理できない、または複数のアプリがそれを処理できる状況への対応が必要な場合があります。 **[RemoteLauncher](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** クラスと **[RemoteLauncherOptions](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** クラスは、これを行う方法を説明します。

### <a name="b-remote-app-services"></a>B) リモート アプリ サービス

Android アプリは Connected Devices ポータルを使用して、他のデバイス上のアプリ サービスと対話できます。 これにより、他のデバイスと通信するための多くの方法が提供されます&mdash;アプリをホスト デバイスの前面に出す必要はまったくありません。 

#### <a name="set-up-the-app-service-on-the-target-device"></a>ターゲット デバイスでアプリ サービスを設定する
このガイドでは、[Windows 用の Roman テスト アプリ](https://aka.ms/romeapp)をターゲット アプリ サービスとして使用します。 したがって、次のコードにより、Android アプリは特定のリモート システム上でその特定のアプリ サービスを探します。 このシナリオをテストする場合は、Windows デバイス上で Roman テスト アプリをダウンロードし、先の準備手順で使用したのと同じ MSA でサインインしていることを確認してください。 

独自の UWP アプリ サービスを記述する方法については、[アプリ サービスの作成と利用 (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) に関するページを参照してください。 サービスに Connected Devices との互換性を持たせるために、いくつかの変更を加える必要があります。 これを行う方法については、[リモート アプリ サービスに関する UWP ガイド](/windows/uwp/launch-resume/communicate-with-a-remote-app-service)を参照してください。 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>クライアント デバイス上でアプリ サービス接続を開く
Android アプリは、リモートのデバイスまたはアプリケーションへの参照を取得する必要があります。 起動のセクションと同様、このシナリオでは **RemoteSystemConnectionRequest** を使用する必要があります。これは **RemoteSystem** から、またはシステム上の利用可能なアプリを表す **RemoteSystemApp** から作成できます。


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
さらにアプリは、*アプリ サービス名* と *パッケージ識別子* の 2 つの文字列を使用して、そのターゲットであるアプリ サービスを識別する必要があります。 これらはアプリ サービス プロバイダーのソース コードに含まれています。この文字列を Windows アプリ サービス用に取得する方法については、[アプリ サービスの作成と利用 (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) に関するページを参照してください。 これらの文字列が合わさって **AppServiceDescription** になり、これが **AppServiceConnection** インスタンスに渡されます。

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

#### <a name="create-a-message-to-send-to-the-app-service"></a>アプリ サービスに送信するメッセージの作成

送信するメッセージを格納する変数を宣言します。 Android では、リモート アプリ サービスに送信するメッセージは **Map** 型になります。

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> アプリが他のプラットフォーム上のアプリ サービスと通信するとき、Connected Devices Platform はこの **Map** を受信側プラットフォームでそれに対応するコンストラクトに変換します。 たとえば、このアプリから Windows アプリ サービスに送信される **[Map](https://developer.android.com/reference/java/util/Map)** は、アプリ サービスが解釈できる (.NET Framework の) [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) オブジェクトに変換されます。 反対方向に渡される情報には、逆の変換が行われます。

次のメソッドは、Windows 用の Roman テスト アプリのアプリ サービスによって解釈できるメッセージを作成します。

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
> リモート アプリ サービスのシナリオでアプリとサービスの間で受け渡しされる **Map** は、次の形式に従う必要があります。キーは文字列である必要があり、次の値を入れることができます: 文字列、ボックス数値型 (整数または浮動小数点数)、ボックス ブール値、android.graphics.Point、android.graphics.Rect、java.util.Date、java.util.UUID、上記いずれかの型と同種の配列、またはこの仕様を満たすその他の **Map** オブジェクト。

#### <a name="send-message-to-the-app-service"></a>アプリ サービスにメッセージを送信する

アプリ サービス接続が確立されてメッセージが作成されたら、それをアプリ サービスに送信するのは簡単であり、そのアプリ サービス接続インスタンスとメッセージへの参照があるアプリ内のどこからでも実行できます。


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

アプリ サービスの応答は、次のメソッドによって受信および解釈されます。

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
Roman アプリの場合、応答にはそれが作成された日付が含まれているため、この非常に単純なユース ケースでは、日付を比較してメッセージ応答の合計転送時間を取得できます。

これで、リモート アプリ サービスとの 1 回のメッセージ交換が終了します。

#### <a name="finish-app-service-communication"></a>アプリ サービス通信の終了

アプリがターゲット デバイスのアプリ サービスとの対話を終了したら、2 つのデバイス間の接続を閉じます。

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a>関連トピック
* [API リファレンス ページ](api-reference-for-android.md) 
* [Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [リモート アプリ サービスとの通信 (UWP)](/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [アプリ サービスの作成と利用 (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)