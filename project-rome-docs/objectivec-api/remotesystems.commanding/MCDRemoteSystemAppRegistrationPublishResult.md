---
title: MCDRemoteSystemAppRegistrationPublishResult
description: クラスは、アカウントの発行のリモート システム アプリ情報の非同期結果を通信します。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 5e28e2533d14839384bcd2cfac2db3fc368a6207
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909924"
---
# <a name="class-mcdremotesystemappregistrationpublishresult"></a>クラス `MCDRemoteSystemAppRegistrationPublishResult` 

```
@interface MCDRemoteSystemAppRegistrationPublishResult : NSObject
```  

このクラスは、アカウントの発行のリモート システム アプリ情報の非同期結果を通信します。 利用できないネットワークなどの特定の一時的な問題が発生した場合の発行を再試行するアプリによってを通じて、この結果、エラー状態を使用する必要があります。

## <a name="properties"></a>プロパティ

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemAppRegistrationPublishStatus status;`

発行操作のステータスの列挙型。