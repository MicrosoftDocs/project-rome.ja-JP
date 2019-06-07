---
title: インクルード ファイル
description: インクルード ファイル
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b8a0de450431adce084919290d49f6326d23d51b
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755796"
---
### <a name="set-up-authentication-and-account-management"></a>認証とアカウントの管理を設定します。

接続されているデバイス プラットフォームでは、登録プロセスで使用される有効な OAuth トークンが必要です。  ご希望の生成と OAuth トークンを管理する方法を使用することがあります。  ただし、ため開発者は、プラットフォームの使用を開始、認証プロバイダーの一部として含まれています、 [iOS サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample)を生成し、アプリでの更新トークンの管理を行えます。

提供されたコードを使用しない場合は、実装する必要があります。、 **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** インターフェイスを自分でします。

MSA を使用している場合は、サインイン要求に、次のスコープを含める: `"wl.offline_access"`、 `"ccs.ReadWrite"`、 `"dds.read"`、 `"dds.register"`、 `"wns.connect"`、 `"asimovrome.telemetry"`、および`"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`します。

> [!NOTE]
> デバイスの Relay Api では、azure Active Directory (AAD) アカウントはサポートされていません。

AAD アカウントを使用している場合は次のユーザーを要求する必要があります: `"https://cdpcs.access.microsoft.com"`、 `"https://cs.dds.microsoft.com"`、 `"https://wns.windows.com/"`、および`"https://activity.microsoft.com"`します。

指定されたを使用するかどうか**MCDConnectedDevicesAccountManager**実装または AAD アプリの登録、Azure portal で次のアクセス許可を指定する必要がありますを使用している場合、not (portal.azure.com >Azure Active Directory > アプリの登録)。
* Microsoft アクティビティ フィードのサービス 
  * 配信し、このアプリのユーザー通知の変更
  * 読み取りおよび書き込みユーザーのアクティビティ フィードにアプリの動作
* Windows 通知サービス
  * デバイスを Windows 通知サービスに接続します。 
* デバイスの Microsoft ディレクトリ サービス
  * デバイスの一覧を参照してください。
  * デバイスとアプリの一覧に追加します。 
* Microsoft Command サービス
  * ユーザーのデバイスと通信します。
  * ユーザー デバイスを読み取り
