---
title: "クイック スタート - 分岐および lops - c# ガイド"
description: "分岐とループに関するこのクイック スタートでは、条件分岐とループ ステートメントを繰り返し実行をサポートする言語の構文を探索する c# コードを記述します。"
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4b077a29cf42072a93b054f50a13a4580ad54304
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="branches-and-loops"></a>分岐とループ

このクイック スタートでは、変数を検査し、それらの変数に基づいて実行パスを変更するコードを記述する方法を説明します。 C# コードを記述し、コンパイルと実行の結果を表示します。 クイック スタートには、一連分岐構造やループ構造 (C#) を探索するレッスンにはが含まれています。 これらのレッスンでは、C# 言語の基本を説明します。

このクイック スタートを使用する開発に使用することができます、マシンが必要です。 .NET トピック[10 分後に開始](https://www.microsoft.com/net/core)Mac や PC、Linux 上のローカル開発環境を設定する方法についてはします。

## <a name="make-decisions-using-the-if-statement"></a>使用して決定、`if`ステートメント

という名前のディレクトリを作成する**分岐クイック スタート**です。 それを現在のディレクトリとし、`dotnet new console -n BranchesAndLoops -o .` を実行します。 このコマンドは、現在のディレクトリに新しい .NET Core コンソール アプリケーションを作成します。 

開いている**Program.cs**好みのエディター、および置換行`Console.Writeline("Hello World!");`を次のコード。

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

このコードを入力して実行`dotnet run`で、コンソール ウィンドウは、です。 メッセージが表示する必要があります「回答は、10 を超えています」。 コンソールに出力されます。

合計が 10 未満になるように `b` の宣言を変更します。 

```csharp
int b = 3;
```

型`dotnet run`もう一度です。 計算結果が 10 未満であるため、何も出力されません。 判定中の**条件**が false になっています。 `if` ステートメントの考えられる分岐の 1 つである true 分岐のみを記述したため、実行すべきコードがありません。

> [!TIP]
> C# (または何らかのプログラミング言語) について詳しく学習するに従い、コードを記述する際にミスをすることもあるでしょう。 コンパイラを検索し、エラーをレポートします。 よく見ると、エラー出力とエラーを生成したコード。 Compler エラー通常役立つ問題を特定します。 

この最初の例は、の機能を示しています`if`およびブール型です。 A*ブール*変数 2 つの値のいずれかです:`true`または`false`です。 C# の場合、特殊な種類の定義`bool`ブール値変数。 `if` ステートメントは、`bool` の値を確認します。 値が `true` の場合、`if` に続くステートメントを実行します。 それ以外の場合はスキップします。 

条件を確認してその条件に基づいてステートメントを実行するというこのプロセスは非常に機能的です。


## <a name="make-if-and-else-work-together"></a>if と else を組み合わせた使用

true 分岐と false 分岐で別々のコードを実行するには、条件が false のときに実行する `else` 分岐を作成します。 これを再試行してください。 次のコードの最後の 2 つの行を追加、`Main`メソッド (既に最初の 4 つ)。

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

`else` キーワードに続くステートメントは、判定中の条件が `false` のときにのみ実行されます。 結合`if`と`else`条件が両方を処理する必要があります。 すべての電力を供給とブール値、`true`と`false`条件。

> [!IMPORTANT]
> `if` と `else` のステートメント内にあるインデントは、人が読みやすいようにするためのものです。
> C# 言語はインデントや空白文字を重要なものとして扱いません。 `if` や `else` のキーワードに続くステートメントは、条件に基づいて実行されます。 このクイック スタートのすべてのサンプルでは、ステートメントの制御フローに基づく行をインデントする一般的な方法に従います。

インデントは重要ではないため、条件に基づいて実行するブロック内に 1 つ以上のステートメントがある場合には、`{` と `}` を使用して示します。 通常、C# プログラマーは `if` と `else` の句にはこの中かっこを使用します。 次の例では、作成したものと同じです。 次のコードに一致するコードを変更します。

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> このクイック スタートの残りの部分からすべてのコード サンプルは、後に、中かっこを含めるプラクティスを受け入れられます。

複雑な条件をテストすることができます。 次のコードを追加、`Main`これまでに作成したコードの後にメソッド。

```csharp
    int c = 4;
    if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

`&&` は "and" (および) を表します。 これは、true 分岐でステートメントを実行するには、両方の条件が true になる必要があることを意味しています。  また、これらの例では、ステートメントが `{` と `}` で囲まれていれば、各条件分岐に複数のステートメントを持つことができることを示しています。

使用することも`||`を表す「または」です。 これまで入力した後、次のコードを追加します。

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

最初の手順を完了しました。 次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。 移動しておくと、新しい例で作業を開始するときに楽になります。 `Main` メソッドの名前を `ExploreIf` に変更し、`ExploreIf` を呼び出す新しい `Main` メソッドを記述します。 完成したコードは次のようになります。

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }            
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

呼び出しをコメント`ExploreIf()`です。 このセクションで作業するとわかりやすい出力にするには。

```csharp
//ExploreIf();
```

`//`開始、**コメント**(C#)。 コメントは、ソース コードで保持しますが、コードとして実行する任意のテキストです。 コンパイラは、コメントから実行可能コードを生成しません。

## <a name="use-loops-to-repeat-operations"></a>ループを使用した処理の繰り返し

このセクションでは使用して**ループ**ステートメントを繰り返す。 このコードを実行してください、`Main`メソッド。

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

`while`ステートメントは、条件をチェックして、ステートメントまたはステートメント ブロックが次の実行、`while`です。 条件で、これらのステートメントを実行する条件が false になるまで繰り返しチェックします。

この例では、もう 1 つ新しい演算子が使用されています。 `counter` 変数のあとにある `++` は、**インクリメント**演算子です。 値に 1 を加算`counter`内でその値を格納し、`counter`変数。

> [!IMPORTANT]
> 確認して、`while`コードを実行するように条件が false に変化をループします。 それ以外の場合は、プログラムが終了することのない**無限ループ**を作成します。 使用しない場合は、プログラムを強制する必要がないこのサンプルで示すは**ctrl キーを押しながら C**またはその他の手段です。

`while` ループは、条件を判定してから `while` に続くコードを実行します。 `do` ... `while` ループは、最初にコードを実行してからその条件を確認します。 ループは、次のコードに表示されるときに:

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

これは、`do`ループと以前`while`ループが同じ出力を生成します。

## <a name="work-with-the-for-loop"></a>for ループの処理

**の**ループは c# でよく使用します。 Main() メソッドでは、このコードを試してください。

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

このループは、既に使用した `while` ループや `do` ループと同じ機能を持っています。 `for` ステートメントは 3 つの部分に分かれてその機能を制御します。 

最初の部分は、**for 初期化子**です。`for index = 0;` は、`index` がループ変数であることを宣言し、その初期値を `0` に設定しています。

2 つ目の部分は、**for 条件**です。`index < 10` は、counter の値が 10 未満である間は `for` ループが実行され続けることを宣言しています。

最後の部分は、**for 反復子**です。`index++` は、`for` ステートメントに続くブロックを実行したあとにループ変数を変更する方法を指定しています。 ここでは、ブロックが実行されるごとに `index` が 1 ずつ増加するよう指定しています。

ご自身でこれを実行してみてください。 以下をそれぞれ試してみます。

- 初期化子を変更して別の値で開始する。
- 条件を変更して別の値で停止する。

完了したら次に進み、学習したことを使用して自分でいくつかのコードを記述してみましょう。

## <a name="combine-branches-and-loops"></a>分岐とループを結合します。

C# 言語における `if` ステートメントとループ構造を見てきました。では、1 から 20 の整数のうち 3 で割り切れる数の合計を求める C# コードを記述できるか確認してみましょう。  次にいくつかヒントを示します。

- `%` 演算子は、除算演算の剰余を算出します。
- `if`ステートメントを使用する条件が、数が合計の一部にする必要があるかどうかを参照してください。
- `for` ループは、1 から 20 までのすべての数を 1 つずつ確認する一連の手順を繰り返すのに役立ちます。

ご自身で試してみてください。 そして自分がとった方法を確認してください。 考えられる 1 つの解答を確認できます[GitHub の完成したコードを表示する](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54)です。

「ループおよび分岐」のクイック スタートが完了しました。

続行できますが、[配列およびコレクション](arrays-and-collections.md)独自開発環境でのクイック スタート。

次のトピックでこれらの概念の詳細を学習できます。

[if と else ステートメント](../language-reference/keywords/if-else.md)   
[while ステートメント](../language-reference/keywords/while.md)   
[do ステートメント](../language-reference/keywords/do.md)   
[for ステートメント](../language-reference/keywords/for.md)   
