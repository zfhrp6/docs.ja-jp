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
# <a name="branches-and-loops"></a><span data-ttu-id="2c160-103">分岐とループ</span><span class="sxs-lookup"><span data-stu-id="2c160-103">Branches and loops</span></span>

<span data-ttu-id="2c160-104">このクイック スタートでは、変数を検査し、それらの変数に基づいて実行パスを変更するコードを記述する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="2c160-104">This quick start teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="2c160-105">C# コードを記述し、コンパイルと実行の結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="2c160-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="2c160-106">クイック スタートには、一連分岐構造やループ構造 (C#) を探索するレッスンにはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2c160-106">The quick start contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="2c160-107">これらのレッスンでは、C# 言語の基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="2c160-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="2c160-108">このクイック スタートを使用する開発に使用することができます、マシンが必要です。</span><span class="sxs-lookup"><span data-stu-id="2c160-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="2c160-109">.NET トピック[10 分後に開始](https://www.microsoft.com/net/core)Mac や PC、Linux 上のローカル開発環境を設定する方法についてはします。</span><span class="sxs-lookup"><span data-stu-id="2c160-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="2c160-110">使用して決定、`if`ステートメント</span><span class="sxs-lookup"><span data-stu-id="2c160-110">Make decisions using the `if` statement</span></span>

<span data-ttu-id="2c160-111">という名前のディレクトリを作成する**分岐クイック スタート**です。</span><span class="sxs-lookup"><span data-stu-id="2c160-111">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="2c160-112">それを現在のディレクトリとし、`dotnet new console -n BranchesAndLoops -o .` を実行します。</span><span class="sxs-lookup"><span data-stu-id="2c160-112">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="2c160-113">このコマンドは、現在のディレクトリに新しい .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c160-113">This command creates a new .NET Core console application in the current directory.</span></span> 

<span data-ttu-id="2c160-114">開いている**Program.cs**好みのエディター、および置換行`Console.Writeline("Hello World!");`を次のコード。</span><span class="sxs-lookup"><span data-stu-id="2c160-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="2c160-115">このコードを入力して実行`dotnet run`で、コンソール ウィンドウは、です。</span><span class="sxs-lookup"><span data-stu-id="2c160-115">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="2c160-116">メッセージが表示する必要があります「回答は、10 を超えています」。</span><span class="sxs-lookup"><span data-stu-id="2c160-116">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="2c160-117">コンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="2c160-117">printed to your console.</span></span>

<span data-ttu-id="2c160-118">合計が 10 未満になるように `b` の宣言を変更します。</span><span class="sxs-lookup"><span data-stu-id="2c160-118">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="2c160-119">型`dotnet run`もう一度です。</span><span class="sxs-lookup"><span data-stu-id="2c160-119">Type `dotnet run` again.</span></span> <span data-ttu-id="2c160-120">計算結果が 10 未満であるため、何も出力されません。</span><span class="sxs-lookup"><span data-stu-id="2c160-120">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="2c160-121">判定中の**条件**が false になっています。</span><span class="sxs-lookup"><span data-stu-id="2c160-121">The **condition** you're testing is false.</span></span> <span data-ttu-id="2c160-122">`if` ステートメントの考えられる分岐の 1 つである true 分岐のみを記述したため、実行すべきコードがありません。</span><span class="sxs-lookup"><span data-stu-id="2c160-122">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="2c160-123">C# (または何らかのプログラミング言語) について詳しく学習するに従い、コードを記述する際にミスをすることもあるでしょう。</span><span class="sxs-lookup"><span data-stu-id="2c160-123">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="2c160-124">コンパイラを検索し、エラーをレポートします。</span><span class="sxs-lookup"><span data-stu-id="2c160-124">The compiler will find and report the errors.</span></span> <span data-ttu-id="2c160-125">よく見ると、エラー出力とエラーを生成したコード。</span><span class="sxs-lookup"><span data-stu-id="2c160-125">Look closely the the error output and the code that generated the error.</span></span> <span data-ttu-id="2c160-126">Compler エラー通常役立つ問題を特定します。</span><span class="sxs-lookup"><span data-stu-id="2c160-126">The compler error can usually help you find the problem.</span></span> 

<span data-ttu-id="2c160-127">この最初の例は、の機能を示しています`if`およびブール型です。</span><span class="sxs-lookup"><span data-stu-id="2c160-127">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="2c160-128">A*ブール*変数 2 つの値のいずれかです:`true`または`false`です。</span><span class="sxs-lookup"><span data-stu-id="2c160-128">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="2c160-129">C# の場合、特殊な種類の定義`bool`ブール値変数。</span><span class="sxs-lookup"><span data-stu-id="2c160-129">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="2c160-130">`if` ステートメントは、`bool` の値を確認します。</span><span class="sxs-lookup"><span data-stu-id="2c160-130">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="2c160-131">値が `true` の場合、`if` に続くステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="2c160-131">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="2c160-132">それ以外の場合はスキップします。</span><span class="sxs-lookup"><span data-stu-id="2c160-132">Otherwise, it is skipped.</span></span> 

<span data-ttu-id="2c160-133">条件を確認してその条件に基づいてステートメントを実行するというこのプロセスは非常に機能的です。</span><span class="sxs-lookup"><span data-stu-id="2c160-133">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>


## <a name="make-if-and-else-work-together"></a><span data-ttu-id="2c160-134">if と else を組み合わせた使用</span><span class="sxs-lookup"><span data-stu-id="2c160-134">Make if and else work together</span></span>

<span data-ttu-id="2c160-135">true 分岐と false 分岐で別々のコードを実行するには、条件が false のときに実行する `else` 分岐を作成します。</span><span class="sxs-lookup"><span data-stu-id="2c160-135">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="2c160-136">これを再試行してください。</span><span class="sxs-lookup"><span data-stu-id="2c160-136">Try this.</span></span> <span data-ttu-id="2c160-137">次のコードの最後の 2 つの行を追加、`Main`メソッド (既に最初の 4 つ)。</span><span class="sxs-lookup"><span data-stu-id="2c160-137">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="2c160-138">`else` キーワードに続くステートメントは、判定中の条件が `false` のときにのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="2c160-138">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="2c160-139">結合`if`と`else`条件が両方を処理する必要があります。 すべての電力を供給とブール値、`true`と`false`条件。</span><span class="sxs-lookup"><span data-stu-id="2c160-139">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c160-140">`if` と `else` のステートメント内にあるインデントは、人が読みやすいようにするためのものです。</span><span class="sxs-lookup"><span data-stu-id="2c160-140">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="2c160-141">C# 言語はインデントや空白文字を重要なものとして扱いません。</span><span class="sxs-lookup"><span data-stu-id="2c160-141">The C# language doesn't treat indentation or whitespace as significant.</span></span> <span data-ttu-id="2c160-142">`if` や `else` のキーワードに続くステートメントは、条件に基づいて実行されます。</span><span class="sxs-lookup"><span data-stu-id="2c160-142">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="2c160-143">このクイック スタートのすべてのサンプルでは、ステートメントの制御フローに基づく行をインデントする一般的な方法に従います。</span><span class="sxs-lookup"><span data-stu-id="2c160-143">All the samples in this quick start follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="2c160-144">インデントは重要ではないため、条件に基づいて実行するブロック内に 1 つ以上のステートメントがある場合には、`{` と `}` を使用して示します。</span><span class="sxs-lookup"><span data-stu-id="2c160-144">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="2c160-145">通常、C# プログラマーは `if` と `else` の句にはこの中かっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c160-145">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="2c160-146">次の例では、作成したものと同じです。</span><span class="sxs-lookup"><span data-stu-id="2c160-146">The following example is the same as the one you just created.</span></span> <span data-ttu-id="2c160-147">次のコードに一致するコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="2c160-147">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="2c160-148">このクイック スタートの残りの部分からすべてのコード サンプルは、後に、中かっこを含めるプラクティスを受け入れられます。</span><span class="sxs-lookup"><span data-stu-id="2c160-148">Through the rest of this quick start, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="2c160-149">複雑な条件をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="2c160-149">You can test more complicated conditions.</span></span> <span data-ttu-id="2c160-150">次のコードを追加、`Main`これまでに作成したコードの後にメソッド。</span><span class="sxs-lookup"><span data-stu-id="2c160-150">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="2c160-151">`&&` は "and" (および) を表します。</span><span class="sxs-lookup"><span data-stu-id="2c160-151">The `&&` represents "and".</span></span> <span data-ttu-id="2c160-152">これは、true 分岐でステートメントを実行するには、両方の条件が true になる必要があることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="2c160-152">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="2c160-153">また、これらの例では、ステートメントが `{` と `}` で囲まれていれば、各条件分岐に複数のステートメントを持つことができることを示しています。</span><span class="sxs-lookup"><span data-stu-id="2c160-153">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="2c160-154">使用することも`||`を表す「または」です。</span><span class="sxs-lookup"><span data-stu-id="2c160-154">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="2c160-155">これまで入力した後、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="2c160-155">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="2c160-156">最初の手順を完了しました。</span><span class="sxs-lookup"><span data-stu-id="2c160-156">You've finished the first step.</span></span> <span data-ttu-id="2c160-157">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="2c160-157">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="2c160-158">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="2c160-158">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="2c160-159">`Main` メソッドの名前を `ExploreIf` に変更し、`ExploreIf` を呼び出す新しい `Main` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="2c160-159">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="2c160-160">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="2c160-160">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="2c160-161">呼び出しをコメント`ExploreIf()`です。</span><span class="sxs-lookup"><span data-stu-id="2c160-161">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="2c160-162">このセクションで作業するとわかりやすい出力にするには。</span><span class="sxs-lookup"><span data-stu-id="2c160-162">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="2c160-163">`//`開始、**コメント**(C#)。</span><span class="sxs-lookup"><span data-stu-id="2c160-163">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="2c160-164">コメントは、ソース コードで保持しますが、コードとして実行する任意のテキストです。</span><span class="sxs-lookup"><span data-stu-id="2c160-164">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="2c160-165">コンパイラは、コメントから実行可能コードを生成しません。</span><span class="sxs-lookup"><span data-stu-id="2c160-165">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="2c160-166">ループを使用した処理の繰り返し</span><span class="sxs-lookup"><span data-stu-id="2c160-166">Use loops to repeat operations</span></span>

<span data-ttu-id="2c160-167">このセクションでは使用して**ループ**ステートメントを繰り返す。</span><span class="sxs-lookup"><span data-stu-id="2c160-167">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="2c160-168">このコードを実行してください、`Main`メソッド。</span><span class="sxs-lookup"><span data-stu-id="2c160-168">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="2c160-169">`while`ステートメントは、条件をチェックして、ステートメントまたはステートメント ブロックが次の実行、`while`です。</span><span class="sxs-lookup"><span data-stu-id="2c160-169">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="2c160-170">条件で、これらのステートメントを実行する条件が false になるまで繰り返しチェックします。</span><span class="sxs-lookup"><span data-stu-id="2c160-170">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="2c160-171">この例では、もう 1 つ新しい演算子が使用されています。</span><span class="sxs-lookup"><span data-stu-id="2c160-171">There's one other new operator in this example.</span></span> <span data-ttu-id="2c160-172">`counter` 変数のあとにある `++` は、**インクリメント**演算子です。</span><span class="sxs-lookup"><span data-stu-id="2c160-172">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="2c160-173">値に 1 を加算`counter`内でその値を格納し、`counter`変数。</span><span class="sxs-lookup"><span data-stu-id="2c160-173">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c160-174">確認して、`while`コードを実行するように条件が false に変化をループします。</span><span class="sxs-lookup"><span data-stu-id="2c160-174">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="2c160-175">それ以外の場合は、プログラムが終了することのない**無限ループ**を作成します。</span><span class="sxs-lookup"><span data-stu-id="2c160-175">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="2c160-176">使用しない場合は、プログラムを強制する必要がないこのサンプルで示すは**ctrl キーを押しながら C**またはその他の手段です。</span><span class="sxs-lookup"><span data-stu-id="2c160-176">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="2c160-177">`while` ループは、条件を判定してから `while` に続くコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="2c160-177">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="2c160-178">`do` ... `while` ループは、最初にコードを実行してからその条件を確認します。</span><span class="sxs-lookup"><span data-stu-id="2c160-178">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="2c160-179">ループは、次のコードに表示されるときに:</span><span class="sxs-lookup"><span data-stu-id="2c160-179">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="2c160-180">これは、`do`ループと以前`while`ループが同じ出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="2c160-180">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="2c160-181">for ループの処理</span><span class="sxs-lookup"><span data-stu-id="2c160-181">Work with the for loop</span></span>

<span data-ttu-id="2c160-182">**の**ループは c# でよく使用します。</span><span class="sxs-lookup"><span data-stu-id="2c160-182">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="2c160-183">Main() メソッドでは、このコードを試してください。</span><span class="sxs-lookup"><span data-stu-id="2c160-183">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="2c160-184">このループは、既に使用した `while` ループや `do` ループと同じ機能を持っています。</span><span class="sxs-lookup"><span data-stu-id="2c160-184">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="2c160-185">`for` ステートメントは 3 つの部分に分かれてその機能を制御します。</span><span class="sxs-lookup"><span data-stu-id="2c160-185">The `for` statement has three parts that control how it works.</span></span> 

<span data-ttu-id="2c160-186">最初の部分は、**for 初期化子**です。`for index = 0;` は、`index` がループ変数であることを宣言し、その初期値を `0` に設定しています。</span><span class="sxs-lookup"><span data-stu-id="2c160-186">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="2c160-187">2 つ目の部分は、**for 条件**です。`index < 10` は、counter の値が 10 未満である間は `for` ループが実行され続けることを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="2c160-187">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="2c160-188">最後の部分は、**for 反復子**です。`index++` は、`for` ステートメントに続くブロックを実行したあとにループ変数を変更する方法を指定しています。</span><span class="sxs-lookup"><span data-stu-id="2c160-188">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="2c160-189">ここでは、ブロックが実行されるごとに `index` が 1 ずつ増加するよう指定しています。</span><span class="sxs-lookup"><span data-stu-id="2c160-189">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="2c160-190">ご自身でこれを実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="2c160-190">Experiment with these yourself.</span></span> <span data-ttu-id="2c160-191">以下をそれぞれ試してみます。</span><span class="sxs-lookup"><span data-stu-id="2c160-191">Try each of the following:</span></span>

- <span data-ttu-id="2c160-192">初期化子を変更して別の値で開始する。</span><span class="sxs-lookup"><span data-stu-id="2c160-192">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="2c160-193">条件を変更して別の値で停止する。</span><span class="sxs-lookup"><span data-stu-id="2c160-193">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="2c160-194">完了したら次に進み、学習したことを使用して自分でいくつかのコードを記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="2c160-194">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="2c160-195">分岐とループを結合します。</span><span class="sxs-lookup"><span data-stu-id="2c160-195">Combine branches and loops</span></span>

<span data-ttu-id="2c160-196">C# 言語における `if` ステートメントとループ構造を見てきました。では、1 から 20 の整数のうち 3 で割り切れる数の合計を求める C# コードを記述できるか確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="2c160-196">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="2c160-197">次にいくつかヒントを示します。</span><span class="sxs-lookup"><span data-stu-id="2c160-197">Here are a few hints:</span></span>

- <span data-ttu-id="2c160-198">`%` 演算子は、除算演算の剰余を算出します。</span><span class="sxs-lookup"><span data-stu-id="2c160-198">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="2c160-199">`if`ステートメントを使用する条件が、数が合計の一部にする必要があるかどうかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c160-199">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="2c160-200">`for` ループは、1 から 20 までのすべての数を 1 つずつ確認する一連の手順を繰り返すのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2c160-200">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="2c160-201">ご自身で試してみてください。</span><span class="sxs-lookup"><span data-stu-id="2c160-201">Try it yourself.</span></span> <span data-ttu-id="2c160-202">そして自分がとった方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="2c160-202">Then check how you did.</span></span> <span data-ttu-id="2c160-203">考えられる 1 つの解答を確認できます[GitHub の完成したコードを表示する](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54)です。</span><span class="sxs-lookup"><span data-stu-id="2c160-203">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="2c160-204">「ループおよび分岐」のクイック スタートが完了しました。</span><span class="sxs-lookup"><span data-stu-id="2c160-204">You've completed the "branches and loops" quick start.</span></span>

<span data-ttu-id="2c160-205">続行できますが、[配列およびコレクション](arrays-and-collections.md)独自開発環境でのクイック スタート。</span><span class="sxs-lookup"><span data-stu-id="2c160-205">You can continue with the [Arrays and collections](arrays-and-collections.md) quick start in your own development environment.</span></span>

<span data-ttu-id="2c160-206">次のトピックでこれらの概念の詳細を学習できます。</span><span class="sxs-lookup"><span data-stu-id="2c160-206">You can learn more about these concepts in these topics:</span></span>

<span data-ttu-id="2c160-207">[if と else ステートメント](../language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="2c160-207">[If and else statement](../language-reference/keywords/if-else.md) </span></span>  
<span data-ttu-id="2c160-208">[while ステートメント](../language-reference/keywords/while.md) </span><span class="sxs-lookup"><span data-stu-id="2c160-208">[While statement](../language-reference/keywords/while.md) </span></span>  
<span data-ttu-id="2c160-209">[do ステートメント](../language-reference/keywords/do.md) </span><span class="sxs-lookup"><span data-stu-id="2c160-209">[Do statement](../language-reference/keywords/do.md) </span></span>  
[<span data-ttu-id="2c160-210">for ステートメント</span><span class="sxs-lookup"><span data-stu-id="2c160-210">For statement</span></span>](../language-reference/keywords/for.md)   
