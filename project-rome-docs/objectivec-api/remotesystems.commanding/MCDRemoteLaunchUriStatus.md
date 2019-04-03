---
title: MCDRemoteLaunchUriStatus
description: URI を使用して、リモート アプリの起動の状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 1a0302cd570b8cb25476a8188e3bcb1667707461
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907144"
---
# <a name="enum-mcdremotelaunchuristatus"></a>列挙型 `MCDRemoteLaunchUriStatus`

`typedef NS_ENUM(NSInteger, MCDRemoteLaunchUriStatus)`

URI を使用して、リモート アプリの起動の状態を記述する値が含まれています。


| 名前    |値   |説明   |                  
|------ |------- |--|
|MCDRemoteLaunchUriStatusUnknown | 0| 状態が不明です。|
|MCDRemoteLaunchUriStatusSuccess | 1| リモートからの起動に成功しました。|
|MCDRemoteLaunchUriStatusAppUnavailable | 2 | 対象となるアプリでは使用できません。|
|MCDRemoteLaunchUriStatusProtocolUnavailable | 3 | 対象となるアプリでは、この URI はサポートされません。|
|MCDRemoteLaunchUriStatusRemoteSystemUnavailable | 4 | メッセージの送信、デバイスは、ご利用いただけません。|
|MCDRemoteLaunchUriStatusValueSetTooLarge | 5 | 対象となるアプリに送信される、データ バンドルが大きすぎます。|
|MCDRemoteLaunchUriStatusDeniedByLocalSystem | 6 | クライアント システムがリモート システム プラットフォームを使用できないように設定します。|
|MCDRemoteLaunchUriStatusDeniedByRemoteSystem | 7 | ターゲット デバイスがリモート システム プラットフォームを使用できないように設定します。|