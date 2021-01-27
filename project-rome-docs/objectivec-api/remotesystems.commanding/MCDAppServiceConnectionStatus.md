---
title: MCDAppServiceConnectionStatus
description: リモートの app service への接続の状態を示す値を格納します。
keywords: microsoft、windows、iOS、iPhone、、、、および接続されているデバイス、プロジェクトローマ
ms.openlocfilehash: cf272326ce5c88f7c847a2a03eafe5b8bbbaa56e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901640"
---
# <a name="enum-mcdappserviceconnectionstatus"></a>enum `MCDAppServiceConnectionStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceConnectionStatus)
```

リモートの app service への接続の状態を示す値を格納します。 Windows デバイス上の app services の詳細については、「 [app service の作成と使用](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) 」を参照してください。

|名前   |値   |説明   |
|--------|-------|-------------|
|MCDAppServiceConnectionStatusSuccess | 0| App service への接続が正常に開かれました。|
|MCDAppServiceConnectionStatusAppNotInstalled | 1| 接続を試行した app service のパッケージがデバイスにインストールされていません。 App service への接続を開こうとする前に、パッケージがインストールされていることを確認してください。|
|MCDAppServiceConnectionStatusAppUnavailable | 2| 接続を試行した app service のパッケージが一時的に使用できなくなっています。 後でもう一度接続してください。|
|MCDAppServiceConnectionStatusAppServiceUnavailable | 3| 指定されたパッケージ ID を持つアプリがインストールされ、使用できますが、指定された app service のサポートはアプリによって宣言されていません。 App service の名前とアプリのバージョンが正しいことを確認します。|
|MCDAppServiceConnectionStatusUnknown | 4| 不明な理由により、接続を確立できませんでした。|
|MCDAppServiceConnectionStatusRemoteSystemUnavailable | 5| ターゲットのリモートデバイスまたはアプリケーションが接続に使用できなくなりました。|
|MCDAppServiceConnectionStatusRemoteSystemNotSupportedByApp | 6|クライアントアプリがリモート接続をサポートするように構成されていません。|
|MCDAppServiceConnectionStatusNotAuthorized | 7| クライアントデバイスは、リモート接続をサポートすることが許可されていません。 これは、MCDAppServiceConnection に無効なトークンが渡されたことが原因で発生する可能性があります。|