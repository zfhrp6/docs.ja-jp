---
title: F# でコンポーネントのデザイン ガイドライン
description: F# で他の呼び出し元で消費するためのコンポーネントを記述するためのガイドラインを説明します。
ms.date: 05/14/2018
ms.openlocfilehash: 7e71710b1bc2fe3e8d7a5a091513a1432650dc04
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
---
# <a name="f-component-design-guidelines"></a>F# でコンポーネントのデザイン ガイドライン

このドキュメントは、一連の f# プログラミング、f# コンポーネントのデザインのガイドラインに基づいて、v14、Microsoft Research のコンポーネントのデザイン ガイドラインおよび[別のバージョン](https://fsharp.org/specs/component-design-guidelines/)最初 curated および f# Software Foundation によって維持されます。

このドキュメントでは、f# プログラミングに慣れていると仮定します。 多く f# コミュニティ投稿と、このガイドのさまざまなバージョンに役立つフィードバックのご協力に感謝します。

## <a name="overview"></a>概要

このドキュメントは、f# コンポーネントの設計とコーディングに関連する問題の一部を検索します。 コンポーネントは、次のいずれかで意味があります。

* プロジェクト内の外部のコンシューマーのある f# プロジェクト内のレイヤー。
* アセンブリ境界を越えて、f# コードによる消費を意図してライブラリです。
* アセンブリ境界を越えて、任意の .NET 言語による消費を意図してライブラリです。
* ライブラリのパッケージ リポジトリを使用して配布など[NuGet](https://nuget.org)です。

この記事で説明した方法に従って、[優れた f# コードの 5 つの原則](index.md#five-principles-of-good-f-code)とため両方の機能を利用し、適切なプログラミング オブジェクトします。

方法には、タイミングに関係なくコンポーネントおよびライブラリのデザイナー接している実用的で prosaic の問題の数、開発者が最も簡単に使用できる API を作成しようとしています。 Conscientious アプリケーション、 [.NET ライブラリ デザイン ガイドライン](../../standard/design-guidelines/index.md)一貫性のある一連の消費を快適になり、Api の作成における導いたりするされます。

## <a name="general-guidelines"></a>一般的なガイドライン

F# ライブラリ、ライブラリの対象読者に関係なく適用されるいくつかのユニバーサル ガイドラインがあります。

### <a name="learn-the-net-library-design-guidelines"></a>.NET ライブラリのデザイン ガイドラインを説明します。

F# でコーディングを行うように関係なくすることが重要知識のある、 [.NET ライブラリ デザイン ガイドライン](../../standard/design-guidelines/index.md)です。 ほとんどの他の f# および .NET プログラマはや理解しており次のガイドラインに準拠するように .NET コードを期待します。

.NET ライブラリのデザイン ガイドラインでは、名前付け、クラス、インターフェイス、メンバーのデザイン (プロパティ、メソッド、イベントなど) およびの詳細は、設計に関する一般的なガイダンスを提供し、さまざまなデザイン ガイドの参照の最初のポイントを便利が。

### <a name="add-xml-documentation-comments-to-your-code"></a>XML ドキュメント コメントをコードに追加します。

パブリック Api の XML ドキュメントでは、ライブラリのファイルをこれらの型とメンバー、および有効にする構成ドキュメントを使用するときに、優れたの Intellisense とクイック ヒントを取得できることを確認します。 参照してください、 [XML ドキュメント](../language-reference/xml-documentation.md)に関するその他のマークアップ内で、xmldoc コメントの使用できるさまざまな xml タグ。

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

短い形式として XML のコメントを使用することができます (`/// comment`)、または標準の XML コメント (`///<summary>comment</summary>`)。

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>安定したライブラリとコンポーネントの Api の明示的なシグネチャ ファイル (.fsi) を使用してください。

パブリック API を両方こと、ライブラリの完全パブリック サーフェスを把握できるだけでなくする内部し、パブリックのドキュメント間を明確に分離を提供することができますの簡潔な概要を説明する f# ライブラリで明示的なシグネチャ ファイルの使用実装の詳細。 シグネチャ ファイルが実装と署名の両方のファイルに対する変更を要求することによって、パブリック API の変化に摩擦を追加することに注意してください。 その結果、署名ファイルは通常のみ際に挿入される API 確立しましたになるし、大幅に変更が不要になった想定します。

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>常に文字列を .NET で使用するためのベスト プラクティスに従う

次の[.NET での文字列を使用するためのベスト プラクティス](../../standard/base-types/best-practices-strings.md)ガイダンス。 具体的には、常に明示的に記述*カルチャ インテント*変換と文字列の比較で (該当する場合)。

## <a name="guidelines-for-f-facing-libraries"></a>F# に関するガイドラインのライブラリが直面しています。

ここでは、パブリック f# の開発に関する推奨事項のライブラリが直面しています。f# の開発者によって使用するためのパブリック Api を公開するライブラリは、します。 F# を具体的には適用可能なライブラリ デザインの推奨事項のさまざまな。 具体的な推奨事項に従うがない場合は、.NET ライブラリ デザイン ガイドラインは、フォールバックのガイダンスです。

### <a name="naming-conventions"></a>名前付け規則

#### <a name="use-net-naming-and-capitalization-conventions"></a>.NET の名前付けおよび大文字と小文字の規則を使用します

次の表では、.NET の名前付けおよび大文字と小文字の規則に従います。 F# の構成要素を含める小さな追加があります。

| 構成体 | Case | パーツ | 使用例 | メモ |
|-----------|------|------|----------|-------|
| 具象型 | PascalCase | 名詞または形容詞 | 一覧で、Double、複雑な | 具象型は、構造体、クラス、列挙体、デリゲート、レコード、および共用体です。 OCaml で小文字従来型の名前ですが、F# で採用しています型の .NET 名前付けスキーム。
| DLL           | PascalCase |                 | Fabrikam.Core.dll |  |
| 共用体タグ     | PascalCase | 名詞 | いくつかの追加、成功 | パブリック Api では、プレフィックスを使わないでください。 必要に応じてなどの内部プレフィックスを使用して '' 入力チーム TAlpha を = | TBeta | TDelta '' '。 |
| event          | PascalCase | 動詞 | ValueChanged/ValueChanging |  |
| 例外     | PascalCase |      | WebException | 名前は、"Exception"で終わる必要があります。 |
| フィールド          | PascalCase | 名詞 | CurrentName  | |
| インターフェイス型 |  PascalCase | 名詞または形容詞 | IDisposable | 名前は、"I"で始まる必要があります。 |
| メソッド |  PascalCase |  動詞 | ToString | |
| 名前空間 | PascalCase | | Microsoft.FSharp.Core | 一般に使用`<Organization>.<Technology>[.<Subnamespace>]`、ただしテクノロジが組織に依存しない場合は、組織をドロップします。 |
| パラメーター | キャメル ケース | 名詞 |  typeName、変換、範囲 | |
| (内部) の値を使用できます。 | キャメル ケースまたは PascalCase | 名詞と動詞 |  getValue、myTable |
| 値 (外部) を使用できます。 | キャメル ケースまたは PascalCase | 名詞と動詞  | List.map、Dates.Today | let バインドされた値は、従来の機能のデザイン パターンに従うときに多くの場合、パブリック。 ただし、通常使用 PascalCase 識別子を他の .NET 言語から使用するとき。 |
| プロパティ  | PascalCase  | 名詞または形容詞  | IsEndOfFile、背景色  | ブール型プロパティ、通常は使用して、ことができ、IsEndOfFile、いない IsNotEndOfFile と同様に、肯定的である必要があります。

#### <a name="avoid-abbreviations"></a>省略形を回避します。

.NET ガイドラインの省略形の使用を防ぐため (たとえば、"使用`OnButtonClick`なく`OnBtnClick`") です。 一般的な省略形など`Async`「非同期」の場合は、許容されます。 、関数型プログラミングでは、このガイドラインは無視される場合がありますたとえば、 `List.iter` 「反復処理する」の省略形を使用します。 このため、略語を使用して f# ではある程度の大きい値を許容する傾向があります-を-f# プログラミングでは、引き続き通常パブリック コンポーネントのデザインに避ける必要がありますが、します。

#### <a name="avoid-casing-name-collisions"></a>大文字小文字の区別の名前の衝突を避ける

.NET のガイドラインでは、一部のクライアント言語 (たとえば、Visual Basic) 小文字は区別されませんので、名の競合を区別するために単独で大文字と小文字を使用できないことを言います。

#### <a name="use-acronyms-where-appropriate"></a>頭字語を使用して適切な場所

XML などの頭字語は、省略形ではないや、uncapitalized 形式 (Xml) での .NET ライブラリで広く使用されます。 のみよく知られている、広く認識されているの頭字語を使用する必要があります。

#### <a name="use-pascalcase-for-generic-parameter-names"></a>PascalCase 名を使用するジェネリック パラメーター

PascalCase 名を使用するジェネリック パラメーターの f# などのパブリック Api でのライブラリが直面しています。 具体的には、ような名前を使用して`T`、 `U`、 `T1`、`T2`の任意のジェネリック パラメーターを使用して特定の名前をなしませんし、f# に直接つながっているライブラリのような名前を使用して`Key`、 `Value`、 `Arg`(がないなど、 `TKey`)。

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>パブリックの関数と f# モジュール内の値に PascalCase またはキャメル ケースのいずれかを使用します。

キャメル ケースが使用するよう設計されているパブリック関数の使用修飾されていない (たとえば、 `invalidArg`)、(たとえば、List.map)「標準的なコレクション関数」にします。 どちらの場合も、関数名機能は言語のキーワードと同様にします。

### <a name="object-type-and-module-design"></a>オブジェクト、型、およびモジュールのデザイン

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>名前空間またはモジュールを使用してタイプやモジュールを含める

コンポーネントのそれぞれの f# ファイルは、名前空間の宣言またはモジュールの宣言で始まる必要があります。

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

または

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

モジュールと名前空間を使用して、最上位レベルのコードを整理する間の相違点は次のとおりです。

* 名前空間が複数のファイルにまたがることができます。
* 名前空間は内部のモジュール内にある場合を除き、f# の関数を含めることはできません。
* 指定されたモジュールのコードは、1 つのファイル内に含まれる必要があります。
* 最上位レベルのモジュールは、内部のモジュールのなしの f# 関数を含めることができます。

最上位レベルの名前空間またはモジュール間の選択は、コードのコンパイルした形式に影響し、したがってが影響他の .NET 言語から、ビューは、API 最終的に利用できる f# コードの外部で。

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>オブジェクトの種類に固有の操作のためのメソッドとプロパティを使用します。

オブジェクトを使用する場合は、メソッドおよびその型のプロパティとして利用できる機能が実装されていることを確認することをお勧めします。

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

そのメンバーに特定のメンバーが持つ機能の一括必要があるとは限りません実装はありませんが、その機能の利用できる部分の有効期限があります。

#### <a name="use-classes-to-encapsulate-mutable-state"></a>クラスを使用して、変更可能な状態をカプセル化

F# でこれのみ行う必要があります、いる状態は既にカプセル化されていないクロージャ、シーケンス式、または非同期計算などの別の言語コンストラクトでします。

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>インターフェイスを使用してグループ化に関連する操作

インターフェイス型を使用して、一連の操作を表します。 これは、関数の組または関数のレコードなど、その他のオプションをお勧めします。

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

優先します。

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

インターフェイスは、.NET では、どのようなファンクター通常できるようになりますを実現するために使用できるファースト クラスの概念です。 さらに、関数のレコードのことはできませんが、プログラムに存在: 型のエンコードに使用できます。

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>操作を実行するグループの機能をモジュールのコレクションを使用します

コレクション型を定義するときなどの操作の標準セットを提供することを検討してください`CollectionType.map`と`CollectionType.iter`) の新しいコレクション型。

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

このようなモジュールを含める場合は FSharp.Core で見つかった関数の名前付け規則に従います。

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>数学関数や DSL ライブラリで特にの一般的な正規の関数グループ関数をモジュールを使用します。

たとえば、`Microsoft.FSharp.Core.Operators`されて自動的に開かれている最上位の関数のコレクション (と同様に`abs`と`sin`) FSharp.Core.dll によって提供されます。

同様に、統計のライブラリは関数を持つモジュールを含めることが`erf`と`erfc`に明示的にまたは自動的に開かれるこのモジュールは設計されています。

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>RequireQualifiedAccess の使用を検討し、慎重に AutoOpen 属性を適用

追加する、`[<RequireQualifiedAccess>]`属性をモジュールにことを示し、モジュールが開かれていませんアクセスを修飾するモジュールの要素への参照が明示的に必要なことです。 たとえば、`Microsoft.FSharp.Collections.List`モジュールは、この属性を持ちます。

これは、機能は、関数と、モジュール内の値は、他のモジュールの名前と競合する可能性のある名前を持つ場合に便利です。 修飾のアクセスを必要とすると、長期的な保守容易性とライブラリの発展性が大幅に増やすできます。

追加する、`[<AutoOpen>]`をモジュールに属性を含む名前空間が開かれたときに、モジュールが開かれることを意味します。 `[<AutoOpen>]`属性は、アセンブリが参照されている場合に自動的に開かれているモジュールを示すためにアセンブリにも適用できます。

統計ライブラリなど、 **MathsHeaven.Statistics**場合があります、`module MathsHeaven.Statistics.Operators`関数を含む`erf`と`erfc`です。 このモジュールとして指定することは正当`[<AutoOpen>]`です。 つまり、`open MathsHeaven.Statistics`もこのモジュールを開き、名前を`erf`と`erfc`スコープにします。 別なを使用して`[<AutoOpen>]`拡張メソッドが含まれるモジュールです。

使いすぎ`[<AutoOpen>]`汚染名前空間と属性に潜在顧客は、注意を払って使用する必要があります。 特定のドメインを賢く利用で特定のライブラリの`[<AutoOpen>]`使いやすさにつながることができます。

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>ここで、よく知られている演算子の使用は適切なクラスで演算子メンバーの定義を検討してください。

場合によってベクトルなどの数学的な構造をモデル化するクラスが使用されます。 モデル化されているドメインがよく知られている演算子を持つクラスに固有のメンバーとして定義することをお勧めします。

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

このガイドは、これらの型の .NET の一般的なガイダンスに対応します。 ただし、f# コーディングこれにより、これらの型の f# 関数と組み合わせておよび List.sumBy など、メンバーの制約のメソッドで使用するようにさらに重要なことができます。

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>提供する CompiledName の使用を検討します。他の .NET 言語コンシューマー NET のフレンドリ名

F# のコンシューマーの名前を 1 つのスタイルで何かにすることも (小文字のみに表示されるように静的メンバーなどモジュール バインド関数の場合と同様) がアセンブリにコンパイルすると、名前の別のスタイルがします。 使用することができます、`[<CompiledName>]`属性とは異なるスタイル コードを提供する非 f# アセンブリを使用します。

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

使用して`[<CompiledName>]`、非 f# アセンブリのコンシューマーの .NET 名前付け規則を使用することができます。

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>メンバー関数の場合は、メソッドのオーバー ロードを使用するため、これにより、シンプルな API 場合

メソッドのオーバー ロードは、さまざまなオプションと引数が、同様の機能を実行する必要がある API を簡略化するための強力なツールです。

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

F# では、引数の型ではなく引数の数のオーバー ロードする方が一般的です。

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>これらの型のデザインが発展する可能性がある場合、レコード、共用体の型の表現を非表示にします。

オブジェクトの具体的な表現を公開することを回避します。 たとえば、具象の形式を<xref:System.DateTime>値が .NET ライブラリ デザインの外部のパブリック API によって公開されていません。 実行時に、共通言語ランタイムは、実行全体で使用されるコミットの実装を認識します。 ただし、コンパイルされたコードはしない自体、具体的な表現への依存関係を取得します。

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>機能拡張の実装の継承は使用しないでください。

F# では、実装の継承がほとんど使用されません。 さらに、継承階層は多くの場合、複雑で、新しい必要条件は到着したときに変更するが困難にします。 継承の実装は、互換性とは、問題に最適なソリューションは、インターフェイスの実装など、ポリモーフィズムの設計時に、f# プログラム内で代替手法を取得する必要がありますが、まれなケースの f# では引き続き存在します。

### <a name="function-and-member-signatures"></a>関数とメンバーのシグネチャ

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>少数の関連のない複数の値を返すときに、戻り値の組を使用します。

戻り値の型、タプルを使用しての良い例を次に示します。

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

多くのコンポーネントを含む型を返すか、コンポーネントは、特定の単一のエンティティに関連する、場所は、組ではなく名前付きの型を使用することを検討してください。

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>使用して`Async<T>`f# API の境界での非同期プログラミング

という名前の対応する同期操作があるかどうかは`Operation`を返す、 `T`、このという名前を付けると、非同期処理する必要があります`AsyncOperation`を返す場合`Async<T>`または`OperationAsync`を返す場合`Task<T>`です。 Begin/end メソッドを公開する、よく使用される .NET 型の使用を検討の`Async.FromBeginEnd`拡張メソッドを特定の .NET Api を F# で非同期プログラミング モデルを提供するファサードとして書き込みます。

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>例外

例外は、.NET の例外つまり、する必要がありますいない頻繁に発生実行時にします。 場合に、含まれている情報は重要です。 例外は、コア .NET; のファースト クラスの概念次のように、例外のアプリケーションを適切なコンポーネントのインターフェイスの設計の一部として使用するため it です。

#### <a name="follow-the-net-guidelines-for-exceptions"></a>例外、.NET のガイドラインに従う

[.NET ライブラリ デザイン ガイドライン](../../standard/design-guidelines/exceptions.md)のすべての .NET プログラミングのコンテキストでの例外の使用上のすばらしいアドバイスを提供します。 これらのガイドラインの一部としては。

* 通常の制御フローの例外を使用しないでください。 この手法は OCaml などの言語で使用される多くの場合、これはバグが発生しやすくし、.NET で効率的なことができます。 代わりに、検討を返す、`None`オプションの失敗の原因、一般的なまたは予期される出現する位置を示す値。

* 関数が正しく使用されていないときに、コンポーネントによってスローされる例外を文書化します。

* 可能であれば、システムの名前空間から既存の例外を使用します。 回避<xref:System.ApplicationException>ことができます。

* スローしないで<xref:System.Exception>ことをユーザー コードにはエスケープするときにします。 これは、使用しないが含まれています。 `failwith`、 `failwithf`、スクリプトで使用すると、開発中コード用の便利な関数は、より具体的な種類の例外がスローされることを優先するための f# ライブラリ コードから削除するかがいます。

* 使用して`nullArg`、 `invalidArg`、および`invalidOp`をスローするためのメカニズムとして<xref:System.ArgumentNullException>、 <xref:System.ArgumentException>、および<xref:System.InvalidOperationException>適切な場合です。

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a>エラーが例外的なシナリオではない場合に戻り値の型のオプションの値を使用してください。

例外に .NET アプローチはことがあります「例外的な」です。つまり、それらを実行する頻度が比較的低い。 ただし、一部の操作 (たとえば、テーブルを検索) が頻繁に失敗する可能性があります。 F# のオプションの値は、これらの操作の戻り値の型を表すための優れた方法です。 これらの操作は、通常、名のプレフィックス"try"で開始します。

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a>拡張メンバー

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>F# で f# 拡張メンバーを慎重に適用にする-f# コンポーネント

F# の拡張メンバー一般にのみ使用してくださいのほとんどでは、そのモードの使用の種類に関連付けられた組み込みの操作のクロージャに含まれる操作。 1 つの一般的な用途は、さまざまな .NET 型の f# 慣用は Api を提供します。

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>共用体の型

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>クラスの階層構造ではなくツリー構造のデータの判別共用体を使用します。

ツリーのような構造体は、再帰的に定義されています。 これは、継承を使用して不適切な判別共用体で洗練されたです。

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

判別共用体のツリーのようなデータを表すも使用するパターン マッチで exhaustiveness メリットを享受できます。

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>使用して`[<RequireQualifiedAccess>]`に名前を持つケースが十分に一意ではない共用体の型

判別共用体ケースなどの別の意味のわかりやすい名前を同じ名前がここでは、ドメインで気づいたら可能性があります。 使用することができます`[<RequireQualifiedAccess>]`トリガーの順序に依存してにシャドウによる混乱を招くエラーを回避するために、ケースの名前を区別するために`open`ステートメント

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>これらの型のデザインが発展する可能性がある場合、バイナリの互換性のある Api の判別共用体の表現を非表示にします。

共用体の型は、f# パターン マッチ フォームの簡潔なプログラミング モデルに依存します。 前述のように、これらの型のデザインが発展する可能性がある場合は、具体的なデータ表現を漏洩を避ける必要があります。

たとえば、判別共用体の形式を非表示にできるプライベートまたは内部の宣言を使用してまたは署名ファイルを使用します。

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

無秩序判別共用体を表示する場合があります、バージョンにハード ライブラリ ユーザー コードを分断することがなく。 代わりに、型の値に一致するパターンを許可するように 1 つまたは複数のアクティブなパターンを公開することを検討してください。

アクティブ パターンでは、f# 共用体の型を直接公開することを回避しながらに一致するパターンを F# でコンシューマーに提供する別の方法を提供します。

### <a name="inline-functions-and-member-constraints"></a>インライン関数とメンバーの制約

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>暗黙的なメンバー制約と静的に解決されたジェネリック型とインライン関数を使用して、ジェネリックな数値アルゴリズムを定義します。

算術メンバー制約と f# 比較制約は、f# のプログラミング用の標準はします。 次に例を示します。

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

この関数の型は次のとおりです。

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

これは、数値演算ライブラリ内のパブリック API の適切な関数です。

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>型のクラスとダック」と入力をシミュレートするためにメンバー制約は使用しないでください。

「入力ダック」をシミュレートすることは f# メンバー制約を使用します。 ただし、構成するメンバーを使用してこのではなく一般的なを f# で使用する必要があります-に、f# ライブラリ デザインします。 これは、未知または標準の暗黙的な制約に基づいてライブラリ デザインになり強い特定のフレームワークを 1 つのパターンに関連付けられたユーザー コードが発生する傾向があるためです。

さらに、この方法でメンバー制約が多用は非常に長いコンパイル時間につながる可能性があります。

### <a name="operator-definitions"></a>演算子の定義

#### <a name="avoid-defining-custom-symbolic-operators"></a>シンボリック カスタムの演算子を定義しないように

カスタム演算子は、一部の状況で不可欠な機能および実装コードの本文内で表記デバイスが非常に有用です。 ライブラリの新規ユーザーの名前付き関数でを使いやすくする多くの場合です。 さらに、カスタム シンボリック演算子は、ドキュメント、しにくいことができ、ユーザーでは検索され、検索エンジンの既存の制限のための演算子に関するヘルプを検索することが難しくします。

その結果、という名前の関数、およびメンバーとして、機能を公開し、さらに、ドキュメントとすることのコストの認知表記の利点を上回る場合する場合にのみにこの機能のための演算子を公開することをお勧めします。

### <a name="units-of-measure"></a>測定単位

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>F# コードで追加した型の安全性の単位を慎重に使用します。

他の .NET 言語で表示したときに、メジャーの単位の追加入力情報が消去されます。 .NET コンポーネント、ツール、およびリフレクションが単位数 san の種類が表示される注意してください。 たとえば、c# コンシューマーは参照`float`なく`float<kg>`です。

### <a name="type-abbreviations"></a>型略称

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>型の省略形を使用して慎重に f# コードを簡略化

.NET コンポーネント、ツール、およびリフレクション型の省略名は表示されません。 型の省略形の重要な使用法には、ドメインが表示されるより複雑実際にが、コンシューマーが混乱することもできます。

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>メンバーとプロパティが省略されている型で使用するものは本質的に異なる必要がありますのパブリック型の型の省略形を回避します。

この場合、省略されている型は、定義されている実際の型の表現についてあまりが表示されます。 代わりに、クラス型または単一ケースの判別共用体での省略形の折り返しを検討してください (または、パフォーマンスが重要な場合は、構造体の型を使用して、省略形をラップすることを検討してください)。

たとえば、することは避けてなど、F# でマップの特殊なケースとして、複数のマップを定義します。

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

ただし、この型でドット付き表記の論理操作は、マップでは、操作と同じではありません: などが妥当 lookup 操作にマップします。[キー] 例外が発生するのではなく、辞書にキーがない場合は、空のリストを返します。

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>他の .NET 言語から使用するためのライブラリに関するガイドライン

他の .NET 言語から使用するためのライブラリをデザインする場合に従う必要が、 [.NET ライブラリ デザイン ガイドライン](../../standard/design-guidelines/index.md)です。 このドキュメントでこれらのライブラリは f# ではなく、標準の .NET ライブラリとしてというラベルが付いた-制限なし構築 f# を使用するライブラリが直面しています。 標準の .NET ライブラリのデザインには、f# の使用を最小限に抑えることによって、.NET Framework の残りの部分と一貫性のある使い慣れたと慣用 Api を提供することを意味のパブリック API で特定のコンス トラクターです。 ルールは、次のセクションで説明します。

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Namespace と型のデザイン (の他の .NET 言語から使用するライブラリ)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>コンポーネントのパブリック API への .NET の名前付け規則を適用します。

省略名および .NET の大文字と小文字のガイドラインを使用する特別な注意してください。

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>名前空間、型、およびメンバーをコンポーネントの主要な組織構造として使用します。

パブリックな機能を含むすべてのファイルの先頭でなければなりません、`namespace`宣言、および名前空間で公開されたエンティティだけに、型を指定する必要があります。 F# モジュールを使用しないでください。

実装コードは、ユーティリティ型、およびユーティリティ関数を保持するためにパブリックでないモジュールを使用します。

静的な型必要がありますよりも優先される、モジュール API の将来の展開のオーバー ロードおよびその他の .NET API の設計概念 f# モジュール内では使用できませんの使用を許可するようにします。

たとえば、次のパブリック API: の代わりに

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

代わりに検討してください。

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>型のデザインが変化しない場合は、バニラ .NET Api で f# レコード型を使用します。

F# のレコードの種類は、単純な .NET クラスにコンパイルされます。 これらは、一部の単純で安定した種類の Api に適しています。 使用を検討する必要があります、`[<NoEquality>]`と`[<NoComparison>]`属性のインターフェイスの自動生成を抑制します。 また、パブリック フィールドとしてこれらの公開バニラ .NET Api で変更可能なレコードのフィールドは使用しないでください。 常にクラスが、API の将来の進化をより柔軟なオプションを提供するかどうかを検討してください。

たとえば、次の f# コードは、c# コンシューマーにパブリック API を公開します。

F# の場合:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

C#: 

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>F# の共用体型バニラ .NET Api の形式を非表示にします。

F# 共用体型一般的に使用されないコンポーネントの境界を越えて f# であってに-f# コーディングします。 これらは、コンポーネント、およびライブラリ内で内部的に使用するときに、優れた実装デバイスです。

バニラ .NET API をデザインする場合は、プライベート宣言または署名ファイルを使用して、union 型の表現を非表示にすることを検討します。

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

目的を提供する、メンバーを持つ共用体の表現を内部的に使用する型を追加することも可能性があります。ネットワークに接続された API です。

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>GUI の設計やフレームワークのデザイン パターンを使用して他のコンポーネント

多くのさまざまなフレームワークは WinForms、WPF では、ASP.NET などの .NET 内で使用できます。 これらのフレームワークで使用するためのコンポーネントをデザインする場合は、それぞれの名前付けと設計の規則を使用してください。 たとえば、WPF のプログラミングでは、WPF のパターンのデザインをデザインするクラスを採用します。 ユーザー インターフェイスのプログラミング モデルでは、イベントなどのデザイン パターンを使用しておりなどのコレクションの通知に基づく<xref:System.Collections.ObjectModel>です。

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>オブジェクトとメンバーのデザイン (の他の .NET 言語から使用するライブラリ)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>CLIEvent 属性を使用して、.NET イベントを公開するには

構築、`DelegateEvent`で特定の .NET デリゲート オブジェクトを取得する型と`EventArgs`(ではなく、 `Event`、使用する、`FSharpHandler`既定では型) を他の .NET 言語の使い慣れた方法でイベントが発行するためです。

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>.NET のタスクを返すメソッドとしての非同期操作を公開します。

タスクは、アクティブな非同期計算を表す .NET で使用されます。 タスクは、一般的な f# より小さいアレンジ`Async<T>`オブジェクト、タスクの「は既に実行中」を表すされ、並列の構成を実行するか、キャンセルの信号、およびその他の伝達を非表示にする方法で同時に構成することはできませんコンテキスト パラメーターです。

ただし、この場合でもタスクを返すメソッドは .NET での非同期プログラミングの標準的な表現です。

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

多くの場合も、明示的なキャンセル トークンをそのまま使用します。

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>F# 関数型ではなく .NET 型のデリゲートを使用します。

ここで「f# 関数型」という意味では「矢印」型と同様に`int -> int`です。

代わりにします。

```fsharp
member this.Transform(f:int->int) =
    ...
```

方法 :

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

として f# 関数型が表示されます`class FSharpFunc<T,U>`他の .NET 言語にはデリゲート型を理解している言語機能とツールには適しています。 .NET Framework 3.5 以降を対象とする上位のメソッドを作成するときに、`System.Func`と`System.Action`デリゲートは、低摩擦方法でこれらの Api を使用する .NET 開発者に公開する右の Api です。 (.NET Framework 2.0 を対象とする場合、システム定義のデリゲート型は制限が多くなどの定義済みのデリゲート型の使用を検討`System.Converter<T,U>`または特定のデリゲート型を定義します)。

反対に、.NET のデリゲートが f# の自然な-ライブラリが直面している (f# で、次のセクションを参照してください-ライブラリが直面している)。 高階メソッドの標準の .NET ライブラリを開発するときに一般的な実装方法はすべて f# 関数型を使用して実装を作成し、実際の f# の最上部のシン ファサードとしてデリゲートを使用してパブリック API を作成、その結果、します。実装です。

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>F# オプション値を返す代わりに、TryGetValue パターンを使用して、引数としての f# のオプション値を取得するメソッドのオーバー ロードを優先

Api で f# オプションの種類の使用の一般的なパターンの適切な標準の .NET を使用して .NET Api バニラに実装されている手法をデザインします。 F# のオプションの値を返す代わりにブール型の戻り値の型と"TryGetValue"パターンと同様に out パラメーターを使用して検討してください。 F# オプション値をパラメーターとして使用すると、代わりに、メソッドのオーバー ロードまたは省略可能な引数を使用を検討してください。

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>使用して、.NET コレクション インターフェイス型 IEnumerable\<T\>および IDictionary\<キー、値\>パラメーターと戻り値

.NET の配列などの具体的なコレクション型の使用を避ける`T[]`、f# の型`list<T>`、`Map<Key,Value>`と`Set<T>`などの .NET の具体的なコレクション型と`Dictionary<Key,Value>`です。 .NET ライブラリのデザイン ガイドラインのようなさまざまなコレクション型を使用するに関する有益なアドバイスがある`IEnumerable<T>`です。 配列の一部を使用して (`T[]`) は状況によっては、パフォーマンス grounds を許容します。 特にことに注意してください`seq<T>`だけ、f# には別名が`IEnumerable<T>`、したがって seq は多くの場合、バニラ .NET API の適切な型とします。

代わりに f# の一覧を示します。

```fsharp
member this.PrintNames(names : string list) =
    ...
```

F# シーケンスを使用します。

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>引数を持たないメソッドを定義するメソッドの唯一の入力の型としてのユニットの種類を使用するか、唯一として void を返すメソッドを定義する型を返す

Unit 型の他の使用は避けてください。 これらは、適切です。

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

これは、正しくありません。

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>標準の .NET API 境界での null 値を確認

F# 実装コードは、変更できないデザイン パターンと f# の型の null リテラルの使用上の制限のためより少ないの null 値を持つ傾向があります。 他の .NET 言語多くの場合、値として null より頻繁に使用します。 このため、バニラ .NET API を公開する f# コードを API 境界で null のパラメーターをチェックし、これらの値が f# 実装コードをより深くをフローさせることを防止します。 `isNull`関数またはパターンに一致する、`null`パターンを使用することができます。

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>戻り値としての組は使用しないでください。

代わりに、集計のデータを保持するか、out パラメーターを使用して複数の値を返す名前付きの型を返すことを好みます。 組と構造体の組 .NET に存在して (c# の言語のサポート構造体の組を含む)、最もよくが用意されて理想的と予想される API .NET 開発者向けです。

#### <a name="avoid-the-use-of-currying-of-parameters"></a>パラメーターのカリー化は使用しないでください。

代わりに、呼び出し規約 .NET``Method(arg1,arg2,…,argN)``です。

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

ヒント: 任意の .NET 言語から使用するためのライブラリをデザインする場合はありません、実際にいくつか実験的な c# および Visual Basic プログラミングことを確認する「フィール右」これらの言語から、ライブラリの代用。 また、ライブラリと、ドキュメントが開発者に期待どおりに表示されていることを確認するのに .NET Reflector や Visual Studio のオブジェクト ブラウザーなどのツールを使用することができます。

## <a name="appendix"></a>付録

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>他の .NET 言語で使用するために f# コードの設計のエンド ツー エンドの例

次のクラスを考えます。

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

このクラスの推定の f# 型は次のとおりです。

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

他の .NET 言語を使用するプログラマがこの f# 型の表示方法を見てをみましょう。 たとえば、おおよそ c#「署名」とおりです。

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

F# でどのように表すかコンストラクトをここで注目してくださいいくつかの重要な点があります。 例えば:

* 引数の名前などのメタデータが保持されています。

* 2 つの引数を受け取る f# メソッドでは、c# のメソッドに 2 つの引数を受け取ることになります。

* 関数および一覧は、対応する型が f# ライブラリへの参照になります。

次のコードでは、これらの点を考慮に入れるには、このコードを調整する方法を示します。

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

コードの推定の f# 型は次のとおりです。

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

C# シグネチャを次に示しますようになりました。

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

修正プログラムは、標準の .NET ライブラリの一部は、次のとおり、この型を使用する準備に対して行われます。

* 複数の名前を調整: `Point1`、 `n`、 `l`、および`f`になった`RadialPoint`、 `count`、 `factor`、および`transform`、それぞれします。

* 戻り値の型を使用する`seq<RadialPoint>`の代わりに`RadialPoint list`一覧の構築を使用して、変更することによって`[ ... ]`を使用してシーケンスの構築に`IEnumerable<RadialPoint>`です。

* .NET のデリゲート型を使用する`System.Func`f# 関数型の代わりにします。

これにより、c# コードで使用するより良いまでです。
