---
title: インクルード ファイル
description: インクルード ファイル
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b81da462f97569d322b76ebff36f800c970c06cc
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901571"
---
### <a name="set-up-authentication-and-account-management"></a>認証とアカウント管理の設定

Connected Devices Platform では、有効な OAuth トークンを登録プロセスで使用する必要があります。  OAuth トークンの生成および管理には任意の方法を使用できます。  ただし、プラットフォームを初めて使用する開発者を支援し、利便性を高めるために、更新トークンを生成および管理する認証プロバイダーを [Android サンプルアプリ](https://github.com/Microsoft/project-rome/tree/master/Android/samples)の一部として含めています。

**[ConnectedDevicesAccountManager](/java/api/com.microsoft.connecteddevices.core._user_account_provider)** インターフェイスを独自に実装する場合は、次の情報に留意してください。 

MSA を使用している場合、サインイン要求に次のスコープを含める必要があります: `"wl.offline_access"`、`"ccs.ReadWrite"`、`"dds.read"`、`"dds.register"`、`"wns.connect"`、`"asimovrome.telemetry"`、および `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`。 

AAD アカウントを使用している場合、次の対象ユーザーを要求する必要があります: `"https://cdpcs.access.microsoft.com"`、`"https://cs.dds.microsoft.com"`、`"https://wns.windows.com/"`、および `"https://activity.microsoft.com"`。

> [!NOTE]
> Azure Active Directory (AAD) アカウントは、Device Relay API ではサポートされていません。

提供されている **ConnectedDevicesAccountManager** の実装を使用するかどうかにかかわらず、AAD を使用している場合は、Azure portal のアプリの登録 (portal.azure.com > [Azure Active Directory] > [アプリの登録]) で次のアクセス許可を指定する必要があります。 
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