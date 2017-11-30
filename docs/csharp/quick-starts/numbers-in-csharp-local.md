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
# <a name="numbers-in-c-quick-start"></a><span data-ttu-id="4a809-103">C# のクイック スタートの番号</span><span class="sxs-lookup"><span data-stu-id="4a809-103">Numbers in C# quick start</span></span> #

<span data-ttu-id="4a809-104">このクイック スタートには、対話的に c# での数値の型について説明します。</span><span class="sxs-lookup"><span data-stu-id="4a809-104">This quick start teaches you about the number types in C# interactively.</span></span> <span data-ttu-id="4a809-105">少量のコードを記述し、コンパイルして、そのコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="4a809-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="4a809-106">クイック スタートには、一連数字と c# での算術演算を探索するレッスンにはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4a809-106">The quick start contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="4a809-107">これらのレッスンでは、C# 言語の基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="4a809-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="4a809-108">このクイック スタートを使用する開発に使用することができます、マシンが必要です。</span><span class="sxs-lookup"><span data-stu-id="4a809-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="4a809-109">.NET トピック[10 分後に開始](https://www.microsoft.com/net/core)Mac や PC、Linux 上のローカル開発環境を設定する方法についてはします。</span><span class="sxs-lookup"><span data-stu-id="4a809-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="4a809-110">整数の演算の確認</span><span class="sxs-lookup"><span data-stu-id="4a809-110">Explore integer math</span></span>

<span data-ttu-id="4a809-111">という名前のディレクトリを作成する**番号クイック スタート**です。</span><span class="sxs-lookup"><span data-stu-id="4a809-111">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="4a809-112">それを現在のディレクトリとし、`dotnet new console -n NumbersInCSharp -o .` を実行します。</span><span class="sxs-lookup"><span data-stu-id="4a809-112">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="4a809-113">開いている**Program.cs**好みのエディター、および置換行で`Console.Writeline("Hello World!");`次。</span><span class="sxs-lookup"><span data-stu-id="4a809-113">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="4a809-114">このコードを入力して実行`dotnet run`コマンド ウィンドウでします。</span><span class="sxs-lookup"><span data-stu-id="4a809-114">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="4a809-115">整数を使用した基本的な算術演算の 1 つを確認しました。</span><span class="sxs-lookup"><span data-stu-id="4a809-115">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="4a809-116">`int` 型は、**整数**を表します (正の整数、または負の整数)。</span><span class="sxs-lookup"><span data-stu-id="4a809-116">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="4a809-117">加算には `+` 記号を使用します。</span><span class="sxs-lookup"><span data-stu-id="4a809-117">You use the `+` symbol for addition.</span></span> <span data-ttu-id="4a809-118">他の一般的な整数の算術演算には次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="4a809-118">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="4a809-119">`-`: 減算</span><span class="sxs-lookup"><span data-stu-id="4a809-119">`-` for subtraction</span></span>
- <span data-ttu-id="4a809-120">`*`: 乗算</span><span class="sxs-lookup"><span data-stu-id="4a809-120">`*` for multiplication</span></span>
- <span data-ttu-id="4a809-121">`/`: 除算</span><span class="sxs-lookup"><span data-stu-id="4a809-121">`/` for division</span></span>

<span data-ttu-id="4a809-122">まずは、上記の各種演算を実行してみます。</span><span class="sxs-lookup"><span data-stu-id="4a809-122">Start by exploring those different operations.</span></span> <span data-ttu-id="4a809-123">後の行の値を書き込みますでこれらの行を追加`c`:</span><span class="sxs-lookup"><span data-stu-id="4a809-123">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="4a809-124">このコードを入力して実行`dotnet run`コマンド ウィンドウでします。</span><span class="sxs-lookup"><span data-stu-id="4a809-124">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="4a809-125">好みで、同じ行で複数の算術演算を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="4a809-125">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="4a809-126">再試行`c = a + b - 12 * 17;`例を示します。</span><span class="sxs-lookup"><span data-stu-id="4a809-126">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="4a809-127">変数と定数の数字の混合を許可するとします。</span><span class="sxs-lookup"><span data-stu-id="4a809-127">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="4a809-128">C# (または何らかのプログラミング言語) について詳しく学習するに従い、コードを記述する際にミスをすることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-128">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="4a809-129">**コンパイラ**は、そうしたエラーを発見して報告します。</span><span class="sxs-lookup"><span data-stu-id="4a809-129">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="4a809-130">出力には、エラー メッセージが含まれていると見ると密接にコード例を修正するかを確認、ウィンドウ内のコード。</span><span class="sxs-lookup"><span data-stu-id="4a809-130">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="4a809-131">こうした実習が C# コードの構造を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4a809-131">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="4a809-132">最初の手順を完了しました。</span><span class="sxs-lookup"><span data-stu-id="4a809-132">You've finished the first step.</span></span> <span data-ttu-id="4a809-133">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-133">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="4a809-134">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="4a809-134">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="4a809-135">`Main` メソッドの名前を `WorkingWithIntegers` に変更し、`WorkingWithIntegers` を呼び出す新しい `Main` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="4a809-135">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="4a809-136">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="4a809-136">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="4a809-137">演算の順序の確認</span><span class="sxs-lookup"><span data-stu-id="4a809-137">Explore order of operations</span></span>

<span data-ttu-id="4a809-138">呼び出しをコメント`WorkingWithIntegers()`です。</span><span class="sxs-lookup"><span data-stu-id="4a809-138">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="4a809-139">このセクションで作業するとわかりやすい出力にするには。</span><span class="sxs-lookup"><span data-stu-id="4a809-139">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="4a809-140">`//`開始、**コメント**(C#)。</span><span class="sxs-lookup"><span data-stu-id="4a809-140">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="4a809-141">コメントは、ソース コードで保持しますが、コードとして実行する任意のテキストです。</span><span class="sxs-lookup"><span data-stu-id="4a809-141">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="4a809-142">コンパイラは、コメントから実行可能コードを生成しません。</span><span class="sxs-lookup"><span data-stu-id="4a809-142">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="4a809-143">C# 言語は、数学で学んだ規則と同じ規則で各演算の優先順位を定義します。</span><span class="sxs-lookup"><span data-stu-id="4a809-143">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="4a809-144">乗算と除算は、加算と減算よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="4a809-144">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="4a809-145">次のコードを追加することで調査を`Main`メソッド、および execuing `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="4a809-145">Explore that by adding the following code to your `Main` method, and execuing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="4a809-146">出力を見ると、加算の前に乗算が実行されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="4a809-146">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="4a809-147">操作の別の順序を強制するには、操作を囲むかっこを追加することで、または対象の操作が最初に実行します。</span><span class="sxs-lookup"><span data-stu-id="4a809-147">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="4a809-148">次の行を追加し、もう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="4a809-148">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="4a809-149">さまざまな演算を多数組み合わせて、他にも試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-149">Explore more by combining many different operations.</span></span> <span data-ttu-id="4a809-150">下部にある次の行を追加、`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4a809-150">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="4a809-151">再試行`dotnet run`もう一度です。</span><span class="sxs-lookup"><span data-stu-id="4a809-151">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="4a809-152">整数について面白い動作をしていることに気づいたでしょうか。</span><span class="sxs-lookup"><span data-stu-id="4a809-152">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="4a809-153">常に整数の除算は、10 進数または分数部分を含めるように結果が期待する場合でも、結果の整数値を生成します。</span><span class="sxs-lookup"><span data-stu-id="4a809-153">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="4a809-154">この動作を目にしていない場合は、末尾に次のコードを実行してください、`Main`メソッド。</span><span class="sxs-lookup"><span data-stu-id="4a809-154">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="4a809-155">型`dotnet run`結果を表示するには、もう一度です。</span><span class="sxs-lookup"><span data-stu-id="4a809-155">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="4a809-156">続行する前に、このセクションで記述し、新しいメソッドに配置したすべてのコードを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-156">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="4a809-157">新しいメソッドを呼び出す`OrderPrecedence`です。</span><span class="sxs-lookup"><span data-stu-id="4a809-157">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="4a809-158">次のよう終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a809-158">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="4a809-159">整数の有効桁数と制限の確認</span><span class="sxs-lookup"><span data-stu-id="4a809-159">Explore integer precision and limits</span></span>
<span data-ttu-id="4a809-160">この最後のサンプルでは、整数の除算における結果の切り捨てについて確認します。</span><span class="sxs-lookup"><span data-stu-id="4a809-160">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="4a809-161">取得することができます、**残りの部分**を使用して、**剰余**、演算子、`%`文字です。</span><span class="sxs-lookup"><span data-stu-id="4a809-161">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="4a809-162">次のコードを実行してください、`Main`メソッド。</span><span class="sxs-lookup"><span data-stu-id="4a809-162">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="4a809-163">C# の整数型は算術における整数ともう 1 つ異なる点があります。それは `int` 型には最小値と最大値の制限があるということです。</span><span class="sxs-lookup"><span data-stu-id="4a809-163">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="4a809-164">このコードを追加、`Main`メソッドをこれらの制限を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a809-164">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="4a809-165">計算によってこれらの制限を超える値が作られると、**アンダーフロー**または**オーバーフロー**の状態になります。</span><span class="sxs-lookup"><span data-stu-id="4a809-165">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="4a809-166">計算の結果が 1 つの制限からもう 1 つの制限に折り返されているように見えます。</span><span class="sxs-lookup"><span data-stu-id="4a809-166">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="4a809-167">これら 2 つの行を追加、`Main`例を参照するメソッド。</span><span class="sxs-lookup"><span data-stu-id="4a809-167">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="4a809-168">計算の結果が最小値の (負の) 整数に極めて近いことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="4a809-168">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="4a809-169">これは `min + 2` と同じです。</span><span class="sxs-lookup"><span data-stu-id="4a809-169">It's the same as `min + 2`.</span></span> <span data-ttu-id="4a809-170">加算演算が許容された整数値を**オーバーフロー**しました。</span><span class="sxs-lookup"><span data-stu-id="4a809-170">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="4a809-171">整数がオーバーフローして最大値から最小値に ”折り返され” たため、計算結果が非常に大きな負の値になっています。</span><span class="sxs-lookup"><span data-stu-id="4a809-171">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="4a809-172">他にもさまざまな制限や有効桁数を持つ数値型があり、`int` 型がご自分のニーズと合わない場合は、そちらも使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a809-172">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="4a809-173">次はその別の数値型を見ていきます。</span><span class="sxs-lookup"><span data-stu-id="4a809-173">Let's explore those next.</span></span>

<span data-ttu-id="4a809-174">繰り返しますが、このセクションの内容を別のメソッドに記述したコードに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-174">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="4a809-175">これに `TestLimits` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="4a809-175">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="4a809-176">double 型の処理</span><span class="sxs-lookup"><span data-stu-id="4a809-176">Work with the double type</span></span>

<span data-ttu-id="4a809-177">`double` 数値型は、倍精度浮動小数点数を表します。</span><span class="sxs-lookup"><span data-stu-id="4a809-177">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="4a809-178">こうした用語を初めて見た人もいるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="4a809-178">Those terms may be new to you.</span></span> <span data-ttu-id="4a809-179">A**浮動小数点**数が非常に大規模なまたは大きさに小規模にすることがあります整数以外の数値を表すに便利です。</span><span class="sxs-lookup"><span data-stu-id="4a809-179">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="4a809-180">**倍精度**は、そうした数値が**単精度**よりも大きな有効桁数を使用して格納されることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="4a809-180">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="4a809-181">最近のコンピューターでは、単精度よりも倍精度の数値を使用する方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="4a809-181">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="4a809-182">確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-182">Let's explore.</span></span> <span data-ttu-id="4a809-183">次のコードを追加し、結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="4a809-183">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="4a809-184">計算結果に商の小数部分が含まれていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="4a809-184">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="4a809-185">double 型を使用して、もう少し複雑な式を試します。</span><span class="sxs-lookup"><span data-stu-id="4a809-185">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="4a809-186">double 値は整数値よりも範囲が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="4a809-186">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="4a809-187">これまで入力した、次のコードを試してください。</span><span class="sxs-lookup"><span data-stu-id="4a809-187">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="4a809-188">これらの値は、科学的表記法で出力されます。</span><span class="sxs-lookup"><span data-stu-id="4a809-188">These values are printed out in scientific notation.</span></span> <span data-ttu-id="4a809-189">左側には、番号、`E`の有効桁がします。</span><span class="sxs-lookup"><span data-stu-id="4a809-189">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="4a809-190">右側の数値は指数であり、10 の累乗です。</span><span class="sxs-lookup"><span data-stu-id="4a809-190">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="4a809-191">算術における 10 進数と同じように、C# における double には丸め誤差が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="4a809-191">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="4a809-192">次のコードを試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-192">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="4a809-193">`0.3` の循環小数は `1/3` と完全に同じではありません。</span><span class="sxs-lookup"><span data-stu-id="4a809-193">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="4a809-194">***課題***</span><span class="sxs-lookup"><span data-stu-id="4a809-194">***Challenge***</span></span>

<span data-ttu-id="4a809-195">`double` 型を使用して、大きい値や小さい値、乗算、除算などの計算してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-195">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="4a809-196">もっと複雑な計算を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="4a809-196">Try more complicated calculations.</span></span>

<span data-ttu-id="4a809-197">チャレンジ時間を費やしている後は、コードを作成し、新しいメソッドに配置を実行します。</span><span class="sxs-lookup"><span data-stu-id="4a809-197">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="4a809-198">その新しいメソッドの名前を付けます`WorkWithDoubles`です。</span><span class="sxs-lookup"><span data-stu-id="4a809-198">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="4a809-199">固定小数点型の処理</span><span class="sxs-lookup"><span data-stu-id="4a809-199">Work with fixed point types</span></span>

<span data-ttu-id="4a809-200">C# の基本的な数値型である整数と double について見てきました。</span><span class="sxs-lookup"><span data-stu-id="4a809-200">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="4a809-201">もう 1 つ知っておくべき型として、`decimal` 型があります。</span><span class="sxs-lookup"><span data-stu-id="4a809-201">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="4a809-202">`decimal`型がより大きい有効桁数が、範囲を小さく`double`です。</span><span class="sxs-lookup"><span data-stu-id="4a809-202">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="4a809-203">**固定小数点**という用語は、小数点 (またはバイナリの小数点) が動かないことを意味しています。</span><span class="sxs-lookup"><span data-stu-id="4a809-203">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="4a809-204">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="4a809-204">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="4a809-205">`double` 型よりも範囲が小さいことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="4a809-205">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="4a809-206">次のコードを実行すると、decimal 型では有効桁数がより大きいことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="4a809-206">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="4a809-207">数値の末尾の `M` は、定数では `decimal` 型を使用する必要があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="4a809-207">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="4a809-208">decimal 型を使用した演算では、小数点の右側の桁数がより多いことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="4a809-208">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="4a809-209">***課題***</span><span class="sxs-lookup"><span data-stu-id="4a809-209">***Challenge***</span></span>

<span data-ttu-id="4a809-210">さまざまな数値型を確認したので、次は半径が 2.50 インチの円の面積を計算するコードを記述してみます。</span><span class="sxs-lookup"><span data-stu-id="4a809-210">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 inches.</span></span> <span data-ttu-id="4a809-211">円の面積は、半径の 2 乗 x 円周率です。</span><span class="sxs-lookup"><span data-stu-id="4a809-211">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="4a809-212">1 つのヒント: c# PI の定数が含まれる<xref:System.Math.PI?displayProperty=nameWithType>の値に対して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4a809-212">One hint: C# contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="4a809-213">によって、応答をチェックする[GitHub の完成後のサンプル コードを見る](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="4a809-213">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="4a809-214">希望の場合は、その他のいくつかの数式を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="4a809-214">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="4a809-215">"番号で c#"クイック スタートが完了しました。</span><span class="sxs-lookup"><span data-stu-id="4a809-215">You've completed the "Numbers in C#" quick start.</span></span> <span data-ttu-id="4a809-216">続行できますが、[分岐とループ](branches-and-loops-local.md)独自開発環境でのクイック スタート。</span><span class="sxs-lookup"><span data-stu-id="4a809-216">You can continue with the [Branches and loops](branches-and-loops-local.md) quick start in your own development environment.</span></span>

<span data-ttu-id="4a809-217">C# の数値の詳細については、次のトピックで学習できます。</span><span class="sxs-lookup"><span data-stu-id="4a809-217">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="4a809-218">[整数型の一覧表](../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="4a809-218">[Integral Types Table](../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="4a809-219">[浮動小数点型の一覧表](../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="4a809-219">[Floating-Point Types Table](../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="4a809-220">[組み込み型の一覧表](../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="4a809-220">[Built-In Types Table](../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="4a809-221">[暗黙的な数値変換の一覧表](../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="4a809-221">[Implicit Numeric Conversions Table](../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="4a809-222">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="4a809-222">Explicit Numeric Conversions Table</span></span>](../language-reference/keywords/explicit-numeric-conversions-table.md)

