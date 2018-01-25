---
title: "クイック スタート - 挿入文字列- C# ガイド"
description: "この挿入文字列に関するクイック スタートでは、C# コードを記述して、より大きな文字列に式の結果を含めます。"
author: rpetrusha
ms.author: ronpet
ms.date: 01/11/2018
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 14185dd4e364f12756541ac6401d1c6ff3206fe9
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2018
---
# <a name="interpolated-strings"></a>挿入文字列

このクイック スタートでは、C# で挿入文字列を使用して、単一の出力文字列に値を挿入する方法を説明します。 C# コードを記述し、コードをコンパイルおよび実行して結果を確認します。 クイック スタートには、値を文字列に挿入し、それらの値の書式をさまざまな方法で設定する、一連のレッスンが含まれています。

このクイック スタートでは、開発用に使用できるマシンがあることを想定しています。 Mac、PC、または Linux 上でローカルの開発環境を設定する手順については、.NET の [10 分でわかる概要](https://www.microsoft.com/net/core)に関するトピックに記載されています。 使用するコマンドの概要を手短に確認するには、[ローカルでのクイック スタートの概要](local-environment.md)と詳細へのリンクをご覧ください。 

## <a name="create-an-interpolated-string"></a>挿入文字列を作成する

**interpolated-quickstart** という名前のディレクトリを作成します。 それを現在のディレクトリにして、コンソール ウィンドウから次のコマンドを実行します。

```console
dotnet new console -n interpolated -o .
```

このコマンドによって、現在のディレクトリに新しい .NET Core コンソール アプリケーションが作成されます。

お好みのエディターで **Program.cs** を開き、`Console.WriteLine("Hello World!");` の行を次のコードで置き換えます。`<name>` は自分の名前に置き換えてください。

```csharp
var name = "<name>";
Console.WriteLine($"Hello, {name}. It's a pleasure to meet you!");
```
コンソール ウィンドウで「`dotnet run`」と入力し、このコードを試します。 プログラムを実行すると、あいさつ文に自分の名前を含む単一の文字列が表示されます。 <xref:System.Console.WriteLine%2A> メソッド呼び出しに含まれる文字列は、*挿入文字列*です。 これは、埋め込みコードを含む文字列から (*結果文字列*という) 単一の文字列を構築できる一種のテンプレートです。 挿入文字列は、文字列に値を挿入したり、文字列を (結合) 連結したりする場合に特に便利です。 
    
この簡単な例には、すべての挿入文字列に含める必要がある次の 2 つの要素が含まれています。 

- 始まりの引用符文字の前の `$` で始まる文字列リテラル。 `$` シンボルと引用符文字の間にスペースを挿入することはできません  (スペースが含まれている場合の動作を確認したい場合は、`$` 文字の後にスペースを挿入し、ファイルを保存してから、コンソール ウィンドウで「`dotnet run`」と入力してプログラムを再実行します。 C# コンパイラには、"エラー CS1056: 予期しない文字 '$' です" というエラー メッセージが表示されます)。 

- 1 つ以上の*挿入式*。 挿入式は、始めかっこと終わりかっこ (`{` と `}`) で示されます。 かっこ内に (`null` を含む) 値を返す C# 式を配置できます。 

その他のいくつかのデータ型を持つ挿入文字列の例をさらにいくつか試してみましょう。
    
## <a name="include-different-data-types"></a>さまざまなデータ型を含める

前のセクションでは、挿入文字列を使用して、1 つの文字列内に別の文字列を挿入しましたが、 挿入文字列式を任意のデータ型にすることもできます。 複数のデータ型の値を持つ挿入文字列を試してみましょう。 
    
次の例には、`Vegetable` オブジェクト、`Unit` 列挙型のメンバー、<xref:System.DateTime> 値、<xref:System.Decimal> 値を持つ挿入式が含まれています。 エディターのすべての C# コードを以下のコードに置き換えてから、`console run` コマンドを使用して実行します。

```csharp
using System;

public class Vegetable
{
   public Vegetable(string name) => Name = name;
   
   public string Name { get; }
   
   public override string ToString() => Name;
}

public class Example
{
   public enum Unit { item, pound, ounce, dozen };
   
   public static void Main()
   {
      var item = new Vegetable("eggplant");
      var date = DateTime.Now;
      var price = 1.99m;
      var unit = Unit.item;
      Console.WriteLine($"On {date}, the price of {item} was {price} per {unit}.");
   }
}
```
    
2 つ目の挿入式には、コンソールに表示される結果文字列の `item` オブジェクトが含まれており、この場合、"eggplant" という文字列が結果文字列に挿入されることに注意してください。 これは、挿入式の型が文字列でない場合、C# コンパイラでは次の処理が行われるためです。

- 挿入式が `null` の場合、挿入式は空の文字列 (""、または <xref:System.String.Empty?displayProperty=nameWithType>) を返します。

- 挿入式が `null` でない場合、挿入式の型の `ToString` メソッドが呼び出されます。 コメント シンボル (`//`) を前に配置して、例の `Vegetable.ToString` メソッドの定義をコメント アウトすることで、これをテストできます。 出力では、"eggplant" という文字列が "Vegetable" という型名に置き換えられます。これは、<xref:System.Object.ToString?displayProperty=nameWithType> メソッドの既定の動作です。   

この例の出力では、日付の精度が高すぎ (エッグプラントの価格が 2 つ目の値により変化しない)、価格の値は通貨の単位を示していません。 次のセクションでは、挿入式によって返される文字列の書式を制御することで、こうした問題を修正する方法について説明します。

## <a name="control-the-formatting-of-interpolated-expressions"></a>挿入式の書式設定を制御する

前のセクションでは、適切に書式設定されていない 2 つの文字列が結果文字列に挿入されました。 1 つは、日付のみが適切な日時の値でした。 もう 1 つは、通貨単位を示さない価格でした。 両方の問題には簡単に対処することができます。 挿入式に、特定の型の書式設定を制御する*書式指定文字列*を含めることができます。 前の例の `Console.WriteLine` 呼び出しを変更し、次の行に示すように、日付と価格のフィールドの書式指定子を含めます。

```csharp
Console.WriteLine($"On {date:d}, the price of {item} was {price:C2} per {unit}.");
```
    
コロンと書式指定文字列を持つ挿入式に従って、書式指定文字列を指定します。 "d" は、短い日付形式を表す[標準の日時書式設定文字列](../../standard/base-types/standard-date-and-time-format-strings.md#the-short-date-d-format-specifier)です。 "C2" は、小数点以下が 2 桁の通貨値として数値を表す[標準の数値書式指定文字列](../../standard/base-types/standard-numeric-format-strings.md#the-currency-c-format-specifier)です。

.NET Standard ライブラリの多くの型で、定義済みの書式指定文字列セットがサポートされています。 これらには、数値型と日時型がすべて含まれます。 書式指定文字列をサポートする型の完全なリストについては、「[.Net 型の書式設定](../../standard/base-types/formatting-types.md)」記事の「[.NET クラス ライブラリの型および書式指定文字列](../../standard/base-types/formatting-types.md#stringRef)」を参照してください。 どの型でも書式指定文字列セットをサポートすることができ、既存の型のカスタム書式指定を提供するカスタム書式指定拡張機能を開発することもできます。 <xref:System.ICustomFormatter> 実装を提供することによるカスタム書式指定については、「[.Net 型の書式設定](../../standard/base-types/formatting-types.md)」記事の「[ICustomFormatter を使用したカスタム書式設定](../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter)」を参照してください。

テキスト エディターで書式指定文字列を変更してみて、変更するたびにプログラムを再実行し、変更が日時と数値の書式設定にどのように影響するかを確認します。 `{date:d}` の "d" を "t" (短い時刻形式を表示する)、"y" (年と月を表示する)、"yyyy" (4 桁の数字として年を表示する) に変更します。 `{price:C2}` "C2" を "e" (指数表記の場合) と "F3" (小数点以下が 3 桁の数値の場合) に変更します。

書式設定を制御するだけでなく、挿入式によって返される文字列のフィールドの幅と配置を制御することもできます。 次のセクションでは、この方法を説明します。

## <a name="control-the-field-width-and-alignment-of-interpolated-expressions"></a>挿入式のフィールドの幅と配置を制御する

通常、挿入式によって返される文字列が結果文字列に含まれている場合、先頭スペースも末尾スペースもありません。 特にデータ セットを処理する場合、挿入式ではフィールドの幅とその配置を指定することができます。 そのためには、テキスト エディターのすべてのコードを次のコードに置き換えてから、「`console run`」と入力してプログラムを実行します。
    
```csharp
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var titles = new Dictionary<string, string>();
      titles.Add("Doyle, Arthur Conan", "Hound of the Baskervilles, The");
      titles.Add("London, Jack", "Call of the Wild, The");
      titles.Add("Shakespeare, William", "Tempest, The");

      Console.WriteLine("Author and Title List");
      Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
      foreach (var title in titles)
         Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
   }
}
```
    
作成者の名前は左揃えになり、書き込まれたタイトルは右揃えになります。 式の後にコンマ (",") を追加し、フィールドの幅を指定して、配置を指定します。 次のようにフィールドの幅が正数の場合、フィールドは右揃えになります。

```text
{expression, width}
```

次のようにフィールドの幅が負数の場合、フィールドは左揃えになります。

```text
{expression, -width}
```

`{"Author",-25}` と `{title.Key,-25}` の挿入式から負号を削除してみて、次のコードのように、例を再実行します。

```csharp
Console.WriteLine($"\n{"Author",-25}    {"Title",30}\n");
foreach (var title in titles)
   Console.WriteLine($"{title.Key,-25}     {title.Value,30}");
```

この場合、作成者情報は右揃えになります。

フィールドの幅と書式指定文字列を組み合わせて単一の挿入式にまとめることができます。 最初にフィールドの幅が配置され、その後にコロンと書式指定文字列が続きます。 `Main` メソッド内のすべてのコードを次のコードに置き換えると、フィールド幅が定義された 3 つの書式指定された文字列が表示されます。 次に、`dotnet run` コマンドを入力してプログラムを実行します。

```csharp
Console.WriteLine($"{DateTime.Now,-20:d} Hour {DateTime.Now,-10:HH} {1063.342,15:N2} feet");
```
出力は次のようになります。

```console
1/11/2018            Hour 09                1,063.34 feet
```

挿入文字列のクイック スタートはこれで終了です。 
    
続けて独自の開発環境で[配列とコレクション](arrays-and-collections.md)のクイック スタートに進むことができます。

挿入文字列の機能の詳細については、C# リファレンスの[挿入文字列](../language-reference/keywords/interpolated-strings.md)に関するトピックで学習できます。

