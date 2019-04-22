---
title: MCDStatelessAppServiceResponseStatus
description: (メッセージ データが正常に配信された) かどうか、別に 1 つの app service から送信されたメッセージの状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 9d01e892861c8551b7b3e41d1b227f65f07d752a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801714"
---
# <a name="enum-mcdstatelessappserviceresponsestatus"></a>列挙型 `MCDStatelessAppServiceResponseStatus`

`typedef NS_ENUM(NSInteger, MCDStatelessAppServiceResponseStatus)`

 (メッセージ データが正常に配信された) かどうか、別に 1 つの app service から送信されたメッセージの状態を記述する値が含まれています。


| 名前    |値   |説明   |                  
|------ |------- |--|
|MCDStatelessAppServiceResponseStatusSuccess | 0| メッセージが正常に配信されました。 |
|MCDStatelessAppServiceResponseStatusAppNotInstalled | 1| デバイスでは、接続の試みを app service のパッケージがインストールされていません。 Theap p サービスへの接続を開く前に、パッケージがインストールされていることを確認します。 |
|MCDStatelessAppServiceResponseStatusAppUnavailable | 2 | 接続の試みを app service のパッケージは一時的にご利用いただけません。 後でもう一度接続しようとしてください。 |
|MCDStatelessAppServiceResponseStatusAppServiceUnavailable | 3 | 指定したパッケージ ID を持つアプリがインストールされ、使用できるが、アプリは、指定した app service のサポートを宣言しません。 App service の名前と、アプリのバージョンが正しいことを確認します。 |
|MCDStatelessAppServiceResponseStatusRemoteSystemUnavailable | 4 | リモート デバイスへの接続を確立できないために、メッセージは配信されませんでした。|
|MCDStatelessAppServiceResponseStatusRemoteSystemNotSupportedByApp | 5 | リモート接続をサポートするためには、リモート アプリが構成されていません。 |
|MCDStatelessAppServiceResponseStatusNotAuthorized | 6 | App service は、リモート デバイスと通信する権限がありません。 |
|MCDStatelessAppServiceResponseStatusResourceLimitsExceeded | 7 | リモートの app service のプログラムのメモリ制限を超えているために、メッセージは配信されませんでした。|
|MCDStatelessAppServiceResponseStatusMessageSizeTooLarge | 8 | 許可されているサイズを超えているために、メッセージは配信されませんでした。 |
|MCDStatelessAppServiceResponseStatusFailure | 9 | ネットワーク エラーのため、メッセージは配信されませんでした。 |
|MCDStatelessAppServiceResponseStatusUnknown | 10 |メッセージが不明な理由では配信されません。 |