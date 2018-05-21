---
title: C# における数値のチュートリアル - C# ローカル クイックスタート
description: 数値型とそのプロパティ、およびメソッドを詳しく見ていくことで C# について学習します。
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: cf8f00193b4fa66ff444fe8e40942c39e99d10b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="numbers-in-c-quickstart"></a><span data-ttu-id="de735-103">C# における数値クイックスタート</span><span class="sxs-lookup"><span data-stu-id="de735-103">Numbers in C# quickstart</span></span>

<span data-ttu-id="de735-104">このクイックスタートでは、対話形式で C# の数値型について説明します。</span><span class="sxs-lookup"><span data-stu-id="de735-104">This quickstart teaches you about the number types in C# interactively.</span></span> <span data-ttu-id="de735-105">少量のコードを記述したら、そのコードをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="de735-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="de735-106">このクイックスタートには、C# の数値と算術演算に関する一連のレッスンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="de735-106">The quickstart contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="de735-107">これらのレッスンでは、C# 言語の基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="de735-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="de735-108">このクイックスタートでは、開発用に使用できるマシンがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="de735-108">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="de735-109">Mac、PC、または Linux 上でローカルの開発環境を設定する手順については、.NET の [10 分でわかる概要](https://www.microsoft.com/net/core)に関するトピックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="de735-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="de735-110">使用するコマンドの概要を手短に確認するには、[ローカルでのクイックスタートの概要](local-environment.md)と詳細へのリンクをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="de735-110">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="de735-111">整数の演算の確認</span><span class="sxs-lookup"><span data-stu-id="de735-111">Explore integer math</span></span>

<span data-ttu-id="de735-112">「**numbers-quickstart**」という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="de735-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="de735-113">それを現在のディレクトリとし、`dotnet new console -n NumbersInCSharp -o .` を実行します。</span><span class="sxs-lookup"><span data-stu-id="de735-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="de735-114">好みのエディターで **Program.cs** を開き、`Console.Writeline("Hello World!");` の行を次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="de735-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="de735-115">コマンド ウィンドウで「`dotnet run`」を入力し、このコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="de735-115">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="de735-116">整数を使用した基本的な算術演算の 1 つを確認しました。</span><span class="sxs-lookup"><span data-stu-id="de735-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="de735-117">`int` 型は、**整数**を表します (正の整数、または負の整数)。</span><span class="sxs-lookup"><span data-stu-id="de735-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="de735-118">加算には `+` 記号を使用します。</span><span class="sxs-lookup"><span data-stu-id="de735-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="de735-119">他の一般的な整数の算術演算には次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="de735-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="de735-120">`-`: 減算</span><span class="sxs-lookup"><span data-stu-id="de735-120">`-` for subtraction</span></span>
- <span data-ttu-id="de735-121">`*`: 乗算</span><span class="sxs-lookup"><span data-stu-id="de735-121">`*` for multiplication</span></span>
- <span data-ttu-id="de735-122">`/`: 除算</span><span class="sxs-lookup"><span data-stu-id="de735-122">`/` for division</span></span>

<span data-ttu-id="de735-123">まずは、上記の各種演算を実行してみます。</span><span class="sxs-lookup"><span data-stu-id="de735-123">Start by exploring those different operations.</span></span> <span data-ttu-id="de735-124">`c` の値を記述した行の後に、次の数行を追加します。</span><span class="sxs-lookup"><span data-stu-id="de735-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="de735-125">コマンド ウィンドウで「`dotnet run`」を入力し、このコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="de735-125">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="de735-126">好みで、同じ行で複数の算術演算を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="de735-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="de735-127">例として `c = a + b - 12 * 17;` を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="de735-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="de735-128">変数と定数を混在させることができます。</span><span class="sxs-lookup"><span data-stu-id="de735-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="de735-129">C# (または何らかのプログラミング言語) について詳しく学習するに従い、コードを記述する際にミスをすることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="de735-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="de735-130">**コンパイラ**は、そうしたエラーを発見して報告します。</span><span class="sxs-lookup"><span data-stu-id="de735-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="de735-131">エラー メッセージが出力された場合は、例のコードをよく確認して、ウィンドウで修正すべきコードを見つけます。</span><span class="sxs-lookup"><span data-stu-id="de735-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="de735-132">こうした実習が C# コードの構造を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="de735-132">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="de735-133">最初の手順が完了しました。</span><span class="sxs-lookup"><span data-stu-id="de735-133">You've finished the first step.</span></span> <span data-ttu-id="de735-134">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="de735-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="de735-135">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="de735-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="de735-136">`Main` メソッドの名前を `WorkingWithIntegers` に変更し、`WorkingWithIntegers` を呼び出す新しい `Main` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="de735-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="de735-137">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="de735-137">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="de735-138">演算の順序の確認</span><span class="sxs-lookup"><span data-stu-id="de735-138">Explore order of operations</span></span>

<span data-ttu-id="de735-139">`WorkingWithIntegers()` の呼び出しをコメント アウトします。</span><span class="sxs-lookup"><span data-stu-id="de735-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="de735-140">こうしておくと、このセクションの作業を進めるにあたって出力がすっきりします。</span><span class="sxs-lookup"><span data-stu-id="de735-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="de735-141">C# では、`//` の後ろが**コメント**になります。</span><span class="sxs-lookup"><span data-stu-id="de735-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="de735-142">コードとしては実行せずにソース コード内に残したい任意のテキストを、コメントにすることができます。</span><span class="sxs-lookup"><span data-stu-id="de735-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="de735-143">コンパイラは、コメントから実行可能コードを生成しません。</span><span class="sxs-lookup"><span data-stu-id="de735-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="de735-144">C# 言語は、数学で学んだ規則と同じ規則で各演算の優先順位を定義します。</span><span class="sxs-lookup"><span data-stu-id="de735-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="de735-145">乗算と除算は、加算と減算よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="de735-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="de735-146">`Main` メソッドに次のコードを追加し、`dotnet run` を実行して詳しく見てみます。</span><span class="sxs-lookup"><span data-stu-id="de735-146">Explore that by adding the following code to your `Main` method, and execuing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="de735-147">出力を見ると、加算の前に乗算が実行されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="de735-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="de735-148">最初に実行したい演算を囲むように丸かっこを追加することで、演算の順序を変えることができます。</span><span class="sxs-lookup"><span data-stu-id="de735-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="de735-149">次の行を追加して、もう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="de735-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="de735-150">さまざまな演算を多数組み合わせて、他にも試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="de735-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="de735-151">`Main` メソッドの下部に、次のような行を追加します。</span><span class="sxs-lookup"><span data-stu-id="de735-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="de735-152">もう一度 `dotnet run` を実行してください。</span><span class="sxs-lookup"><span data-stu-id="de735-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="de735-153">整数について面白い動作をしていることに気づいたでしょうか。</span><span class="sxs-lookup"><span data-stu-id="de735-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="de735-154">結果に小数点や小数部分が含まれると予想される場合でも、整数の除算は常に整数の結果を算出します。</span><span class="sxs-lookup"><span data-stu-id="de735-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="de735-155">この動作を確認できない場合は、`Main` メソッドの最後で次のコードを試してください。</span><span class="sxs-lookup"><span data-stu-id="de735-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="de735-156">もう一度 `dotnet run` を入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="de735-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="de735-157">続行する前に、このセクションで記述したコードをすべて新しいメソッドに移します。</span><span class="sxs-lookup"><span data-stu-id="de735-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="de735-158">新しいメソッドを `OrderPrecedence` とします。</span><span class="sxs-lookup"><span data-stu-id="de735-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="de735-159">コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="de735-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="de735-160">整数の有効桁数と制限の確認</span><span class="sxs-lookup"><span data-stu-id="de735-160">Explore integer precision and limits</span></span>
<span data-ttu-id="de735-161">この最後のサンプルでは、整数の除算における結果の切り捨てについて確認します。</span><span class="sxs-lookup"><span data-stu-id="de735-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="de735-162">**modulo** 演算子 (`%` 文字) を使用して、**剰余**を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="de735-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="de735-163">`Main` メソッドで次のコードを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="de735-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="de735-164">C# の整数型は算術における整数ともう 1 つ異なる点があります。それは `int` 型には最小値と最大値の制限があるということです。</span><span class="sxs-lookup"><span data-stu-id="de735-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="de735-165">`Main` メソッドに次のコードを追加して、この制限を確認します。</span><span class="sxs-lookup"><span data-stu-id="de735-165">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="de735-166">計算によってこれらの制限を超える値が作られると、**アンダーフロー**または**オーバーフロー**の状態になります。</span><span class="sxs-lookup"><span data-stu-id="de735-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="de735-167">計算の結果が 1 つの制限からもう 1 つの制限に折り返されているように見えます。</span><span class="sxs-lookup"><span data-stu-id="de735-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="de735-168">`Main` メソッドに次の 2 行を追加して、例を確認します。</span><span class="sxs-lookup"><span data-stu-id="de735-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="de735-169">計算の結果が最小値の (負の) 整数に極めて近いことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="de735-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="de735-170">これは `min + 2` と同じです。</span><span class="sxs-lookup"><span data-stu-id="de735-170">It's the same as `min + 2`.</span></span> <span data-ttu-id="de735-171">加算演算が許容された整数値を**オーバーフロー**しました。</span><span class="sxs-lookup"><span data-stu-id="de735-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="de735-172">整数がオーバーフローして最大値から最小値に ”折り返され” たため、計算結果が非常に大きな負の値になっています。</span><span class="sxs-lookup"><span data-stu-id="de735-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="de735-173">他にもさまざまな制限や有効桁数を持つ数値型があり、`int` 型がご自分のニーズと合わない場合は、そちらも使用できます。</span><span class="sxs-lookup"><span data-stu-id="de735-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="de735-174">次はその別の数値型を見ていきます。</span><span class="sxs-lookup"><span data-stu-id="de735-174">Let's explore those next.</span></span>

<span data-ttu-id="de735-175">もう一度、このセクションで記述したコードを別のメソッドに移します。</span><span class="sxs-lookup"><span data-stu-id="de735-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="de735-176">これに `TestLimits` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="de735-176">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="de735-177">double 型の処理</span><span class="sxs-lookup"><span data-stu-id="de735-177">Work with the double type</span></span>

<span data-ttu-id="de735-178">`double` 数値型は、倍精度浮動小数点数を表します。</span><span class="sxs-lookup"><span data-stu-id="de735-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="de735-179">こうした用語を初めて見た人もいるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="de735-179">Those terms may be new to you.</span></span> <span data-ttu-id="de735-180">**浮動小数点**数は、非常に大きな、または非常に小さな、整数ではない数値を表すのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="de735-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="de735-181">**倍精度**は、そうした数値が**単精度**よりも大きな有効桁数を使用して格納されることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="de735-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="de735-182">最近のコンピューターでは、単精度よりも倍精度の数値を使用する方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="de735-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="de735-183">確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="de735-183">Let's explore.</span></span> <span data-ttu-id="de735-184">次のコードを追加して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="de735-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="de735-185">計算結果に商の小数部分が含まれていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="de735-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="de735-186">double 型を使用して、もう少し複雑な式を試します。</span><span class="sxs-lookup"><span data-stu-id="de735-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="de735-187">double 値は整数値よりも範囲が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="de735-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="de735-188">これまでに記述したコードの下で、次のコードを試します。</span><span class="sxs-lookup"><span data-stu-id="de735-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="de735-189">これらの値は指数表記で出力されます。</span><span class="sxs-lookup"><span data-stu-id="de735-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="de735-190">`E` の左側は有効数字です。</span><span class="sxs-lookup"><span data-stu-id="de735-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="de735-191">右側の数値は指数であり、10 の累乗です。</span><span class="sxs-lookup"><span data-stu-id="de735-191">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="de735-192">算術における 10 進数と同じように、C# における double には丸め誤差が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="de735-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="de735-193">次のコードを試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="de735-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="de735-194">`0.3` の循環小数は `1/3` と完全に同じではありません。</span><span class="sxs-lookup"><span data-stu-id="de735-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="de735-195">***課題***</span><span class="sxs-lookup"><span data-stu-id="de735-195">***Challenge***</span></span>

<span data-ttu-id="de735-196">`double` 型を使用して、大きい値や小さい値、乗算、除算などの計算してみましょう。</span><span class="sxs-lookup"><span data-stu-id="de735-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="de735-197">もっと複雑な計算を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="de735-197">Try more complicated calculations.</span></span>

<span data-ttu-id="de735-198">しばらく試してみたあとは、これまでに記述したコードを新しいメソッドに移します。</span><span class="sxs-lookup"><span data-stu-id="de735-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="de735-199">新しいメソッドに `WorkWithDoubles` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="de735-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="de735-200">固定小数点型の処理</span><span class="sxs-lookup"><span data-stu-id="de735-200">Work with fixed point types</span></span>

<span data-ttu-id="de735-201">C# の基本的な数値型である整数と double について見てきました。</span><span class="sxs-lookup"><span data-stu-id="de735-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="de735-202">もう 1 つ知っておくべき型として、`decimal` 型があります。</span><span class="sxs-lookup"><span data-stu-id="de735-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="de735-203">`decimal` 型は、`double` 型よりも範囲は小さいですが、有効桁数が大きい型です。</span><span class="sxs-lookup"><span data-stu-id="de735-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="de735-204">**固定小数点**という用語は、小数点 (またはバイナリの小数点) が動かないことを意味しています。</span><span class="sxs-lookup"><span data-stu-id="de735-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="de735-205">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="de735-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="de735-206">`double` 型よりも範囲が小さいことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="de735-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="de735-207">次のコードを実行すると、decimal 型では有効桁数がより大きいことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="de735-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="de735-208">数値の末尾の `M` は、定数では `decimal` 型を使用する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="de735-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="de735-209">decimal 型を使用した演算では、小数点の右側の桁数がより多いことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="de735-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="de735-210">***課題***</span><span class="sxs-lookup"><span data-stu-id="de735-210">***Challenge***</span></span>

<span data-ttu-id="de735-211">さまざまな数値型を確認したので、次は半径が 2.50 センチメートルの円の面積を計算するコードを記述してみます。</span><span class="sxs-lookup"><span data-stu-id="de735-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="de735-212">円の面積は、半径の 2 乗 x 円周率です。</span><span class="sxs-lookup"><span data-stu-id="de735-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="de735-213">ヒント: .NET には <xref:System.Math.PI?displayProperty=nameWithType> という円周率の定数があり、その値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="de735-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="de735-214">答えは 19 と 20 の間になるはずです。</span><span class="sxs-lookup"><span data-stu-id="de735-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="de735-215">[GitHub にある完成版のサンプル コード](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)で答えを確認できます。</span><span class="sxs-lookup"><span data-stu-id="de735-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="de735-216">お好みで他の数式を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="de735-216">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="de735-217">これで "C# の数値" に関するクイックスタートは終了です。</span><span class="sxs-lookup"><span data-stu-id="de735-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="de735-218">続けて独自の開発環境で[分岐とループ](branches-and-loops-local.md)のクイックスタートに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="de735-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="de735-219">C# の数値の詳細については、次のトピックで学習できます。</span><span class="sxs-lookup"><span data-stu-id="de735-219">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="de735-220">[整数型の一覧表](../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="de735-220">[Integral Types Table](../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="de735-221">[浮動小数点型の一覧表](../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="de735-221">[Floating-Point Types Table](../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="de735-222">[組み込み型の一覧表](../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="de735-222">[Built-In Types Table](../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="de735-223">[暗黙的な数値変換の一覧表](../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="de735-223">[Implicit Numeric Conversions Table](../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="de735-224">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="de735-224">Explicit Numeric Conversions Table</span></span>](../language-reference/keywords/explicit-numeric-conversions-table.md)

