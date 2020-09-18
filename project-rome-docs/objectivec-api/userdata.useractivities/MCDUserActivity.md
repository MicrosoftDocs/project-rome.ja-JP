---
title: MCDUserActivity
description: MCDUserActivity クラスとそのプロパティについて説明します。 このクラスは、1つのユーザーアクティビティインスタンスを表します。
keywords: microsoft、windows、ユーザーアクティビティ、iOS、iPhone、、接続デバイス、プロジェクトローマ
ms.openlocfilehash: 8bdaf553611e868a5c37a9e033e2ba3126151967
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760146"
---
# <a name="class-mcduseractivity"></a>講義 `MCDUserActivity`

```
@interface MCDUserActivity : NSObject
```

このクラスは、1つのユーザーアクティビティインスタンスを表します。 ユーザーアクティビティは、実行中にアプリによって作成され、別のデバイスまたは同じデバイス上の別のデバイスで続行できるユーザー作業ストリームをシステムに通知します。 これは、ユーザーが関与しているタスクに関する情報を提供します。

>**注:** MCDUserActivity インスタンスには、100 KB のサイズ制限があります。この値を超えるとパブリッシュできません。

## <a name="properties"></a>Properties

### <a name="activityid"></a>activityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

このアクティビティの一意の ID。

### <a name="state"></a>状態
`@property(nonatomic, readonly) MCDUserActivityState state;`

このアクティビティの状態。

### <a name="activationuri"></a>activationUri
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

このユーザーアクティビティがアクティブになったときに従う URI。

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

プライマリ URI が失敗した場合に使用される、このアクティビティによって保持されている web フレンドリ URI。

### <a name="contenturi"></a>contentUri
`@property(nonatomic, copy, nullable) NSString* contentUri;`

このアクティビティのコンテンツ URI (別のデバイス上のアクティビティを表すために使用されるイメージの URI)。

### <a name="contenttype"></a>contentType
`@property(nonatomic, copy, nullable) NSString* contentType;`

**Contenturi**に格納されているコンテンツの MIME (Multipurpose Internet Mail Extensions) の種類。 たとえば、"text/plain" のようになります。

### <a name="contentinfojson"></a>contentInfoJson
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

このアクティビティの基本コンテンツ情報。 たとえば、アクティビティが RSS フィードを読み取っている場合、コンテンツ文字列には、アーティクルとその作成者の名前が含まれている可能性があります。

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

このアクティビティのアプリの表示名。

### <a name="visualelements"></a>visualElements
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

このアクティビティのビジュアル要素 (アクティビティの "詳細" タイルに使用できる情報)。

### <a name="roamable"></a>ローミング
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

このアクティビティが他のエンドポイントにローミングされているかどうかを取得または設定します。

## <a name="constructors"></a>コンストラクター

### <a name="activitywithactivityid"></a>activityWithActivityId
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

指定した ID を使用して、このクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `activityId` 

このアクティビティの識別子 (一意の文字列である必要があります)。

#### <a name="returns"></a>戻り値
このクラスのインスタンスを返します。

### <a name="initwithactivityid"></a>initWithActivityId
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

指定した ID を使用して、このクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `activityId`

このアクティビティの識別子 (一意の文字列である必要があります)。

#### <a name="returns"></a>戻り値
このクラスのインスタンスを返します。

## <a name="methods"></a>メソッド

### <a name="createsession"></a>createSession
`- (nonnull MCDUserActivitySession*)createSession;`

この MCDUserActivity が関連付けられるユーザーアクティビティセッションを作成します。 関連付けられた MCDUserActivitySession は、ユーザーが現在アクティビティに関与していることを示します。

#### <a name="returns"></a>戻り値
作成されたセッション。

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

ユーザーアクティビティを発行します。 このメソッドが呼び出される前に、MCDUserActivity には、アクティベーション URI と VisualElements メンバーが設定されている必要があります。 このメソッドは、アプリが MCDUserActivity のプロパティを変更するたびに呼び出される必要があります (更新プログラムを発行するため)。

#### <a name="parameters"></a>パラメーター
* `completionBlock` 完了時に実行するコードブロック。