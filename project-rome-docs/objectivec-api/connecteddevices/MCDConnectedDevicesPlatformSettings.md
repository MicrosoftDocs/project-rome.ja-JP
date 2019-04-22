---
title: MCDConnectedDevicesPlatformSettings
description: 特定の場所に格納されるデバイス プラットフォームの接続の設定を許可するインターフェイスです。
keywords: microsoft、windows、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: 9753553cefbbeaff598550687b8dfa5100d2006e
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801754"
---
# <a name="class-mcdconnecteddevicesplatformsettings"></a><span data-ttu-id="51284-104">クラス `MCDConnectedDevicesPlatformSettings`</span><span class="sxs-lookup"><span data-stu-id="51284-104">class `MCDConnectedDevicesPlatformSettings`</span></span> 

```
@interface MCDConnectedDevicesPlatformSettings : NSObject
```  
<span data-ttu-id="51284-105">特定の場所に格納されるデバイス プラットフォームの接続の設定を許可するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="51284-105">An interface to allow Connected Devices Platform settings to be stored in a particular location.</span></span>  

## <a name="properties"></a><span data-ttu-id="51284-106">プロパティ</span><span class="sxs-lookup"><span data-stu-id="51284-106">Properties</span></span>

### <a name="storagepath"></a><span data-ttu-id="51284-107">StoragePath</span><span class="sxs-lookup"><span data-stu-id="51284-107">storagePath</span></span>
`@property (nonatomic, readwrite, nonnull) NSString* storagePath;`

<span data-ttu-id="51284-108">接続されているデバイス プラットフォームの設定の格納場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="51284-108">The path to the storage location of the Connected Devices Platform settings.</span></span>