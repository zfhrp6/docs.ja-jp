---
title: "タプル | C# ガイド"
description: "C の名前のないタプルと名前付きタプルについて#"
keywords: .NET, .NET Core, C#
author: BillWagner
ms-author: wiwagn
ms.date: 11/23/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f2c81b7e18f36bde5b46c0c6df5c8122cd303931
ms.lasthandoff: 03/13/2017

---

# <a name="c-tuple-types"></a>C# のタプル型 #

C# のタプルは、軽量構文を使用して定義する型で、 構文がシンプルである、変換の規則がフィールドの数 ("アリティ" と呼ばれます) と種類に基づく、コピーと割り当ての規則が一貫している、などのメリットがあります。 そのトレードオフとして、タプルでは、継承に関連するオブジェクト指向の表現形式の一部がサポートされていません。 概要については、[C# 7 の新機能のタプル](csharp-7.md#tuples)に関するトピックのセクションをご覧ください。

このトピックでは、C# 7 でタプルに適用される言語の規則、タプルの使用方法、およびタプルを操作するための入門的ガイダンスについて説明します。

> [!NOTE]
> 新しいタプル機能を使用するには、`System.ValueTuple` 型が必要です。 Visual Studio 2017 の場合、NuGet ギャラリーで入手可能な NuGet パッケージ [System.ValueTuple](https://www.nuget.org/packages/System.ValueTuple/) を追加する必要があります。
> このパッケージがないと、`error CS8179: Predefined type 'System.ValueTuple``2' is not defined or imported`、`error CS8137: Cannot define a class or member that utilizes tuples because the compiler required type 'System.Runtime.CompilerServices.TupleElementNamesAttribute' cannot be found.` などのコンパイル エラーが発生する可能性があります

詳しく見ていく前に、新しいタプルのサポートを追加した理由について説明します。 メソッドが返すのは 1 つのオブジェクトです。 タプルを使用すると、その 1 つのオブジェクトに複数の値を簡単にパッケージできます。 

.NET Framework には `Tuple` ジェネリック クラスが既にありますが、 このクラスには 2 つの大きな制限がありました。 1 つは、`Tuple` クラスのフィールドに `Item1`、`Item2` という名前が付けられる、というもので、 その名前にはセマンティック情報が保持されていません。 つまり、この `Tuple` 型を使用しても、各フィールドの情報を伝達することはできません。 さらに、`Tuple` クラスが参照型であるのも、懸念事項の 1 つです。 `Tuple` 型を使用するには、オブジェクトを割り当てる必要があります。 ホット パスでは、これがアプリケーションのパフォーマンスに大きな影響を及ぼすことがあります。

`class` や `struct` を作成して複数のフィールドを指定すれば、この弱点を回避できますが、 その分、手間が増え、設計の意図がわかりにくくなります。 `struct` や `class` を作成すると、データと動作の両方で型を定義しなければなりませんが、 1 つのオブジェクトに複数の値を格納したいだけという状況もよくあります。

タプルの新しい機能は、フレームワークの新しいクラスと組み合わされて、このような弱点に対処しています。 新しいタプルでは、新しい `ValueTuple` ジェネリック構造体が使用されます。 名前からわかるように、この型は、`class` ではなく `struct` です。 この構造体にはさまざまなバージョンがあり、さまざまな数のフィールドを含むタプルがサポートされます。 新しいサポートでは、タプル型のフィールドにセマンティック名が提供されるほか、タプル フィールドの構築やタプル フィールドへのアクセスを容易にする機能も用意されています。

これらの機能と `ValueTuple` ジェネリック構造体では、タプル型に動作 (メソッド) を追加できないという規則が適用されます。
すべての `ValueTuple` 型が "*mutable 構造体*" で、 各メンバー フィールドがパブリック フィールドであるため、 非常に軽量です。 ただし、不変性が重要な場合は、タプルを使用しないでください。

タプルは、`class` 型や `struct` 型に比べて、シンプルで柔軟なデータ コンテナーです。 両者の違いを見てみましょう。

## <a name="named-and-unnamed-tuples"></a>名前付きのタプルと名前がないタプル

既存の `Tuple` 型で定義されたプロパティと同様、`ValueTuple` 構造体のフィールドには `Item1`、`Item2`、`Item3` といった名前が付いています。
"*名前のないタプル*" には、この名前しか使用できません。 タプルに代替フィールド名を付けなかった場合は、名前のないタプルが作成されます。

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "名前のないタプル")]

タプルを初期化する際に、新しい機能を使用して、各フィールドにわかりやすい名前を付けることができます。 これによって、"*名前付きタプル*" が作成されます。
名前付きタプルには `Item1`、`Item2`、`Item3` という名前のフィールドがまだ存在しますが、
名前を付けたフィールドに対してシノニムが設定されます。
名前付きタプルを作成するには、各フィールドの名前を指定します。 たとえば、タプル初期化の一環として名前を指定できます。

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "名前付きタプル")]

コンパイラと言語によってシノニムが処理されるため、名前付きタプルを効果的に使用できるようになります。 IDE やエディターは Roslyn API を使用して、セマンティック名を読み取ります。 これにより、同じアセンブリ内の任意の場所で、セマンティック名によって名前付きタプルのフィールドを参照できます。 定義した名前は、コンパイル済み出力が生成されるときに、対応する `Item*` に置き換えられます。 これらのフィールドに設定した名前は、コンパイルされた Microsoft Intermediate Language (MSIL) には含まれません。 

コンパイラは、パブリック メソッドまたはプロパティから返されたタプルに指定されている名前を伝える必要があります。 このような場合、コンパイラはメソッドに `TupleElementNames` 属性を追加します。 この属性には、タプルの各フィールドに付けられた名前が含まれた `TransformNames` リスト プロパティが含まれています。 

> [!NOTE]
> Visual Studio などの開発ツールも、そのメタデータを読み取り、メタデータ フィールド名を使用する IntelliSense などの機能を提供します。

名前付きタプルを相互に割り当てるための規則を理解するには、新しいタプルと `ValueTuple` 型の基本を理解しておくことが重要です。

## <a name="assignment-and-tuples"></a>割り当てとタプル

フィールドの数と型が同じタプル型間での割り当てがサポートされています。 型は、コンパイル時に完全に一致している必要があります。 他の変換は、割り当てでは考慮されません。 タプル型間で許可されている割り当ての種類を見てみましょう。

以降の例で使用されている変数について考えます。

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "変数の作成")]

最初の 2 つの変数 `unnamed` および `anonymous` では、フィールドにセマンティック名が割り当てられていません。 フィールド名は `Item1` と `Item2` になります。
最後の 2 つの変数 `named` および `differentName` では、フィールドにセマンティック名が付けられています。 この 2 つのタプルでは、フィールド名が異なっていることに注意してください。

この 4 つのタプルに含まれているフィールドの数 ("アリティ" と呼ばれます) とフィールドの型は同じです。 このため、これらの割り当てはすべて機能します。

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "変数の割り当て")]

タプルの名前が割り当てられていないことに注意してください。 フィールドの値は、タプルのフィールドの順序に従って割り当てられます。

フィールドの型または数が異なるタプルを割り当てることはできません。

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>メソッドの戻り値としてのタプル

タプルはメソッドの戻り値として使用できます。これはタプルの一般的な使用方法の 1 つです。 その例を見てみましょう。 数値シーケンスの標準偏差を計算する次のメソッドについて考えます。

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "標準偏差を計算する")]

> [!NOTE]
> この例では、未修正のサンプル標準偏差を計算します。
> 修正後のサンプル標準偏差式は、`Average` 拡張メソッドで行われるのと同様に、平均値との差の二乗和を、N ではなく (N-1) で除算します。 標準偏差のこうした数式の間に生じる差の詳細については、統計値のテキストを参照してください。

これは、標準偏差の教科書どおりの数式に従っています。 正しい答えが生成されますが、きわめて非効率的な実装です。 このメソッドは、シーケンスを 2 回列挙します。1 回は平均値を生成するため、もう 1 回は平均値との差を 2 乗して、その平均値を生成するためです 
(前述のとおり、LINQ クエリは遅延評価されるため、平均値との差と、その差の平均値の計算で生成される列挙は 1 つだけです)。

シーケンスの列挙を 1 つだけ使用して標準偏差を計算する、別の数式があります。  この計算では、シーケンスを列挙しながら、2 つの値が生成されます。1 つはシーケンス内のすべての項目の合計、もう 1 つは各値の二乗和です。

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "二乗和を使用して標準偏差を計算する")]

このバージョンでは、シーケンスを 1 回だけ列挙しますが、 最適な再利用可能なコードとは言えません。 操作を続けていくと、さまざまな統計計算処理の多くが、シーケンス内の項目数、シーケンスの合計、およびシーケンスの二乗和を使用していることがわかります。 このメソッドをリファクタリングし、その 3 つの値すべてを生成するユーティリティ メソッドを作成しましょう。

ここで、タプルが非常に役に立ちます。 

このメソッドを更新して、列挙中に計算された 3 つの値をタプルに格納しましょう。 そうすると、次のバージョンが作成されます。

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "リファクタリングしてタプルを使用する")]

Visual Studio のリファクタリング サポートにより、主要な統計情報の機能をプライベート メソッドに抽出できます。 これにより、3 つの値 `Sum`、`SumOfSquares`、`Count` を含むタプル型を返す `private static` メソッドが作成されます。

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "ユーティリティ メソッドの抽出後")]
 
編集を手動ですばやく行う必要がある場合は、使用できるオプションが他にもいくつかあります。 まず、`var` 宣言を使用することで、`ComputeSumAndSumOfSquares` メソッド呼び出しのタプルの結果を初期化できます。 `ComputeSumAndSumOfSquares` メソッド内に異なる 3 つの変数を作成することもできます。 最終的なバージョンは以下のようになります。

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "最後のクリーンアップ後")]

この最終バージョンは、この 3 つの値を必要とするすべてのメソッド、またはそのサブセットで使用できます。

このようなタプルを返すメソッドでフィールドの名前を管理するオプションが他にもサポートされています。

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
メソッドから返されたタプルのフィールドには、セマンティック名を指定することをお勧めします。

また、作成している LINQ クエリの最終的な結果が、選択したオブジェクトのプロパティが一部だけ含まれるプロジェクションとなるときも、タプルが非常に便利です。

従来、クエリの結果は、匿名型のオブジェクトのシーケンスに射影していましたが、 この方法には多くの制限が伴いました。メソッドの戻り値の型では、匿名型に名前を付けるのが簡単ではなかったからです。 代替手段として `object` や `dynamic` を結果の型に使用すると、パフォーマンス コストは大きくなります。

タプル型のシーケンスを返すのは簡単です。フィールドの名前と型は、コンパイル時に IDE ツールで使用することができます。
たとえば、次の ToDo アプリケーションを考えてみます。 ToDo リストの 1 つのエントリを表すために、次のようなクラスを定義します。

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do 項目")]

モバイル アプリケーションでサポートされるのは、タイトルしか表示されないコンパクト形式の現在の ToDo 項目です。 その LINQ クエリでは、ID とタイトルのみが含まれるプロジェクションが作成されます。 タプルのシーケンスを返すメソッドは、その設計を適切に表現しています。

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "タプルを返すクエリ")]

名前付きタプルは、署名に含めることができます。 これによって、コンパイラと IDE ツールは静的チェックを行い、結果が正しく使用されていることを確認できます。 名前付きタプルには静的情報も含まれているため、リフレクション、動的バインドなど、コストのかかるランタイム機能を使用して結果を操作する必要がありません。

## <a name="deconstruction"></a>分解

タプル内のすべての項目を展開するには、メソッドによって返されるタプルを "*分解*" します。 タプルは 2 とおりの方法で分解できます。  まず、かっこの中で各フィールドの型を明示的に宣言して、タプルのフィールドごとに個別の変数を作成することができます。

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "分解する")]

また、かっこの外に `var` キーワードを使用して、タプルの各フィールドに対して暗黙的に型指定された変数を宣言することもできます。

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Var に分解する")]

`var` キーワードは、かっこ内のいずれか 1 つの変数宣言に使用することも、すべての変数宣言に使用することもできます。 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```
タプル内のフィールドすべての型が同じでも、かっこ外では使用できない型があることに注意してください。

### <a name="deconstring-user-defined-types"></a>ユーザー定義型の分解

上に示したように、すべてのタプル型を分解できます。 また、ユーザー定義型 (クラス、構造体、またはインターフェイス) も簡単に分解できます。

型の作成者は、型を構成するデータ要素を表す任意の数の `out` 変数に対して値を割り当てる `Deconstruct` メソッドを 1 つ以上定義できます。 たとえば、次の `Person` 型は、person オブジェクトを、名と姓を表すフィールドに分解する `Deconstruct` メソッドを定義しています。

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "deconstruct メソッドと型")]

deconstruct メソッドを使用すると、`Person` から、`FirstName` プロパティと `LastName` プロパティを表す 2 つの文字列を割り当てることができます。

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "クラス型を分解する")]

自分で作成していない型を分解することもできます。
`Deconstruct` メソッドは、オブジェクトのアクセス可能なデータ メンバーを展開する拡張メソッドとして使用できます。 次の例は、`Person` から派生した `Student` 型と、`Student` を 3 つの変数 `FirstName`、`LastName`、`GPA` に分解する拡張メソッドを示しています。

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "deconstruct 拡張メソッドと型")]

`Student` オブジェクトには、アクセス可能な `Deconstruct` メソッドが 2 つあります。`Student` 型に対して宣言された拡張メソッドと、`Person` 型のメンバーです。 両方ともスコープ内にあり、`Student` を 2 つまたは 3 つの変数に分解できます。
student を 3 つの変数に割り当てると、名、姓、GPA のすべてが返されます。 student を 2 つの変数に割り当てると、名と姓のみが返されます。

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "拡張メソッドを使用してクラス型を分解する")]

クラスまたはクラス階層で複数の `Deconstruct` メソッドを定義するときには注意が必要です。 `out` パラメーターの数が同じ `Deconstruct` メソッドが複数あると、あいまいさが生じ、 呼び出し元が、必要な `Deconstruct` メソッドを簡単には呼び出せなくなる場合があります。

この例では、出力パラメーターが `Person` の `Deconstruct` メソッドには 2 つ、`Student` の `Deconstruct` メソッドには 3 つ含まれるため、呼び出しが不明確になる可能性は最小限に抑えられています。

## <a name="conclusion"></a>まとめ 

クラスや構造体では動作の定義が必要であるため、新しい言語とライブラリで名前付きタプルがサポートされたことで、動作を定義せずに複数のフィールドを格納するデータ構造設計が格段に扱いやすくなりました。 こうした型に対してタプルを使用するのは簡単です。 詳細な `class` または `struct` 構文を使用して型を作成しなくても、静的な型チェックのすべてのメリットを利用できます。 とは言っても、class や struct は、`private` や `internal` のユーティリティ メソッドにとっては非常に便利です。 複数のフィールドを含む値がパブリック メソッドによって返される場合は、ユーザー定義型、`class` または`struct` を作成してください。

