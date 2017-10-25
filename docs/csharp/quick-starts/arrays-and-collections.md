---
title: "クイック スタート - コレクション - C# ガイド"
description: "このクイック スタートでは、リスト コレクションについて確認して C# を学習します。"
keywords: "C#, 使用開始, チュートリアル, コレクション, リスト"
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
# <a name="c-quick-start-collections"></a><span data-ttu-id="e104b-104">C# クイック スタート: コレクション</span><span class="sxs-lookup"><span data-stu-id="e104b-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="e104b-105">このチュートリアルでは、C# 言語の概要と <xref:System.Collections.Generic.List%601> クラスの基本を説明します。</span><span class="sxs-lookup"><span data-stu-id="e104b-105">This tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="a-simple-list-example"></a><span data-ttu-id="e104b-106">単純なリストの例</span><span class="sxs-lookup"><span data-stu-id="e104b-106">A simple list example.</span></span>

> [!NOTE]
> <span data-ttu-id="e104b-107">[dot.net](https://dot.net/) で記述したコードから開始する場合、既にこのセクションにコードが記述されています。</span><span class="sxs-lookup"><span data-stu-id="e104b-107">If you're starting from the code you wrote in [dot.net](https://dot.net/), you already have the code written in this section.</span></span> <span data-ttu-id="e104b-108">「[リスト コンテンツを変更する](#modify-list-contents)」へ進んでください。</span><span class="sxs-lookup"><span data-stu-id="e104b-108">Jump to [Modify list contents](#modify-list-contents).</span></span>

<span data-ttu-id="e104b-109">このレッスンでは、オンラインのクイック スタートを終了していることと、[.NET Core SDK](http://dot.net/core) と [Visual Studio Code](https://code.visualstudio.com/) がインストール済みであることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="e104b-109">This lesson assumes you've finished the online quick starts, and you've installed the [.NET Core SDK](http://dot.net/core) and [Visual Studio Code](https://code.visualstudio.com/).</span></span> 

<span data-ttu-id="e104b-110">「**list-quickstart**」という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="e104b-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="e104b-111">それを現在のディレクトリとし、`dotnet new console` を実行します。</span><span class="sxs-lookup"><span data-stu-id="e104b-111">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="e104b-112">好みのエディターで **Program.cs** を開き、既存のコードを次のコードで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e104b-112">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="e104b-113">`<name>` をユーザー名で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e104b-113">Replace `<name>` with your name.</span></span> <span data-ttu-id="e104b-114">**Program.cs** を保存します。</span><span class="sxs-lookup"><span data-stu-id="e104b-114">Save **Program.cs**.</span></span> <span data-ttu-id="e104b-115">コンソール ウィンドウに「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="e104b-115">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="e104b-116">文字列のリストを作成し、そのリストに 3 つの名前を追加し、それらの名前をすべて大文字で出力しました。</span><span class="sxs-lookup"><span data-stu-id="e104b-116">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="e104b-117">先のクイック スタートで学習した概念を使用して、リストをループしています。</span><span class="sxs-lookup"><span data-stu-id="e104b-117">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="e104b-118">名前を表示するコードは、**補間文字列**を使用します。</span><span class="sxs-lookup"><span data-stu-id="e104b-118">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="e104b-119">`string` の前に文字 `$` を配置すると、文字列宣言に C# コードを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e104b-119">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="e104b-120">実際の文字列は、生成する値でその C# コードを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e104b-120">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="e104b-121">この例では、<xref:System.String.ToUpper%2A> メソッドを呼び出したため、文字列は `{name.ToUpper()}` をそれぞれの名前に置き換え、文字を大文字に変換しています。</span><span class="sxs-lookup"><span data-stu-id="e104b-121">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="e104b-122">続けて確認していきましょう。</span><span class="sxs-lookup"><span data-stu-id="e104b-122">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="e104b-123">リスト コンテンツを変更する</span><span class="sxs-lookup"><span data-stu-id="e104b-123">Modify list contents</span></span>

<span data-ttu-id="e104b-124">作成したコレクションは <xref:System.Collections.Generic.List%601> 型を使用します。</span><span class="sxs-lookup"><span data-stu-id="e104b-124">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="e104b-125">この型は、要素のシーケンスを格納します。</span><span class="sxs-lookup"><span data-stu-id="e104b-125">This type stores sequences of elements.</span></span> <span data-ttu-id="e104b-126">要素の型を山かっこの内側で指定します。</span><span class="sxs-lookup"><span data-stu-id="e104b-126">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="e104b-127">この <xref:System.Collections.Generic.List%601> 型の重要な点は増減が可能で、要素を追加したり削除したりできることです。</span><span class="sxs-lookup"><span data-stu-id="e104b-127">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="e104b-128">`Main` メソッドの閉じかっこ `}` の前に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e104b-128">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="e104b-129">さらに 2 つの名前をリストの末尾に追加しました。</span><span class="sxs-lookup"><span data-stu-id="e104b-129">You've added two more names to the end of the list.</span></span> <span data-ttu-id="e104b-130">また、1 つを削除しました。</span><span class="sxs-lookup"><span data-stu-id="e104b-130">You've also removed one as well.</span></span> <span data-ttu-id="e104b-131">ファイルを保存し、「`dotnet run`」と入力して試します。</span><span class="sxs-lookup"><span data-stu-id="e104b-131">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="e104b-132"><xref:System.Collections.Generic.List%601> を使用すると、**インデックス**でも個々の項目を参照できます。</span><span class="sxs-lookup"><span data-stu-id="e104b-132">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="e104b-133">リスト名に続く `[` と `]` のトークンの間にインデックスを記述します。</span><span class="sxs-lookup"><span data-stu-id="e104b-133">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="e104b-134">C# では、初めのインデックスには 0 を使用します。</span><span class="sxs-lookup"><span data-stu-id="e104b-134">C# uses 0 for the first index.</span></span> <span data-ttu-id="e104b-135">追加したコードのすぐ下に次のコードを追加して試します。</span><span class="sxs-lookup"><span data-stu-id="e104b-135">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="e104b-136">リストの末尾を越えてインデックスにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="e104b-136">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="e104b-137">インデックスは 0 から始まるため、有効なインデックスの最大値はリスト内の項目の数より 1 小さくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e104b-137">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="e104b-138"><xref:System.Collections.Generic.List%601.Count%2A> プロパティを使用すれば、リストの長さを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e104b-138">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="e104b-139">次のコードを Main メソッドの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="e104b-139">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="e104b-140">ファイルを保存し、もう一度「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="e104b-140">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="e104b-141">リストを検索して並び替える</span><span class="sxs-lookup"><span data-stu-id="e104b-141">Search and sort lists</span></span>
<span data-ttu-id="e104b-142">サンプルでは比較的小さいリストを使用していますが、ご利用のアプリケーションでは、より多くの (場合によっては何千もの) 要素が含まれるリストを作成することもよくあるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="e104b-142">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="e104b-143">そうした大規模なコレクションの中から要素を見つけるには、別々の項目をリストで検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e104b-143">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="e104b-144"><xref:System.Collections.Generic.List%601.IndexOf%2A> メソッドは項目を検索し、その項目のインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="e104b-144">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="e104b-145">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e104b-145">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="e104b-146">同じように、リスト内の項目を並び替えできます。</span><span class="sxs-lookup"><span data-stu-id="e104b-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="e104b-147"><xref:System.Collections.Generic.List%601.Sort%2A> メソッドは、リスト内のすべての項目を正規順序 (文字列の場合はアルファベット順) で並び替えます。</span><span class="sxs-lookup"><span data-stu-id="e104b-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="e104b-148">`Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e104b-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="e104b-149">ファイルを保存し、「`dotnet run`」と入力してこの最新バージョンを試します。</span><span class="sxs-lookup"><span data-stu-id="e104b-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="e104b-150">次のセクションを開始する前に、現在のコードを別のメソッドに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="e104b-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="e104b-151">移動しておくと、新しい例で作業を開始するときに楽になります。</span><span class="sxs-lookup"><span data-stu-id="e104b-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="e104b-152">`Main` メソッドの名前を `WorkingWithStrings` に変更し、`WorkingWithStrings` を呼び出す新しい `Main` メソッドを記述します。</span><span class="sxs-lookup"><span data-stu-id="e104b-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="e104b-153">完成したコードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e104b-153">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="e104b-154">その他の型のリスト</span><span class="sxs-lookup"><span data-stu-id="e104b-154">Lists of other types</span></span>

<span data-ttu-id="e104b-155">ここまでは、リスト内で `string` 型を使用してきました。</span><span class="sxs-lookup"><span data-stu-id="e104b-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="e104b-156">別の型を使用して <xref:System.Collections.Generic.List%601> を作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="e104b-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="e104b-157">数値のセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="e104b-157">Let's build a set of numbers.</span></span> 

<span data-ttu-id="e104b-158">新しい `Main` メソッドの下部に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e104b-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="e104b-159">これにより整数のリストが作成され、最初の 2 つの整数が値 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e104b-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="e104b-160">これらは、数列の 1 つである*フィボナッチ数列*の最初の 2 つの値です。</span><span class="sxs-lookup"><span data-stu-id="e104b-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="e104b-161">次のフィボナッチ数はそれぞれ、その直前の 2 つの数値の合計を取得することによって得られます。</span><span class="sxs-lookup"><span data-stu-id="e104b-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="e104b-162">このコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e104b-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="e104b-163">ファイルを保存し、「`dotnet run`」と入力して結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="e104b-163">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="e104b-164">このセクションにだけ集中したいときは、`WorkingWithStrings();` を呼び出すコードはコメント アウトしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="e104b-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="e104b-165">`// WorkingWithStrings();` のように、呼び出しの前に `/` 文字を 2 つ記述します。</span><span class="sxs-lookup"><span data-stu-id="e104b-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="e104b-166">課題</span><span class="sxs-lookup"><span data-stu-id="e104b-166">Challenge</span></span>
<span data-ttu-id="e104b-167">このレッスンと以前のレッスンの中から、いくつかのレッスンの内容をまとめて理解できているかどうかを確認してみましょう。</span><span class="sxs-lookup"><span data-stu-id="e104b-167">See if you can put together some of the lessons from this and earlier lessons.</span></span> <span data-ttu-id="e104b-168">ここまでフィボナッチ数を使用して作成してきたコードを使ってください。</span><span class="sxs-lookup"><span data-stu-id="e104b-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="e104b-169">シーケンスの最初の 20 個の数を生成するコードを記述してみましょう。</span><span class="sxs-lookup"><span data-stu-id="e104b-169">Try and write the code to generate the first 20 numbers in the sequence.</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="e104b-170">課題完了</span><span class="sxs-lookup"><span data-stu-id="e104b-170">Complete challenge</span></span>

<span data-ttu-id="e104b-171">[GitHub にある完成したサンプル コード](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs)で、ソリューションの例を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e104b-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs)</span></span>

<span data-ttu-id="e104b-172">ループの繰り返しごとに、リストの最後の 2 つの整数を取得して合計し、その値をリストに追加しています。</span><span class="sxs-lookup"><span data-stu-id="e104b-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="e104b-173">このループは、20 個の項目がリストに追加されるまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="e104b-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="e104b-174">おつかれさまでした。リストについてのチュートリアルはこれで終了です。</span><span class="sxs-lookup"><span data-stu-id="e104b-174">Congratulations, you've completed the list tutorial.</span></span>

<span data-ttu-id="e104b-175">`List` 型の使用方法の詳細については、[.NET ガイド](../../standard/index.md)の[コレクション](../../standard/collections/index.md)に関するトピックで学習できます。</span><span class="sxs-lookup"><span data-stu-id="e104b-175">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="e104b-176">その他の多くのコレクション型についても学習できます。</span><span class="sxs-lookup"><span data-stu-id="e104b-176">You'll also learn about many other collection types.</span></span>
