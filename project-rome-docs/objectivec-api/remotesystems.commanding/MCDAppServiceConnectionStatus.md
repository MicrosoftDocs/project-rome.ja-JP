---
title: MCDAppServiceConnectionStatus
description: リモート アプリ サービスへの接続の状態を記述する値が含まれています。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5beba7ae30d8ffd9149c5e8a599eacc38213b6d2
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801454"
---
# <a name="enum-mcdappserviceconnectionstatus"></a>列挙型 `MCDAppServiceConnectionStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceConnectionStatus)
```

リモート アプリ サービスへの接続の状態を記述する値が含まれています。 参照してください[作成し、app service を使用](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service)Windows デバイス上の app services についてはします。

|名前   |値   |説明   |
|--------|-------|-------------|
|MCDAppServiceConnectionStatusSuccess | 0| App service への接続を正常に開きました。|
|MCDAppServiceConnectionStatusAppNotInstalled | 1| デバイスでは、接続の試みを app service のパッケージがインストールされていません。 App service への接続を開こうとする前に、パッケージがインストールされていることを確認します。|
|MCDAppServiceConnectionStatusAppUnavailable | 2| 接続の試みを app service のパッケージは一時的にご利用いただけません。 後でもう一度接続しようとしてください。|
|MCDAppServiceConnectionStatusAppServiceUnavailable | 3| 指定したパッケージ ID を持つアプリがインストールされ、使用できるが、アプリは、指定した app service のサポートを宣言しません。 App service の名前と、アプリのバージョンが正しいことを確認します。|
|MCDAppServiceConnectionStatusUnknown | 4| 不明な理由で、接続を確立できませんでした。|
|MCDAppServiceConnectionStatusRemoteSystemUnavailable | 5| 対象のリモート デバイスまたはアプリケーションでは、接続の使用できなくします。|
|MCDAppServiceConnectionStatusRemoteSystemNotSupportedByApp | 6|リモート接続をサポートするためには、クライアント アプリが構成されていません。|
|MCDAppServiceConnectionStatusNotAuthorized | 7| クライアント デバイスは、リモート接続をサポートする権限がありません。 これは、MCDAppServiceConnection に無効なトークンが渡されるために発生する可能性があります。|