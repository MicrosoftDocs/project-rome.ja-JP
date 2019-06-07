---
title: インクルード ファイル
description: インクルード ファイル
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: a6e92df6114443827b22dc85cf877d631e5fcfdf
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755785"
---
### <a name="set-up-authentication-and-account-management"></a>認証とアカウントの管理を設定します。

接続されているデバイス プラットフォームでは、登録プロセスで使用される有効な OAuth トークンが必要です。  ご希望の生成と OAuth トークンを管理する方法を使用することがあります。  ただし、ため開発者は、プラットフォームの使用を開始、認証プロバイダーの一部として含まれています、 [Android サンプル アプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)を生成し、必要に応じて更新トークンを管理します。

実装する場合、 **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** インターフェイスを自分で、次の情報をメモしておきます。 

MSA を使用している場合は、サインイン要求に、次のスコープを含める必要があります。: `"wl.offline_access"`、 `"ccs.ReadWrite"`、 `"dds.read"`、 `"dds.register"`、 `"wns.connect"`、 `"asimovrome.telemetry"`、および`"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`します。 

AAD アカウントを使用している場合は次のユーザーを要求する必要があります: `"https://cdpcs.access.microsoft.com"`、 `"https://cs.dds.microsoft.com"`、 `"https://wns.windows.com/"`、および`"https://activity.microsoft.com"`します。

> [!NOTE]
> デバイスの Relay Api では、azure Active Directory (AAD) アカウントはサポートされていません。

指定されたを使用するかどうか**ConnectedDevicesAccountManager**実装または AAD アプリの登録、Azure portal で次のアクセス許可を指定する必要がありますを使用している場合、not (portal.azure.com > AzureActive Directory > アプリの登録)。 
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
