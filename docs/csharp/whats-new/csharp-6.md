---
title: C# 6 の新機能 - C# ガイド
description: C# バージョン 6 の新機能について説明します
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: d9f5c5ca94c04a873e4e98863f9fea3b8f477c1c
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34458006"
---
# <a name="whats-new-in-c-6"></a>C# 6 の新機能

C# の 6.0 リリースには、開発者の生産性を向上させる多くの機能が含まれています。 このリリースの新機能には、次の機能が含まれます。

* [読み取り専用の自動プロパティ](#read-only-auto-properties):
    - コンス トラクターでのみ設定できる、読み取り専用の自動プロパティ を作成できます。
* [自動プロパティの初期化子](#auto-property-initializers):
    - 自動プロパティの初期値を設定する初期化式を記述できます。
* [式形式の関数メンバー](#expression-bodied-function-members):
    - ラムダ式を使用して、1 行のメソッドを作成できます。
* [using static](#using-static):
    - 1 つのクラスのすべてのメソッドを、現在の名前空間にインポートできます。
* [null 条件演算子](#null-conditional-operators):
    - null 条件演算子で null をチェックしながら、オブジェクトのメンバーに簡潔かつ安全にアクセスできます。
* [文字列補間](#string-interpolation):
    - 位置指定引数の代わりに、インライン式を使用して書式設定文字列式をを記述できます。
* [例外フィルター](#exception-filters):
    - 例外のプロパティやその他のプログラム状態に基づいて、式をキャッチできます。 
* [nameof 式](#nameof-expressions):
    - コンパイラで記号の文字列表現を生成できます。
* [Catch ブロックと Finally ブロックでの Await](#await-in-catch-and-finally-blocks):
    - 以前は許可されなかった場所で `await` 式を使用できます。
* [インデックス初期化子](#index-initializers):
    - シーケンス コンテナーだけでなく、連想コンテナーの初期化式も作成できます。
* [コレクション初期化子の拡張メソッド](#extension-add-methods-in-collection-initializers):
    - コレクション初期化子に、メンバー メソッドだけでなく、使いやすい拡張メソッドを使用できます。
* [オーバーロード解決の改善](#improved-overload-resolution):
    - 以前はあいまいなメソッド呼び出しを生成していた一部のコンストラクトを、正しく解決できるようになりました。

これらの機能がもたらす全体的な効果として、より読みやすく簡潔なコードを記述できるようになりました。 一般的なベスト プラクティスを多数反映することで、構文に使用される形式的な記述が減っています。 形式的な記述が減ったことで、設計の意図が理解しやすくなっています。 これらの機能を十分に学習すれば、生産性が高まり、より読みやすいコードを記述できるようになります。また、言語の構造がわかりやすくなる分、コア機能の作業に専念できるようになります。

このトピックでは、これらの各機能について詳しく説明していきます。

## <a name="auto-property-enhancements"></a>自動プロパティの機能強化 

自動的に実装されるプロパティ (通常、"自動プロパティ" と呼ばれる) の構文は、get と set のシンプルなアクセサーを使ったプロパティの作成を簡単にしました。

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

ただし、このシンプルな構文では、自動プロパティを使ってサポートできる設計の種類に制限がありました。 C# 6 では、自動プロパティの機能が強化され、より多くのシナリオで自動プロパティを使用できるようなりました。 これにより、冗長な構文を宣言したり、バッキング フィールドを手動で操作する労力が軽減されます。

新しい構文は、読み取り専用のプロパティを扱うシナリオや、自動プロパティの背後での変数格納を初期化するシナリオに対応しています。

### <a name="read-only-auto-properties"></a>読み取り専用の自動プロパティ

*読み取り専用の自動プロパティ*を使用すると、より簡潔な構文で不変型を作成できます。 以前のバージョンの C# では、不変型を作成するための最も簡単な方法は、プライベート セッターを宣言する方法でした。

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
この構文を使用した場合、コンパイラは型が本当に変更不可であることを保証できません。 `FirstName` プロパティと `LastName` プロパティが、クラス外部のコードから変更されないようにするだけです。

読み取り専用の自動プロパティを使用すれば、真の読み取り専用動作を実現できます。 自動プロパティは、get アクセサーのみを使用して宣言します。

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

`FirstName` プロパティと `LastName` プロパティは、コンス トラクターの本体でのみ設定できます。

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

別のメソッドで `LastName` を設定しようとすると、コンパイル エラー `CS0200` が生成されます。

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

この機能を使用すれば、不変型を作成したり、より簡潔で便利な自動プロパティ構文を使用するための、本格的な言語サポートを実現できます。

### <a name="auto-property-initializers"></a>自動プロパティ初期化子

*自動プロパティ初期化子*を使用すると、プロパティ宣言の一部として自動プロパティの初期値を宣言できます。  以前のバージョンでは、これらのプロパティにはセッターが必要でした。そのセッターを使用して、バッキング フィールドによって使用されるデータ ストレージを初期化する必要がありました。 たとえば、生徒の名前と成績を含んだ、生徒用のクラスがあるとします。

[!code-csharp[Construction](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Construction)]
 
このクラスが大きくなってくると、他のコンス トラクターが追加されることもあるでしょう。 各コンス トラクターでは、このフィールドを初期化する必要があります。そうしないとエラーが発生します。

C# 6 では、自動プロパティ宣言で自動プロパティによって使用されるストレージの初期値を割り当てることができます。

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

`Grades` メンバーは宣言された場所で初期化されます。 これにより、初期化を厳密に 1 回だけ実行しやすくなります。 初期化がプロパティ宣言の一部になることで、ストレージ割り当てが `Student` オブジェクトのパブリック インターフェイスと同じであることを示しやすくなっています。

次のように、プロパティ初期化子は読み取り専用プロパティだけでなく、読み取り/書き込みプロパティにも使用できます。

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a>式形式の関数メンバー

開発者が記述する多くのメンバーの本文は、式として表すことができる 1 つのステートメントだけで構成されます。 これに代えて式形式のメンバーを記述すれば、その構文を減らすことができます。 この方法は、メソッドと読み取り専用プロパティに有効です。 たとえば、`ToString()` のオーバーライドはその好例です。

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

式形式のメンバーは、読み取り専用のプロパティにも使用できます。

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

## <a name="using-static"></a>using static

*using static* 拡張機能を使用すると、1 つのクラスの静的メソッドをインポートすることができます。 これまで、`using` ステートメントは名前空間内のすべての型をインポートしていました。 

開発者はクラスの静的メソッドをコード内の随所で使用することがよくありますが、 クラス名を繰り返し入力すると、コードの意味がわかりにくくなることもあります。 一般的な例としては、多数の数値計算を実行するクラスが挙げられます。
このようなクラスでは、<xref:System.Math> クラス内の異なるメソッドに対する <xref:System.Math.Sin%2A>、<xref:System.Math.Sqrt%2A>、およびその他の呼び出しがコード内に散在することになります。 新しい `using static` 構文では、これらのクラスを大幅に簡潔化し、読みやすくすることができます。 具体的には、使用するクラスを次のように指定します。

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

これで、<xref:System.Math> クラスを修飾しなくても、<xref:System.Math> クラス内の任意の静的メソッドを使用できます。 <xref:System.Math> クラスにはインスタンス メソッドが含まれていないので、この機能が特に役に立ちます。 また `using static` は、静的メソッドとインスタンス メソッドの両方を持つクラスの静的クラスをインポートするためにも使用できます。 特に便利な例の 1 つが <xref:System.String> です。

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> static using ステートメントでは、完全修飾クラス名 (`System.String`) 使用する必要があります。 代わりに `string` キーワードを使用することはできません。 

これで、<xref:System.String> クラス内で定義された静的メソッドを、そのクラスのメンバーとして修飾しなくても呼び出せるようになります。

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

`static using` 機能と拡張メソッドは興味深い方法で相互作用し、言語設計には、それらの相互作用に具体的に対応するいくつかのルールが含まれています。 その目的は、既存のコードベース (ユーザーのコードを含む) に重大な変更が生じる可能性を最小限に減らすことです。

拡張メソッドは、拡張メソッドの呼び出し構文を使用して呼び出された場合にのみ、スコープ内に含められます。静的メソッドとして呼び出された場合には含められません。
これは、LINQ クエリで多く見受けられることになるでしょう。 LINQ パターンは、<xref:System.Linq.Enumerable> をインポートすることによってインポートできます。

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

このコードは、<xref:System.Linq.Enumerable> クラス内のすべてのメソッドをインポートします。
ただし拡張メソッドは、拡張メソッドとして呼び出された場合にしかスコープ内に含められません。 静的メソッドの構文を使用して呼び出された場合には、スコープに含められません。

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

このような仕様になったのは、拡張メソッドが通常、拡張メソッドの呼び出し式を使用して呼び出されるためです。 まれに、静的メソッドの呼び出し構文を使用して呼び出される場合もありますが、それはあいまいさを解決するためです。
呼び出しには必ずクラス名を含めるようにするのが賢明と言えるでしょう。

最後に、`static using` の機能がもう1 つあります。 `static using` ディレクティブは、入れ子にされた型もインポートします。 これにより、入れ子になった型を修飾なしで参照できるようになっています。

## <a name="null-conditional-operators"></a>Null 条件演算子

Null 値はコードを複雑にします。 開発者は変数のアクセスをすべてチェックして、`null` を逆参照していないことを確認する必要があります。 *Null 条件演算子*を使用すれば、これらのチェックをより簡単で円滑なものにすることができます。

やり方は、メンバー アクセス `.` を `?.` 置き換えるだけです。

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

上記の例では、person オブジェクトが `null` の場合に、変数 `first` に `null` が割り当てられます。 その他の場合には、`FirstName` プロパティの値が割り当てられます。 特に重要なのは、`?.` を使用した場合、変数 `person` が `null` であっても、このコード行では `NullReferenceException` が生成されないということです。 代わりに、処理がショートサーキットされ、`null` が生成されます。

また、この式は `string` の値に関係なく、`person` を返します。
処理がショート サーキットされた場合は、返された `null` 値が式全体に一致するように入力されます。

*null 結合*演算子を使用したこのコンストラクトは、いずれかのプロパティが `null` の場合に既定値を割り当てる目的で使用できます。

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

`?.` 演算子の右側のオペランドは、プロパティやフィールドに制限されません。
メソッドを条件付きで呼び出すためにも使用できます。 Null 条件演算子を使用したメンバー関数の最も一般的な用途は、`null` である可能性があるデリゲート (またはイベント ハンドラー) を安全に呼び出すことです。  これを行うには、`?.` 演算子を使用してデリゲートの `Invoke` メソッドを呼び出し、メンバーにアクセスします。 この例は、  
[デリゲート パターン](../delegates-patterns.md#handling-null-delegates)に関するトピックに記載されています。

`?.` 演算子のルールでは、、演算子の左側が 1 回だけ評価されることが保証されています。 これは重要なことであり、これによって多くの表現方法が可能になります (イベント ハンドラーを使用した例を含む)。 まずは、イベント ハンドラーを使用した例から見ていきましょう。 以前のバージョンの C# では、コードを次のように記述することが推奨されていました。

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

これは、次のような単純な構文よりも推奨されていました。

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> 上記の例では、競合状態が発生しています。 `SomethingHappened` イベントは、`null` に対してチェックされた時点ではサブスクライバーが存在する可能性がありますが、それらのサブスクライバーは、イベントが生成する前に削除される可能性もあります。 その場合、<xref:System.NullReferenceException> がスローされます。

この 2 つ目のバージョンでは、`SomethingHappened` イベント ハンドラーがテスト時に Null 以外である可能性もありますが、その他のコードによってハンドラーが削除された場合には、イベント ハンドラーの呼び出し時に Null になっている可能性もあります。

`?.` 演算子に対してコンパイラが生成するコードでは、`?.` 式の左側 (`this.SomethingHappened`) が 1 回だけ評価され、その結果がキャッシュされます。

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

左側が 1 回しか評価されないことが確実であるということは、`?.` の左側で任意の式 (メソッド呼び出しを含む) を使用できるということでもあります。それらに副作用があったとしても、1 回しか評価されないので、副作用も 1 回しか発生しません。 この例は、[イベント](../events-overview.md#language-support-for-events)に関するコンテンツで参照できます。

## <a name="string-interpolation"></a>文字列補間

C# 6 で導入された新しい構文では、書式文字列と、その他の文字列値を生成するために評価される式から、文字列を作成することができます。

これまでは、`string.Format` などのメソッドで位置指定パラメーターを使用する必要がありました。

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

C# 6 では、新しい[文字列補間](../language-reference/tokens/interpolated.md)機能を使用して、書式文字列に式を埋め込むことができます。 方法は、文字列の前に `$` を付けるだけです。

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

この最初の例では、置換される式にプロパティ式を使用しています。 この構文を拡張することで、任意の式を使用することができます。 たとえば、補間の一部として生徒の評価点の平均を計算することもできます。

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

上記の例を実行すると、`Grades.Average()` の出力に含まれる小数点以下の桁数が、開発者の意図よりも多くなる場合があることに気付くでしょう。 文字列補間の構文では、これまでの書式設定メソッドを通じて利用できるすべての書式がサポートされます。 中かっこ内に書式文字列を追加し、 書式設定する式 の後に、`:` を追加します。

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

上記のコード行では、`Grades.Average()` の値が、小数点以下 2 桁の浮動小数点数として書式設定されます。

`:` は常に、書式設定される式と書式文字列との間の区切り記号として解釈されます。 そのため、`:` が式内で別の目的 (条件演算子など) に使用されている場合には、問題が生じる可能性があります。

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

上記の例では、`:` は条件演算子の一部ではなく、書式文字列の開始点として解析されます。 このような場合には、式を中かっこで囲むことで、コンパイラに正しく式を解釈させることができます。

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

中かっこの間に配置できる式に制限はありません。 補間文字列内で複雑な LINQ クエリを実行して計算を実行し、結果を表示することもできます。

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

この例のように、文字列補間式の内部で、別の文字列補間式を入れ子にすることもできます。 この例は開発者が運用コードで使用するものよりも複雑である可能性が高いですが、
この機能の対応範囲を説明するためにあえて示しました。 補間文字列の中かっこの間には、任意の C# 式を配置できます。

### <a name="string-interpolation-and-specific-cultures"></a>文字列補間と特定のカルチャ

前のセクションで示した例はいずれも、コードが実行されるマシンの現在のカルチャと言語を使用して文字列を書式設定するものでした。 しかし場合によっては、生成された文字列を特定のカルチャで書式設定する必要が生じる場合もあるでしょう。
これを行うには、文字列補間によって生成されたオブジェクトは暗黙的に <xref:System.FormattableString> に変換できることを利用します。

<xref:System.FormattableString> インスタンスには、書式文字列と、それらを文字列に変換する前の式評価の結果が含まれます。 <xref:System.FormattableString> のパブリック メソッドを使用すれば、文字列の書式設定時にカルチャを指定することができます。 たとえば、次の例は、ドイツのカルチャを使用して文字列を生成します。 (小数点区切り文字に ',' 文字が使用され、桁区切り記号に '.' 文字が使用されます。)

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

詳細については、[文字列補間](../language-reference/tokens/interpolated.md)に関するトピックを参照してください。

## <a name="exception-filters"></a>例外フィルター

C# 6 では、*例外フィルター*という新機能も追加されています。 例外フィルターは、特定の catch 句がいつ適用されるのかを決定する句です。
例外フィルターに使用されている式が `true` と評価された場合、catch 句は例外に対して通常の処理を実行します。 式が `false` と評価された場合、`catch` 句はスキップされます。

用途としては、例外に関する情報を調べて、`catch` 句で例外を処理できるかどうかを確認するという使い方があります。

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

例外フィルターによって生成されたコードには、スローされ、処理されていない例外についての詳細な情報が含まれます。 例外フィルターがこの言語に追加される以前は、次のようなコードを作成する必要がありました。

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

これら 2 つの例では、例外がスローされるポイントが異なります。
旧来のコード (`throw` 句を使用したコード) では、スタック トレースの分析やクラッシュ ダンプの調査を実行した場合、catch 句内の `throw` ステートメントから例外がスローされたと示されます。 実際の例外オブジェクトには元の呼び出し履歴が含まれますが、このスロー ポイントと元のスロー ポイントとの間での呼び出し履歴内にあるその他の変数情報はすべて失われます。 

これに対し、例外フィルターを使用したコードはどのように処理されるかというと、例外フィルター式が `false` と評価されます。 そのため、`catch` 句が実行されることはありません。 `catch` 句が実行されないので、スタックのアンワインドは行われません。 つまり、以降に発生するいずれのデバッグ活動においても、元のスロー場所が保持されます。

例外の種類のみを使用するのではなく、例外のフィールドやプロパティも評価する必要がある場合には、必ず例外フィルターを使用して、デバッグの詳細を保持するようにしてください。

例外フィルターを使用するもう 1 つの推奨パターンとして、ルーチンのロギングがあります。 例外フィルターが `false` と評価された場合に例外のスロー ポイントが保持されるという動作は、この用途でも役に立ちます。

次の例では、無条件に `false` を返す例外を、ロギング メソッドの引数にしています。

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

例外をログに記録する必要がある場合には、catch 句を追加し、このメソッドを例外フィルターとして使用できます。

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

`LogException` メソッドは常に `false` を返するため、例外はキャッチされません。 常に false となるこの例外フィルターを使用すれば、このロギング ハンドラーを、他のどの例外ハンドラーよりも前に配置することができます。

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

上記の例は、例外フィルターの非常に重要な特徴を示しています。
それは、例外フィルターを使用すれば、詳細な例外 catch 句よりも前に、より一般的な例外 catch 句が配置されるシナリオにも対応できるということです。 また、複数の catch 句に同じ種類の例外を配置することもできます。

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

もう 1 つの推奨パターンとして、デバッガーがアタッチされている場合には catch 句で例外を処理しないようにする用途もあります。 この手法を使用すれば、デバッガーを使ってアプリケーションを実行し、例外がスローされた場合には実行を停止することができます。

具体的には、コードに例外フィルターを追加して、デバッガーがアタッチされていない場合にのみ、修復コードが実行されるようにします。

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

この記述をコードに追加した後、すべての未処理例外に対して処理を中断するようにデバッガーを設定します。 その後デバッガーを使用してプログラムを実行すると、デバッガーは `PerformFailingOperation()` が `RecoverableException` をスローするたびに処理を中断します。
false を返す例外フィルターがあるため catch 句は実行されず、デバッガーがプログラムを中断します。

## <a name="nameof-expressions"></a>`nameof` 式

`nameof` 式はシンボルの名前を評価します。 この式は、変数、プロパティ、またはメンバー フィールドの名前が必要なときに便利です。

`nameof` の用途として特に一般的なものの 1 つは、例外の原因となったシンボルの名前を取得することです。

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

また、`INotifyPropertyChanged` インターフェイスを実装する XAML ベースのアプリケーションでも使用されます。

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

`nameof` 演算子が定数文字列よりも便利な点は、ツールがシンボルを把握できるという点です。 リファクタリング ツールを使用してシンボルの名前を変更すると、その名前が `nameof` 式で変更されます。 これは、定数文字列にはない利点です。 好みのエディターを使用して変数の名前を変更すれば、`nameof` 式も更新されます。

`nameof` 式は、開発者が引数の完全修飾名を使用した場合でも、引数の非修飾名 (上記の例では `LastName`) を生成します。

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

この `nameof` 式では、`UXComponents.ViewModel.FirstName` ではなく、`FirstName` が生成されます。

## <a name="await-in-catch-and-finally-blocks"></a>Catch ブロックと Finally ブロックでの Await

C# 5 では、`await` 式を配置できる位置について、いくつかの制限がありました。
C# 6 では、そのうちの 1 つが解消され、 `await` を `catch` 式や `finally` 式で使用できるようになりました。 

catch や finally のブロックに await を追加すると、それらの処理方法が複雑になるように思えるかもしれないので、 コード例で説明していきましょう。 非同期メソッドでは、finally 句で await 式を使用できます。

C# 6 では、catch 式でも await を使用することができます。 次に示すのは、ロギングのシナリオで特によく使用されるコードです。

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

`catch` 句と `finally` 句の内部に `await` のサポートを追加するための実装詳細では、その動作と、同期コードの動作との整合性が保証されています。 `catch` または `finally` 句で実行されたコードがエラーをスローした場合、プログラムは次の包含ブロック内から適切な `catch` 句を検索します。 現行の例外があった場合、その例外は失われます。 `catch` 句や `finally` 句で待機中の式についても、これと同じことが起こります。つまり、適切な `catch` が検索され、現行の例外がある場合は、その例外が失われます。  

> [!NOTE]
> この動作を理由に、`catch` 句と `finally` 句は慎重に記述することが推奨されています (新しい例外が導入されないようにしてください)。

## <a name="index-initializers"></a>インデックス初期化子

*インデックス初期化子*は、コレクション初期化子の一貫性を高める 2 つの機能のうちの 1 つです。 C# の以前のリリースでは、*コレクション初期化子*はシーケンス スタイルのコレクションでのみ使用できました。

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

C# 6 では、<xref:System.Collections.Generic.Dictionary%602> コレクションや、それと同様の型でも使用できるようになりました。

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

この機能が加わったことにより、いくつかのバージョンでシーケンス コンテナーに使用されていたものと同様の構文を使用して、連想コンテナーを初期化できるようになりました。

## <a name="extension-add-methods-in-collection-initializers"></a>コレクション初期化子内の拡張 `Add` メソッド

コレクション初期化を使いやすくするもう 1 つの機能として、 *メソッドの*拡張メソッド`Add`を使用できるようになりました。 この機能は、Visual Basic との同等性を確保するために追加されました。 

この機能は、新しい項目を意味的に追加するために、カスタム コレクション クラスで別の名前のメソッドを使用している場合に特に便利です。

たとえば、次のような生徒のコレクションがあるとします。

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

`Enroll` メソッドは生徒を追加しますが、 `Add` パターンには従いません。
C# の以前のバージョンでは、コレクション初期化子は `Enrollment` オブジェクトには使用できませんした。

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

C# 6 ではこれが可能になりましたが、`Add` を `Enroll` にマップする拡張メソッドを作成した場合に限られます。

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

この機能を使用してできることは、拡張メソッドを作成することによって、コレクションに項目を追加する任意のメソッドを、`Add` という名前のメソッドにマップするということです。

## <a name="improved-overload-resolution"></a>オーバーロード解決の改善

最後に説明するのは、言われなければ気付かないかもしれない機能です。 以前のバージョンの C# コンパイラでは、ラムダ式を使用した一部のメソッド呼び出しがあいまいと判断されるコンストラクトがありました。 たとえば、次のメソッドがあったとします。

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

以前のバージョンの C# では、メソッド グループ構文を使用してこのメソッドを呼び出すと、エラーが発生していました。

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
以前のコンパイラでは、`Task.Run(Action)` と `Task.Run(Func<Task>())` を正しく区別することができませんでした。 以前のバージョンでは、引数としてラムダ式を使用する必要がありました。

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

C# 6 の コンパイラは、`Task.Run(Func<Task>())` のほうが適切であるということを正しく判断できます。
