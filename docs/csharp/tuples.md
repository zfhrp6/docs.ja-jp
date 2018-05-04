---
title: タプル - C# ガイド
description: C# の名前のないタプルと名前付きタプルについて
keywords: .NET, .NET Core, C#
author: BillWagner
ms-author: wiwagn
ms.date: 11/23/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 1d1fc450503dc905e6b260a2b984e3ce2315fd45
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="c-tuple-types"></a>C# のタプル型 #

C# のタプルは、軽量構文を使用して定義する型で、 構文がシンプルである、変換の規則が要素の数 ("カーディナリティ" と呼ばれます) と種類に基づく、コピーと割り当ての規則が一貫している、などのメリットがあります。 そのトレードオフとして、タプルでは、継承に関連するオブジェクト指向の表現形式の一部がサポートされていません。 概要については、[C# 7.0 の新機能のタプル](whats-new/csharp-7.md#tuples)に関するトピックのセクションをご覧ください。

このトピックでは、C# 7.0 以降でタプルに適用される言語の規則、タプルの使用方法、およびタプルを操作するための入門的ガイダンスについて説明します。

> [!NOTE]
> 新しいタプル機能を使用するには、<xref:System.ValueTuple> 型が必要です。
> 型が含まれていないプラットフォームで使用する場合は、NuGet パッケージ [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) を追加する必要があります。
>
> これは、フレームワークで提供される型に依存するその他の言語機能に似ています。 たとえば、`INotifyCompletion` インターフェイスに依存する `async` や `await`、`IEnumerable<T>` に依存する LINQ などがあります。 ただし、.NET がプラットフォームにさらに依存しなくなりつつあるため、配信メカニズムもそれに応じて変わりつつあります。 .NET Framework が、言語コンパイラと同じ周期で配布されるとは限りません。 新しい言語機能が新しい型に依存する場合、それらの型は、言語機能の配布時に NuGet パッケージとして入手できます。 これらの新しい型は .NET 標準 API に追加され、フレームワークの一部として配信されるため、NuGet パッケージは必要なくなります。

詳しく見ていく前に、新しいタプルのサポートを追加した理由について説明します。 メソッドが返すのは 1 つのオブジェクトです。 タプルを使用すると、その 1 つのオブジェクトに複数の値を簡単にパッケージできます。

.NET Framework には `Tuple` ジェネリック クラスが既にありますが、 このクラスには 2 つの大きな制限がありました。 1 つは、`Tuple` クラスのプロパティに `Item1`、`Item2` という名前が付けられるというものです。 その名前にはセマンティック情報が保持されていません。 つまり、この `Tuple` 型を使用しても、各プロパティの情報を伝達することはできません。 新しい言語機能を使用すると、タプルの要素に意味的にわかりやすい名前を宣言して使用できます。

さらに、`Tuple` クラスが参照型であるのも、懸念事項の 1 つです。 `Tuple` 型を使用するには、オブジェクトを割り当てる必要があります。 ホット パスでは、これがアプリケーションのパフォーマンスに大きな影響を及ぼすことがあります。 そのため、タプルの言語サポートでは、新しい `ValueTuple` 構造体を活用します。

`class` や `struct` を作成して複数の要素を伝達すれば、この弱点を回避できますが、 その分、手間が増え、設計の意図がわかりにくくなります。 `struct` や `class` を作成すると、データと動作の両方で型を定義しなければなりませんが、 1 つのオブジェクトに複数の値を格納したいだけという状況もよくあります。

これらの機能と `ValueTuple` ジェネリック構造体では、タプル型に動作 (メソッド) を追加できないという規則が適用されます。
すべての `ValueTuple` 型が "*mutable 構造体*" で、 各メンバー フィールドがパブリック フィールドであるため、 非常に軽量です。 ただし、不変性が重要な場合は、タプルを使用しないでください。

タプルは、`class` 型や `struct` 型に比べて、シンプルで柔軟なデータ コンテナーです。 両者の違いを見てみましょう。

## <a name="named-and-unnamed-tuples"></a>名前付きのタプルと名前がないタプル

既存の `Tuple` 型で定義されたプロパティと同様、`ValueTuple` 構造体のフィールドには `Item1`、`Item2`、`Item3` といった名前が付いています。
"*名前のないタプル*" には、この名前しか使用できません。 タプルに代替フィールド名を付けなかった場合は、名前のないタプルが作成されます。

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

前の例のタプルは、リテラル定数を使って初期化されており、C# 7.1 の*タプル フィールド名プロジェクション*を使って作成された要素名はありません。

タプルを初期化する際に、新しい機能を使用して、各フィールドにわかりやすい名前を付けることができます。 これによって、"*名前付きタプル*" が作成されます。
名前付きタプルには `Item1`、`Item2`、`Item3` という名前の要素がまだ存在しますが、
名前を付けた要素に対してシノニムも設定されます。
名前付きタプルを作成するには、各要素の名前を指定します。 たとえば、タプル初期化の一環として名前を指定できます。

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

コンパイラと言語によってシノニムが処理されるため、名前付きタプルを効果的に使用できるようになります。 IDE やエディターは Roslyn API を使用して、セマンティック名を読み取ります。 これにより、同じアセンブリ内の任意の場所で、セマンティック名によって名前付きタプルの要素を参照できます。 定義した名前は、コンパイル済み出力が生成されるときに、対応する `Item*` に置き換えられます。 これらの要素に設定した名前は、コンパイルされた Microsoft Intermediate Language (MSIL) には含まれません。

C# 7.1 以降、タプルのフィールド名は、タプルの初期化に使用した変数によって指定される場合があります。 これは、**[タプル プロジェクション初期化子](#tuple-projection-initializers)** と呼ばれます。 次のコードでは、要素 `count` (整数)、および `sum` (倍精度浮動小数点型) で `accumulation` という名前のタプルを作成します。

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

コンパイラは、パブリック メソッドまたはプロパティから返されたタプルに指定されている名前を伝える必要があります。 このような場合、コンパイラはメソッドに <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> 属性を追加します。 この属性には、タプルの各要素に付けられた名前が含まれた <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> リスト プロパティが含まれています。

> [!NOTE]
> Visual Studio などの開発ツールも、そのメタデータを読み取り、メタデータ フィールド名を使用する IntelliSense などの機能を提供します。

名前付きタプルを相互に割り当てるための規則を理解するには、新しいタプルと `ValueTuple` 型の基本を理解しておくことが重要です。

## <a name="tuple-projection-initializers"></a>タプル プロジェクション初期化子

一般に、タプル プロジェクション初期化子は、タプルの初期化ステートメントの右側にある変数またはフィールド名を使用して機能します。
明示的な名前が指定された場合は、射影された名前より優先されます。 たとえば、次の初期化子では、要素は `localVariableOne` や `localVariableTwo` ではなく、`explicitFieldOne` と `explicitFieldTwo` になります。

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

明示的な名前が指定されていないフィールドの場合、適用可能な暗黙的な名前が射影されます。 明示的または暗黙的のいずれかで、セマンティック名を指定するための要件はありません。 次の初期化子には、フィールド名 `Item1` があり、その値は `42` と `StringContent` で、その値は "The answer to everything" です。

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

候補フィールド名がタプル フィールドに射影されない場合の条件は 2 つあります。

1. 候補名が予約されているタプル名の場合。 例としては、`Item3`、`ToString` または `Rest` です。
1. 候補名が、別のタプル フィールド名 (明示的または暗黙的のいずれか) の複製である場合。

これらの条件によってあいまいさを回避します。 この名前がタプルのフィールドのフィールド名として使用される場合、あいまいさの原因となります。 この条件はどちらも、コンパイル時エラーを発生させることはありません。 代わりに、射影された名前のない要素には、射影されたセマンティック名がありません。  これらの条件の例を以下に示します。

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

これらの条件は、タプル フィールド名プロジェクションが利用できなかった場合、C# 7.0 で記述されたコードに対する重大な変更になるため、コンパイラ エラーが発生することはありません。

## <a name="assignment-and-tuples"></a>割り当てとタプル

要素の数が同じで、これらの各要素に型の暗黙的な変換があるタプル型間での、代入がサポートされています。 他の変換は、割り当てでは考慮されません。 タプル型間で許可されている割り当ての種類を見てみましょう。

以降の例で使用されている変数について考えます。

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

最初の 2 つの変数 `unnamed` および `anonymous` では、要素にセマンティック名が割り当てられていません。 フィールド名は `Item1` と `Item2` になります。
最後の 2 つの変数 `named` および `differentName` では、要素にセマンティック名が付けられています。 この 2 つのタプルでは、要素名が異なっていることに注意してください。

この 4 つのタプルに含まれている要素の数 ("カーディナリティ" と呼ばれます) と要素の型は同じです。 このため、これらの割り当てはすべて機能します。

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

タプルの名前が割り当てられていないことに注意してください。 要素の値は、タプルの要素の順序に従って割り当てられます。

要素の型または数が異なるタプルを割り当てることはできません。

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>メソッドの戻り値としてのタプル

タプルはメソッドの戻り値として使用できます。これはタプルの一般的な使用方法の 1 つです。 その例を見てみましょう。 数値シーケンスの標準偏差を計算する次のメソッドについて考えます。

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> この例では、未修正のサンプル標準偏差を計算します。
> 修正後のサンプル標準偏差式は、`Average` 拡張メソッドで行われるのと同様に、平均値との差の二乗和を、N ではなく (N-1) で除算します。 標準偏差のこうした数式の間に生じる差の詳細については、統計値のテキストを参照してください。

これは、標準偏差の教科書どおりの数式に従っています。 正しい答えが生成されますが、きわめて非効率的な実装です。 このメソッドは、シーケンスを 2 回列挙します。1 回は平均値を生成するため、もう 1 回は平均値との差を 2 乗して、その平均値を生成するためです 
(前述のとおり、LINQ クエリは遅延評価されるため、平均値との差と、その差の平均値の計算で生成される列挙は 1 つだけです)。

シーケンスの列挙を 1 つだけ使用して標準偏差を計算する、別の数式があります。  この計算では、シーケンスを列挙しながら、2 つの値が生成されます。1 つはシーケンス内のすべての項目の合計、もう 1 つは各値の二乗和です。

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

このバージョンでは、シーケンスを 1 回だけ列挙しますが、 最適な再利用可能なコードとは言えません。 操作を続けていくと、さまざまな統計計算処理の多くが、シーケンス内の項目数、シーケンスの合計、およびシーケンスの二乗和を使用していることがわかります。 このメソッドをリファクタリングし、その 3 つの値すべてを生成するユーティリティ メソッドを作成しましょう。

ここで、タプルが非常に役に立ちます。 

このメソッドを更新して、列挙中に計算された 3 つの値をタプルに格納しましょう。 そうすると、次のバージョンが作成されます。

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Visual Studio のリファクタリング サポートにより、主要な統計情報の機能をプライベート メソッドに抽出できます。 これにより、3 つの値 `Sum`、`SumOfSquares`、`Count` を含むタプル型を返す `private static` メソッドが作成されます。

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
編集を手動ですばやく行う必要がある場合は、使用できるオプションが他にもいくつかあります。 まず、`var` 宣言を使用することで、`ComputeSumAndSumOfSquares` メソッド呼び出しのタプルの結果を初期化できます。 `ComputeSumAndSumOfSquares` メソッド内に異なる 3 つの変数を作成することもできます。 最終的なバージョンは以下のようになります。

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

この最終バージョンは、この 3 つの値を必要とするすべてのメソッド、またはそのサブセットで使用できます。

このようなタプルを返すメソッドで要素の名前を管理するオプションが他にもサポートされています。

戻り値の宣言からフィールド名を削除して、名前のないタプルを返すことができます。

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

このタプルのフィールドは、`Item1`、`Item2`、`Item3` として扱う必要があります。
メソッドから返されたタプルの要素には、セマンティック名を指定することをお勧めします。

また、作成している LINQ クエリの最終的な結果が、選択したオブジェクトのプロパティが一部だけ含まれるプロジェクションとなるときも、タプルが非常に便利です。

従来、クエリの結果は、匿名型のオブジェクトのシーケンスに射影していましたが、 この方法には多くの制限が伴いました。メソッドの戻り値の型では、匿名型に名前を付けるのが簡単ではなかったからです。 代替手段として `object` や `dynamic` を結果の型に使用すると、パフォーマンス コストは大きくなります。

タプル型のシーケンスを返すのは簡単です。要素の名前と型は、コンパイル時に IDE ツールで使用することができます。
たとえば、次の ToDo アプリケーションを考えてみます。 ToDo リストの 1 つのエントリを表すために、次のようなクラスを定義します。

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

モバイル アプリケーションでサポートされるのは、タイトルしか表示されないコンパクト形式の現在の ToDo 項目です。 その LINQ クエリでは、ID とタイトルのみが含まれるプロジェクションが作成されます。 タプルのシーケンスを返すメソッドは、その設計を適切に表現しています。

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> C# 7.1 では、タプル プロジェクションを使用して、匿名型で名前が付けられたプロパティと同様の方法で、要素を使用する名前付きタプルを作成できます。 上記のコードでは、クエリ プロジェクションの `select` ステートメントで、要素 `ID` と `Title` を含むタプルを作成します。

名前付きタプルは、署名に含めることができます。 これによって、コンパイラと IDE ツールは静的チェックを行い、結果が正しく使用されていることを確認できます。 名前付きタプルには静的情報も含まれているため、リフレクション、動的バインドなど、コストのかかるランタイム機能を使用して結果を操作する必要がありません。

## <a name="deconstruction"></a>分解

タプル内のすべての項目を展開するには、メソッドによって返されるタプルを*分解*します。 タプルは 3 とおりの方法で分解できます。  まず、かっこの中で各フィールドの型を明示的に宣言して、タプルの要素ごとに個別の変数を作成することができます。

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

また、かっこの外に `var` キーワードを使用して、タプルの各フィールドに対して暗黙的に型指定された変数を宣言することもできます。

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

`var` キーワードは、かっこ内のいずれか 1 つの変数宣言に使用することも、すべての変数宣言に使用することもできます。 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

タプル内のフィールドすべての型が同じでも、かっこ外では使用できない型があることに注意してください。

既存の宣言を使用してタプルを分解することもできます。

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  既存の宣言をかっこ内の宣言と混在させることはできません。 たとえば、`(var x, y) = MyMethod();` は許可されません。 *x* はかっこ内で宣言されており、*y* は他の場所で以前に宣言されているため、これによりエラー CS8184 が生成されます。

### <a name="deconstructing-user-defined-types"></a>ユーザー定義型の分解

上に示したように、すべてのタプル型を分解できます。 また、ユーザー定義型 (クラス、構造体、またはインターフェイス) も簡単に分解できます。

型の作成者は、型を構成するデータ要素を表す任意の数の `out` 変数に対して値を割り当てる `Deconstruct` メソッドを 1 つ以上定義できます。 たとえば、次の `Person` 型は、person オブジェクトを、名と姓を表す要素に分解する `Deconstruct` メソッドを定義しています。

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

deconstruct メソッドを使用すると、`Person` から、`FirstName` プロパティと `LastName` プロパティを表す 2 つの文字列を割り当てることができます。

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

自分で作成していない型を分解することもできます。
`Deconstruct` メソッドは、オブジェクトのアクセス可能なデータ メンバーを展開する拡張メソッドとして使用できます。 次の例は、`Person` から派生した `Student` 型と、`Student` を 3 つの変数 `FirstName`、`LastName`、`GPA` に分解する拡張メソッドを示しています。

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

`Student` オブジェクトには、アクセス可能な `Deconstruct` メソッドが 2 つあります。`Student` 型に対して宣言された拡張メソッドと、`Person` 型のメンバーです。 両方ともスコープ内にあり、`Student` を 2 つまたは 3 つの変数に分解できます。
student を 3 つの変数に割り当てると、名、姓、GPA のすべてが返されます。 student を 2 つの変数に割り当てると、名と姓のみが返されます。

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

クラスまたはクラス階層で複数の `Deconstruct` メソッドを定義するときには注意が必要です。 `out` パラメーターの数が同じ `Deconstruct` メソッドが複数あると、あいまいさが生じ、 呼び出し元が、必要な `Deconstruct` メソッドを簡単には呼び出せなくなる場合があります。

この例では、出力パラメーターが `Person` の `Deconstruct` メソッドには 2 つ、`Student` の `Deconstruct` メソッドには 3 つ含まれるため、呼び出しが不明確になる可能性は最小限に抑えられています。

## <a name="conclusion"></a>まとめ 

クラスや構造体では動作の定義が必要であるため、新しい言語とライブラリで名前付きタプルがサポートされたことで、動作を定義せずに複数の要素を格納するデータ構造設計が格段に扱いやすくなりました。 こうした型に対してタプルを使用するのは簡単です。 詳細な `class` または `struct` 構文を使用して型を作成しなくても、静的な型チェックのすべてのメリットを利用できます。 とは言っても、class や struct は、`private` や `internal` のユーティリティ メソッドにとっては非常に便利です。 複数の要素を含む値がパブリック メソッドによって返される場合は、ユーザー定義型、`class` または`struct` を作成します。
