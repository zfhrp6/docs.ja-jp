---
title: "C# のクイック スタート - 数字 (C#) のガイド"
description: "数値型、そのプロパティおよびメソッドを表示することによって (C#) を説明します。"
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 821cca4ea6d6148410e9b179f05d5b74c4844628
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="numbers-in-c-quick-start"></a>C# のクイック スタートの番号 #

このクイック スタートには、対話的に c# での数値の型について説明します。 少量のコードを記述し、コンパイルして、そのコードを実行します。 クイック スタートには、一連数字と c# での算術演算を探索するレッスンにはが含まれています。 これらのレッスンでは、C# 言語の基本を説明します。

このクイック スタートを使用する開発に使用することができます、マシンが必要です。 .NET トピック[10 分後に開始](https://www.microsoft.com/net/core)Mac や PC、Linux 上のローカル開発環境を設定する方法についてはします。

## <a name="explore-integer-math"></a>整数の演算の確認

という名前のディレクトリを作成する**番号クイック スタート**です。 それを現在のディレクトリとし、`dotnet new console -n NumbersInCSharp -o .` を実行します。

開いている**Program.cs**好みのエディター、および置換行で`Console.Writeline("Hello World!");`次。

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

このコードを入力して実行`dotnet run`コマンド ウィンドウでします。 

整数を使用した基本的な算術演算の 1 つを確認しました。 `int` 型は、**整数**を表します (正の整数、または負の整数)。 加算には `+` 記号を使用します。 他の一般的な整数の算術演算には次のものがあります。

- `-`: 減算
- `*`: 乗算
- `/`: 除算

まずは、上記の各種演算を実行してみます。 後の行の値を書き込みますでこれらの行を追加`c`:

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

このコードを入力して実行`dotnet run`コマンド ウィンドウでします。 
    
好みで、同じ行で複数の算術演算を実行することもできます。 再試行`c = a + b - 12 * 17;`例を示します。 変数と定数の数字の混合を許可するとします。

> [!TIP]
> C# (または何らかのプログラミング言語) について詳しく学習するに従い、コードを記述する際にミスをすることもあるでしょう。 **コンパイラ**は、そうしたエラーを発見して報告します。 出力には、エラー メッセージが含まれていると見ると密接にコード例を修正するかを確認、ウィンドウ内のコード。
> こうした実習が C# コードの構造を理解するのに役立ちます。     

最初の手順を完了しました。 次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。 移動しておくと、新しい例で作業を開始するときに楽になります。 `Main` メソッドの名前を `WorkingWithIntegers` に変更し、`WorkingWithIntegers` を呼び出す新しい `Main` メソッドを記述します。 完成したコードは次のようになります。

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a>演算の順序の確認

呼び出しをコメント`WorkingWithIntegers()`です。 このセクションで作業するとわかりやすい出力にするには。

```csharp
//WorkingWithIntegers();
```

`//`開始、**コメント**(C#)。 コメントは、ソース コードで保持しますが、コードとして実行する任意のテキストです。 コンパイラは、コメントから実行可能コードを生成しません。

C# 言語は、数学で学んだ規則と同じ規則で各演算の優先順位を定義します。
乗算と除算は、加算と減算よりも優先されます。
次のコードを追加することで調査を`Main`メソッド、および execuing `dotnet run`:

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

出力を見ると、加算の前に乗算が実行されていることがわかります。

操作の別の順序を強制するには、操作を囲むかっこを追加することで、または対象の操作が最初に実行します。 次の行を追加し、もう一度実行します。

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

さまざまな演算を多数組み合わせて、他にも試してみましょう。 下部にある次の行を追加、`Main`メソッドです。 再試行`dotnet run`もう一度です。

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

整数について面白い動作をしていることに気づいたでしょうか。 常に整数の除算は、10 進数または分数部分を含めるように結果が期待する場合でも、結果の整数値を生成します。

この動作を目にしていない場合は、末尾に次のコードを実行してください、`Main`メソッド。

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

型`dotnet run`結果を表示するには、もう一度です。

続行する前に、このセクションで記述し、新しいメソッドに配置したすべてのコードを見てみましょう。 新しいメソッドを呼び出す`OrderPrecedence`です。
次のよう終了する必要があります。

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {   
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a>整数の有効桁数と制限の確認
この最後のサンプルでは、整数の除算における結果の切り捨てについて確認します。
取得することができます、**残りの部分**を使用して、**剰余**、演算子、`%`文字です。 次のコードを実行してください、`Main`メソッド。

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

C# の整数型は算術における整数ともう 1 つ異なる点があります。それは `int` 型には最小値と最大値の制限があるということです。 このコードを追加、`Main`メソッドをこれらの制限を参照してください。
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

計算によってこれらの制限を超える値が作られると、**アンダーフロー**または**オーバーフロー**の状態になります。 計算の結果が 1 つの制限からもう 1 つの制限に折り返されているように見えます。 これら 2 つの行を追加、`Main`例を参照するメソッド。

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
計算の結果が最小値の (負の) 整数に極めて近いことに注目してください。 これは `min + 2` と同じです。 加算演算が許容された整数値を**オーバーフロー**しました。
整数がオーバーフローして最大値から最小値に ”折り返され” たため、計算結果が非常に大きな負の値になっています。

他にもさまざまな制限や有効桁数を持つ数値型があり、`int` 型がご自分のニーズと合わない場合は、そちらも使用できます。 次はその別の数値型を見ていきます。

繰り返しますが、このセクションの内容を別のメソッドに記述したコードに移動してみましょう。 これに `TestLimits` という名前を付けます。 

## <a name="work-with-the-double-type"></a>double 型の処理

`double` 数値型は、倍精度浮動小数点数を表します。 こうした用語を初めて見た人もいるかもしれません。 A**浮動小数点**数が非常に大規模なまたは大きさに小規模にすることがあります整数以外の数値を表すに便利です。 **倍精度**は、そうした数値が**単精度**よりも大きな有効桁数を使用して格納されることを意味しています。 最近のコンピューターでは、単精度よりも倍精度の数値を使用する方が一般的です。
確認してみましょう。 次のコードを追加し、結果を確認します。

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

計算結果に商の小数部分が含まれていることに注目してください。 double 型を使用して、もう少し複雑な式を試します。

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

double 値は整数値よりも範囲が大きくなります。 これまで入力した、次のコードを試してください。

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

これらの値は、科学的表記法で出力されます。 左側には、番号、`E`の有効桁がします。 右側の数値は指数であり、10 の累乗です。 

算術における 10 進数と同じように、C# における double には丸め誤差が発生することがあります。 次のコードを試してみましょう。

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

`0.3` の循環小数は `1/3` と完全に同じではありません。

***課題***

`double` 型を使用して、大きい値や小さい値、乗算、除算などの計算してみましょう。  もっと複雑な計算を試してみてください。

チャレンジ時間を費やしている後は、コードを作成し、新しいメソッドに配置を実行します。 その新しいメソッドの名前を付けます`WorkWithDoubles`です。

## <a name="work-with-fixed-point-types"></a>固定小数点型の処理

C# の基本的な数値型である整数と double について見てきました。  もう 1 つ知っておくべき型として、`decimal` 型があります。 `decimal`型がより大きい有効桁数が、範囲を小さく`double`です。 **固定小数点**という用語は、小数点 (またはバイナリの小数点) が動かないことを意味しています。 では、始めましょう。

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

`double` 型よりも範囲が小さいことに注目してください。 次のコードを実行すると、decimal 型では有効桁数がより大きいことを確認できます。

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

数値の末尾の `M` は、定数では `decimal` 型を使用する必要があることを示しています。

decimal 型を使用した演算では、小数点の右側の桁数がより多いことに注目してください。 

***課題***

さまざまな数値型を確認したので、次は半径が 2.50 インチの円の面積を計算するコードを記述してみます。 円の面積は、半径の 2 乗 x 円周率です。 1 つのヒント: c# PI の定数が含まれる<xref:System.Math.PI?displayProperty=nameWithType>の値に対して使用することができます。 

によって、応答をチェックする[GitHub の完成後のサンプル コードを見る](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)

希望の場合は、その他のいくつかの数式を再試行してください。 

"番号で c#"クイック スタートが完了しました。 続行できますが、[分岐とループ](branches-and-loops-local.md)独自開発環境でのクイック スタート。

C# の数値の詳細については、次のトピックで学習できます。

[整数型の一覧表](../language-reference/keywords/integral-types-table.md)   
[浮動小数点型の一覧表](../language-reference/keywords/floating-point-types-table.md)   
[組み込み型の一覧表](../language-reference/keywords/built-in-types-table.md)   
[暗黙的な数値変換の一覧表](../language-reference/keywords/implicit-numeric-conversions-table.md)   
[明示的な数値変換の一覧表](../language-reference/keywords/explicit-numeric-conversions-table.md)

