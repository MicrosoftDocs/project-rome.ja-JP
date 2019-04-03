### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Microsoft Windows デベロッパー センターでのクロス デバイス エクスペリエンスのアプリを登録します。
次に、アプリケーションを登録する必要があります、[クロス デバイス エクスペリエンスの機能、Microsoft 開発者向けダッシュ ボードの](https://developer.microsoft.com/dashboard/crossplatform/web)します。 これは、上記の手順で説明した MSA と AAD のアプリ登録から別のプロシージャです。 このプロセスの主な目的は、接続されているデバイス プラットフォームによって認識され、同時に、ネイティブを使用して通知を送信する Microsoft Graph の通知を承認するクロス プラットフォーム アプリの id によるプラットフォームの特定のアプリ id にマップするにはプッシュ通知サービスが OS プラットフォームごとに対応します。 この場合、グラフの通知 WNS – Windows Notification Service を使用して Windows UWP アプリのエンドポイントに通知を送信することができます。 Dev Center のダッシュ ボードに移動して、左側にあるナビゲーション ウィンドウで、クロス デバイス エクスペリエンスに移動して次のように示すように、新しいクロス デバイス アプリの構成を選択します。
![デベロッパー センター ダッシュ ボード-クロス デバイス エクスペリエンス](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

デベロッパー センターで、オンボード プロセスには、次の手順が必要です。
* サポートされているプラットフォームを選択します: アプリが存在する必要があり、クロス デバイス エクスペリエンスを有効にするプラットフォームを選択します。 グラフの通知の統合の場合は、Windows、Android、および iOS から選択できます。 次のように表示されます。
![クロス デバイス エクスペリエンス: サポートされているプラットフォーム](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* アプリ Id を提供: 各アプリが、プレゼンスがプラットフォームにアプリ Id を提供します。 次のように表示されます。
![クロス デバイス エクスペリエンス: アプリ Id](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> プラットフォームごと (最大 10 個) の異なる Id を追加することがあります-これは、同じアプリ、または異なる場合でも、同じユーザーを対象としたアプリケーション サーバーによって送信された同じ通知を受信できるようにアプリの複数のバージョンがある場合、します。 

* 指定するか、MSA または AAD アプリの登録からアプリ Id を選択します。 MSA または AAD アプリの登録に対応するこれらのクライアント Id は、上記の前の MSA/AAD アプリ登録の手順で取得されました。 次のように表示されます。 
![クロス デバイス エクスペリエンス: MSA と AAD アプリの登録](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)
* グラフの通知およびその他のデバイス プラットフォームの接続機能を活用して各クライアントのエンドポイント、つまり、アプリに通知を送信する WNS (Windows UWP) 用、GCM (Android) 用、および APNS (iOS 用の主要なプラットフォームでネイティブ通知プラットフォーム). これらの通知プラットフォームにユーザーを対象とした通知を発行するときに、アプリ サーバーの通知を配信するグラフの通知を有効にするための資格情報を提供します。 次のように表示されます。 
![クロス デバイス エクスペリエンス: プッシュの資格情報](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Windows UWP アプリの場合は、Microsoft Graph の通知を使用する前提条件が WNS プッシュ通知を有効にします。 参照してください[WNS 概要](https://docs.microsoft.com/en-us/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview)の詳細。 オンボードを完了すると接続されているデバイス プラットフォームに Windows デベロッパー センターを使用してプッシュの資格情報を提供できます。 
* 最後の手順では、アプリではこのドメインの所有権に登録されているアプリのクロス デバイス アプリ id のように機能することを証明する検証プロセスとして機能するクロス デバイス アプリ ドメインを確認します。 次のように表示されます。  
![クロス デバイス エクスペリエンス: ドメインの確認](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)オンボードのすべての設定できるようになった。 次のセクションに進んでください。 


