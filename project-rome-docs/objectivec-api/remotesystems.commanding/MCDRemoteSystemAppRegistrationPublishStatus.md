---
title: MCDRemoteSystemAppRegistrationPublishStatus
description: URI を使用して、リモート アプリの起動の状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 32c3e473938925f12838bf6dc5ccc3e98a3394a6
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800584"
---
# <a name="enum-mcdremotesystemappregistrationpublishstatus"></a>列挙型 `MCDRemoteSystemAppRegistrationPublishStatus`

`typedef NS_ENUM(NSInteger, MCDRemoteSystemAppRegistrationPublishStatus)`

発行操作の状態を示す列挙です。
エラー状態では、アプリ開発者の発行を再試行する必要のある一時的な状態を示します。

| 名前    |値   |説明   |                  
|------ |------- |--|
|MCDRemoteSystemAppRegistrationPublishStatusSuccess | 0 | 操作が正常に完了しました。|
|MCDRemoteSystemAppRegistrationPublishStatusErrorNoNetwork | 1 | ネットワークは使用できませんでした。 |
|MCDRemoteSystemAppRegistrationPublishStatusErrorWebFailure | 2 | Web サービスが失敗しました。|
|MCDRemoteSystemAppRegistrationPublishStatusErrorNoTokenRequestSubscriber | 3 | トークン要求のサブスクライバーが応答しません。|
|MCDRemoteSystemAppRegistrationPublishStatusErrorTokenRequestFailed | 4 | トークンの要求が失敗しました。|
|MCDRemoteSystemAppRegistrationPublishStatusErrorAccountNotFound | 5 | 情報を発行するアカウントが見つかりませんでした。|
|MCDRemoteSystemAppRegistrationPublishStatusErrorUnknown | 6 | 操作には、不明なエラーが発生しました。|