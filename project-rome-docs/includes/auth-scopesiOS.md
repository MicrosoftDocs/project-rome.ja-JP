---
title: インクルード ファイル
description: インクルード ファイル
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b8a0de450431adce084919290d49f6326d23d51b
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755796"
---
### <a name="set-up-authentication-and-account-management"></a>認証とアカウント管理の設定

Connected Devices Platform では、有効な OAuth トークンを登録プロセスで使用する必要があります。  OAuth トークンの生成および管理には任意の方法を使用できます。  ただし、プラットフォームを初めて使用する開発者を支援するために、アプリで更新トークンの生成と管理に使用できる認証プロバイダーを [iOS サンプルアプリ](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample)の一部として含めています。

提供されたコードを使用しない場合、 **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** インターフェイスを自身で実装する必要があります。

MSA を使用している場合、サインイン要求に次のスコープを含めます: `"wl.offline_access"`、`"ccs.ReadWrite"`、`"dds.read"`、`"dds.register"`、`"wns.connect"`、`"asimovrome.telemetry"`、および `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`。

> [!NOTE]
> Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。

AAD アカウントを使用している場合、次の対象ユーザーを要求する必要があります: `"https://cdpcs.access.microsoft.com"`、`"https://cs.dds.microsoft.com"`、`"https://wns.windows.com/"`、および `"https://activity.microsoft.com"`。

提供されている **MCDConnectedDevicesAccountManager** の実装を使用するかどうかにかかわらず、AAD を使用している場合は、Azure portal のアプリの登録 (portal.azure.com > [Azure Active Directory] > [アプリの登録]) で次のアクセス許可を指定する必要があります。
* Microsoft アクティビティ フィード サービス 
  * このアプリのユーザー通知を配信および変更する
  * アプリのアクティビティを読み取ってユーザーのアクティビティ フィードに書き込む
* Windows 通知サービス
  * デバイスを Windows 通知サービスに接続する 
* Microsoft デバイス ディレクトリ サービス
  * デバイスの一覧を参照する
  * デバイスとアプリの一覧に追加される 
* Microsoft コマンド サービス
  * ユーザー デバイスと通信する
  * ユーザー デバイスを読み取る
