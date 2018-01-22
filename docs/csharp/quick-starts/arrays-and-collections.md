---
title: "クイック スタート - コレクション - C# ガイド"
description: "このクイック スタートでは、リスト コレクションについて確認して C# を学習します。"
keywords: "C#, 使用開始, チュートリアル, コレクション, リスト"
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 44e79432c0a1970313cba21778e2bf439f8a4388
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2018
---
# <a name="c-quick-start-collections"></a><span data-ttu-id="5f35a-104">C# クイック スタート: コレクション</span><span class="sxs-lookup"><span data-stu-id="5f35a-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="5f35a-105">このクイック スタートでは、C# 言語の概要と <xref:System.Collections.Generic.List%601> クラスの基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-105">This quick start provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="5f35a-106">このクイック スタートでは、開発用に使用できるマシンがあることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="5f35a-106">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="5f35a-107">Mac、PC、または Linux 上でローカルの開発環境を設定する手順については、.NET の [10 分でわかる概要](https://www.microsoft.com/net/core)に関するトピックに記載されています。</span><span class="sxs-lookup"><span data-stu-id="5f35a-107">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="5f35a-108">使用するコマンドの概要を手短に確認するには、[ローカルでのクイック スタートの概要](local-environment.md)と詳細へのリンクをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5f35a-108">A quick overview of the commands you'll use is in the [introduction to the local quick starts](local-environment.md) with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="5f35a-109">基本のリストの例。</span><span class="sxs-lookup"><span data-stu-id="5f35a-109">A basic list example.</span></span>

<span data-ttu-id="5f35a-110">「**list-quickstart**」という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="5f35a-111">それを現在のディレクトリとし、`dotnet new console` を実行します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-111">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="5f35a-112">[10 分でわかる .NET の概要](https://www.microsoft.com/net)を完了したところであれば、先ほど作成した myApp アプリケーションを引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-112">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>
 
<span data-ttu-id="5f35a-113">好みのエディターで **Program.cs** を開き、既存のコードを次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-113">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="5f35a-114">`<name>` をユーザー名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="5f35a-115">**Program.cs** を保存します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-115">Save **Program.cs**.</span></span> <span data-ttu-id="5f35a-116">コンソール ウィンドウに「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="5f35a-117">文字列のリストを作成し、そのリストに 3 つの名前を追加し、それらの名前をすべて大文字で出力しました。</span><span class="sxs-lookup"><span data-stu-id="5f35a-117">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="5f35a-118">先のクイック スタートで学習した概念を使用して、リストをループしています。</span><span class="sxs-lookup"><span data-stu-id="5f35a-118">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="5f35a-119">名前を表示するコードは、**補間文字列**を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-119">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="5f35a-120">`string` の前に文字 `$` を配置すると、文字列宣言に C# コードを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="5f35a-121">実際の文字列は、生成する値でその C# コードを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="5f35a-122">この例では、<xref:System.String.ToUpper%2A> メソッドを呼び出したため、文字列は `{name.ToUpper()}` をそれぞれの名前に置き換え、文字を大文字に変換しています。</span><span class="sxs-lookup"><span data-stu-id="5f35a-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="5f35a-123">続けて確認していきましょう。</span><span class="sxs-lookup"><span data-stu-id="5f35a-123">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="5f35a-124">リスト コンテンツを変更する</span><span class="sxs-lookup"><span data-stu-id="5f35a-124">Modify list contents</span></span>

<span data-ttu-id="5f35a-125">作成したコレクションは <xref:System.Collections.Generic.List%601> 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="5f35a-126">この型は、要素のシーケンスを格納します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-126">This type stores sequences of elements.</span></span> <span data-ttu-id="5f35a-127">要素の型を山かっこの内側で指定します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-127">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="5f35a-128">この <xref:System.Collections.Generic.List%601> 型の重要な点は増減が可能で、要素を追加したり削除したりできることです。</span><span class="sxs-lookup"><span data-stu-id="5f35a-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="5f35a-129">`Main` メソッドの閉じかっこ `}` の前に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-129">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="5f35a-130">さらに 2 つの名前をリストの末尾に追加しました。</span><span class="sxs-lookup"><span data-stu-id="5f35a-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="5f35a-131">また、1 つを削除しました。</span><span class="sxs-lookup"><span data-stu-id="5f35a-131">You've also removed one as well.</span></span> <span data-ttu-id="5f35a-132">ファイルを保存し、「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-132">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="5f35a-133"><xref:System.Collections.Generic.List%601> を使用すると、**インデックス**でも個々の項目を参照できます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="5f35a-134">リスト名に続く `[` と `]` のトークンの間にインデックスを記述します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="5f35a-135">C# では、初めのインデックスには 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="5f35a-136">追加したコードのすぐ下に次のコードを追加して試します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="5f35a-137">リストの末尾を越えてインデックスにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5f35a-137">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="5f35a-138">インデックスは 0 から始まるため、有効なインデックスの最大値はリスト内の項目の数より 1 小さくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5f35a-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="5f35a-139"><xref:System.Collections.Generic.List%601.Count%2A> プロパティを使用すれば、リストの長さを確認できます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="5f35a-140">次のコードを Main メソッドの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-140">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="5f35a-141">ファイルを保存し、もう一度「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-141">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="5f35a-142">リストを検索して並び替える</span><span class="sxs-lookup"><span data-stu-id="5f35a-142">Search and sort lists</span></span>
<span data-ttu-id="5f35a-143">サンプルでは比較的小さいリストを使用していますが、ご利用のアプリケーションでは、より多くの (場合によっては何千もの) 要素が含まれるリストを作成することもよくあるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="5f35a-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="5f35a-144">そうした大規模なコレクションの中から要素を見つけるには、別々の項目をリストで検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5f35a-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="5f35a-145"><xref:System.Collections.Generic.List%601.IndexOf%2A> メソッドは項目を検索し、その項目のインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="5f35a-146">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-146">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="5f35a-147">同じように、リスト内の項目を並び替えできます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-147">The items in your list can be sorted as well.</span></span> <span data-ttu-id="5f35a-148"><xref:System.Collections.Generic.List%601.Sort%2A> メソッドは、リスト内のすべての項目を正規順序 (文字列の場合はアルファベット順) で並び替えます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-148">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="5f35a-149">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-149">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="5f35a-150">ファイルを保存し、「`dotnet run`」と入力してこの最新バージョンを試します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-150">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="5f35a-151">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5f35a-151">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="5f35a-152">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="5f35a-152">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="5f35a-153">`Main` メソッドの名前を `WorkingWithStrings` に変更し、`WorkingWithStrings` を呼び出す新しい `Main` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-153">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="5f35a-154">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="5f35a-154">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="5f35a-155">その他の型のリスト</span><span class="sxs-lookup"><span data-stu-id="5f35a-155">Lists of other types</span></span>

<span data-ttu-id="5f35a-156">ここまでは、リスト内で `string` 型を使用してきました。</span><span class="sxs-lookup"><span data-stu-id="5f35a-156">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="5f35a-157">別の型を使用して <xref:System.Collections.Generic.List%601> を作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5f35a-157">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="5f35a-158">数値のセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-158">Let's build a set of numbers.</span></span> 

<span data-ttu-id="5f35a-159">新しい `Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-159">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="5f35a-160">これにより整数のリストが作成され、最初の 2 つの整数が値 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-160">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="5f35a-161">これらは、数列の 1 つである*フィボナッチ数列*の最初の 2 つの値です。</span><span class="sxs-lookup"><span data-stu-id="5f35a-161">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="5f35a-162">次のフィボナッチ数はそれぞれ、その直前の 2 つの数値の合計を取得することによって得られます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-162">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="5f35a-163">このコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-163">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="5f35a-164">ファイルを保存し、「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-164">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="5f35a-165">このセクションにだけ集中したいときは、`WorkingWithStrings();` を呼び出すコードはコメント アウトしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="5f35a-165">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="5f35a-166">`// WorkingWithStrings();` のように、呼び出しの前に `/` 文字を 2 つ記述します。</span><span class="sxs-lookup"><span data-stu-id="5f35a-166">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="5f35a-167">課題</span><span class="sxs-lookup"><span data-stu-id="5f35a-167">Challenge</span></span>
<span data-ttu-id="5f35a-168">このレッスンと以前のレッスンの中から、いくつかの概念を理解できているかどうかを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5f35a-168">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="5f35a-169">ここまでフィボナッチ数を使用して作成してきたコードを使ってください。</span><span class="sxs-lookup"><span data-stu-id="5f35a-169">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="5f35a-170">シーケンスの最初の 20 個の数を生成するコードを記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="5f35a-170">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="5f35a-171">(ヒント: フィボナッチ数の 20 番目の数は 6765 です。)</span><span class="sxs-lookup"><span data-stu-id="5f35a-171">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="5f35a-172">課題完了</span><span class="sxs-lookup"><span data-stu-id="5f35a-172">Complete challenge</span></span>

<span data-ttu-id="5f35a-173">[GitHub にある完成したサンプル コード](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)で、ソリューションの例を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-173">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="5f35a-174">ループの繰り返しごとに、リストの最後の 2 つの整数を取得して合計し、その値をリストに追加しています。</span><span class="sxs-lookup"><span data-stu-id="5f35a-174">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="5f35a-175">このループは、20 個の項目がリストに追加されるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-175">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="5f35a-176">おつかれさまでした。リストについてのクイック スタートはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="5f35a-176">Congratulations, you've completed the list quick start.</span></span> <span data-ttu-id="5f35a-177">続けて独自の開発環境で[クラスの概要](introduction-to-classes.md)のクイック スタートに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-177">You can continue with the [Introduction to classes](introduction-to-classes.md) quick start in your own development environment.</span></span>

<span data-ttu-id="5f35a-178">`List` 型の使用方法の詳細については、[.NET ガイド](../../standard/index.md)の[コレクション](../../standard/collections/index.md)に関するトピックで学習できます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-178">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="5f35a-179">その他の多くのコレクション型についても学習できます。</span><span class="sxs-lookup"><span data-stu-id="5f35a-179">You'll also learn about many other collection types.</span></span>
