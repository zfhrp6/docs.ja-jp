---
title: "C# のクイック スタート - コレクションのガイド"
description: "このクイック スタートでは、そのリスト コレクションを表示することによって (C#) を説明します。"
keywords: "C# の場合、最初に、チュートリアル、コレクション、ボックスの一覧"
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 51b190fba32186cb4c52ccd773274d9ae22c8efb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="c-quick-start-collections"></a>C# の場合は、クイック スタート: コレクション #

このチュートリアルでは、c# 言語の基本的な概要については、<xref:System.Collections.Generic.List%601>クラスです。

## <a name="a-simple-list-example"></a>単純なリストの使用例です。

> [!NOTE]
> 記述したコードから開始する場合は[dot.net](https://dot.net/)、このセクションで記述されたコードがあります。 ジャンプ[一覧の内容を変更](#modify-list-contents)です。

このレッスンでは、オンラインのクイック スタートが終了したら、インストールされている前提としています、 [.NET Core SDK](http://dot.net/core)と[Visual Studio Code](https://code.visualstudio.com/)です。 

という名前のディレクトリを作成する**リスト クイック スタート**です。 いることを現在のディレクトリと実行`dotnet new console`です。

開いている**Program.cs**好みのエディターと置換、既存のコードを次に。

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

置き換える`<name>`名に置き換えています。 保存**Program.cs**です。 型`dotnet run`コンソール ウィンドウしてみてください。

だけ文字列のリストを作成、そのリストに 3 つの名前を追加してすべて大文字で名前を印刷します。 一覧をループする以前のクイック スタートで学習した概念を使用しています。

名前を表示するコードでは、使用**補間文字列**です。  前に指定するときに、`string`で、`$`文字、文字列の宣言での c# コードを埋め込むことができます。 実際の文字列を生成値に c# コードを置き換えます。 この例では置き換えられます、`{name.ToUpper()}`各名前を持つために、変換英大文字、呼び出したのと、<xref:System.String.ToUpper%2A>メソッドです。

みましょうの探索してください。
    
## <a name="modify-list-contents"></a>変更内容の一覧表示

使用して作成したコレクション、<xref:System.Collections.Generic.List%601>型です。 この型は、要素のシーケンスを格納します。 山かっこ間の要素の種類を指定するとします。
    
この 1 つの重要な側面<xref:System.Collections.Generic.List%601>型は、拡大または縮小、でく要素を追加または削除できるようにすることです。 終了する前にこのコードを追加`}`で、`Main`メソッド。

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

2 つ以上の名前は、リストの末尾に追加されました。 したも 1 つも削除します。 ファイル、および種類保存`dotnet run`してみてください。
    
<xref:System.Collections.Generic.List%601>個々 のアイテムを参照することができます**インデックス**もします。 間でインデックスを配置する`[`と`]`リスト名の後にトークンです。 C# の場合 0 を最初のインデックスを使用します。 追加したコードのすぐ下には、このコードを追加して、それを再試行してください。

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

リストの末尾を越えるインデックスにアクセスすることはできません。 インデックスは、有効なインデックスの最大値であるため、0 から始まりますリスト内の項目の数よりも小さいです。 一覧がどのくらいの期間を使用しているかをチェックすることができます、<xref:System.Collections.Generic.List%601.Count%2A>プロパティです。 Main メソッドの最後に、次のコードを追加します。

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

ファイル、および種類保存`dotnet run`結果を表示するには、もう一度です。    

## <a name="search-and-sort-lists"></a>検索および並べ替えリスト
サンプルは、比較的小さいリストを使用してですが、アプリケーションで、多くの詳細要素と、数千に達しますのリストを作成ことが多くの場合、可能性があります。 これらの大規模なコレクション内の要素を検索、さまざまなアイテムの一覧を検索する必要があります。 <xref:System.Collections.Generic.List%601.IndexOf%2A>メソッド アイテムを検索し、項目のインデックスを返します。 下に次のコードを追加、`Main`メソッド。

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
    
}
```

リスト内の項目も並べ替えられます。 <xref:System.Collections.Generic.List%601.Sort%2A>メソッド (文字列) の場合にアルファベット順に、通常の順序で一覧のすべての項目を並べ替えます。 下に次のコードを追加、`Main`メソッド。

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

ファイルの保存と型`dotnet run`を最新のバージョンを実行してください。

次のセクションを開始する前に別のメソッドに現在コードに移動してみましょう。 これにより新しい例の操作を開始します。 名前を変更、`Main`メソッドを`WorkingWithStrings`と新しい書き込み`Main`メソッドを呼び出す`WorkingWithStrings`です。 完了したら、コードは次のようになります。

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a>その他の種類の一覧

使用した、`string`これまでのリストを入力します。 こちらから、<xref:System.Collections.Generic.List%601>別の種類を使用します。 数値のセットを構築してみましょう。 

新しいの下部に次のコードを追加`Main`メソッド。

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

整数のリストを作成し、最初の 2 つの整数を値 1 に設定します。 これは、値は、最初の 2 つの*フィボナッチ シーケンス*一連の数値。 各次のフィボナッチ数は、前の 2 つの数値の合計を取得して検出されます。 このコードを追加します。

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

ファイルの保存と型`dotnet run`結果を確認します。 

> [!TIP]
> このセクションでを重点的にすることができますをコメント アウトを呼び出すコード`WorkingWithStrings();`です。 2 つの配置だけ`/`次のように、呼び出しの前に文字:`// WorkingWithStrings();`です。 

## <a name="challenge"></a>チャレンジ
一緒に配置できるかどうかを参照してください。 ここから、前のレッスンの一部のレッスンです。 新機能を作成したらこれまでフィボナッチの数列を展開します。 シーケンスの最初の 20 個の番号を生成するコードを記述してください。

## <a name="complete-challenge"></a>完全なチャレンジ

ソリューションの例を確認できます[GitHub の完成後のサンプル コードを見る](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs)

一覧にその値を追加、集計、および、ループの反復ごとの最後の 2 つの整数の一覧でに移動しています。 ループは、20 個のアイテムを一覧に追加するまで繰り返されます。

これで、一覧のチュートリアルを完了しました。

作業方法について学習することができます、`List`に入力、 [.NET ガイド](../../standard/index.md)に関するトピック[コレクション](../../standard/collections/index.md)です。 その他の多くのコレクション型についても学習します。
