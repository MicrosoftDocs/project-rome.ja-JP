---
title: MCDUserActivity
description: このクラスは、1 人のユーザー アクティビティのインスタンスを表します。
keywords: microsoft、windows、ユーザー アクティビティ、iOS、iPhone、objectiveC に接続されているデバイス、プロジェクトのローマ
ms.openlocfilehash: f01889f5e41c761fe359ed1fa90befee4a8aca46
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907424"
---
# <a name="class-mcduseractivity"></a>クラス `MCDUserActivity`

```
@interface MCDUserActivity : NSObject
```

このクラスは、1 人のユーザー アクティビティのインスタンスを表します。 ユーザーのアクティビティは、別のデバイスで、または同じデバイス上の別の時に再開できるユーザーのワーク ストリームのシステムに通知するには、その実行中に、アプリによって作成されます。 ユーザーが進行中のタスクに関する情報を提供します。

>**注:** MCDUserActivity インスタンスでは、100 KB を超えると、パブリッシュできませんのサイズ制限があります。

## <a name="properties"></a>プロパティ

### <a name="activityid"></a>ActivityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

このアクティビティの一意の ID。

### <a name="state"></a>state
`@property(nonatomic, readonly) MCDUserActivityState state;`

このアクティビティの状態。

### <a name="activationuri"></a>activationUri
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

このユーザーのアクティビティがアクティブ化されるときに実行する URI。

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

プライマリの URI が失敗した場合に使用される、このアクティビティによって保持されている web に適した URI。

### <a name="contenturi"></a>contentUri
`@property(nonatomic, copy, nullable) NSString* contentUri;`

このアクティビティ (別のデバイスでのアクティビティを表すために使用されるイメージの URI) のコンテンツの URI。

### <a name="contenttype"></a>contentType
`@property(nonatomic, copy, nullable) NSString* contentType;`

格納されているコンテンツの MIME (Multipurpose Internet Mail Extensions) 種類**contentUri**します。 たとえば、「テキスト/プレーン」。

### <a name="contentinfojson"></a>contentInfoJson
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

このアクティビティの基本的なコンテンツ情報。 たとえば、アクティビティが RSS フィードを読み取って、コンテンツの文字列は、情報の記事と、作成者の名前を含める可能性があります。

### <a name="appdisplayname"></a>AppDisplayName
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

このアクティビティのアプリの表示名。

### <a name="visualelements"></a>VisualElements
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

このアクティビティ (アクティビティの詳細」のタイルを使用できる情報) のビジュアル要素。

### <a name="roamable"></a>移動
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

取得またはこのアクティビティは他のエンドポイントにローミングするかどうかを設定します。

## <a name="constructors"></a>コンストラクター

### <a name="activitywithactivityid"></a>activityWithActivityId
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

指定した ID に置き換えます。 このクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `activityId` 

(一意の文字列にする必要があります)、このアクティビティの識別子。

#### <a name="returns"></a>戻り値
このクラスのインスタンスを返します。

### <a name="initwithactivityid"></a>initWithActivityId
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

指定した ID に置き換えます。 このクラスのインスタンスを作成します。

#### <a name="parameters"></a>パラメーター
* `activityId`

(一意の文字列にする必要があります)、このアクティビティの識別子。

#### <a name="returns"></a>戻り値
このクラスのインスタンスを返します。

## <a name="methods"></a>メソッド

### <a name="createsession"></a>CreateSession
`- (nonnull MCDUserActivitySession*)createSession;`

この MCDUserActivity の関連付けられているユーザー アクティビティのセッションを作成します。 関連付けられている MCDUserActivitySession では、ユーザーが現在、アクティビティに関与していることを示します。

#### <a name="returns"></a>戻り値
作成されたセッションです。

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

ユーザー アクティビティを発行します。 MCDUserActivity は、このメソッドが呼び出される前に、アクティブ化 URI と設定の表示テキストを持つ VisualElements メンバーが必要です。 アプリは、(更新プログラムの発行) するために、MCDUserActivity のプロパティを変更するたびに、このメソッドを呼び出す必要があります。

#### <a name="parameters"></a>パラメーター
* `completionBlock` 完了時に実行するコード ブロックです。