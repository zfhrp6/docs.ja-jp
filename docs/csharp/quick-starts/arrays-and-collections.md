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
# <a name="c-quick-start-collections"></a><span data-ttu-id="fcecb-104">C# の場合は、クイック スタート: コレクション</span><span class="sxs-lookup"><span data-stu-id="fcecb-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="fcecb-105">このチュートリアルでは、c# 言語の基本的な概要については、<xref:System.Collections.Generic.List%601>クラスです。</span><span class="sxs-lookup"><span data-stu-id="fcecb-105">This tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

## <a name="a-simple-list-example"></a><span data-ttu-id="fcecb-106">単純なリストの使用例です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-106">A simple list example.</span></span>

> [!NOTE]
> <span data-ttu-id="fcecb-107">記述したコードから開始する場合は[dot.net](https://dot.net/)、このセクションで記述されたコードがあります。</span><span class="sxs-lookup"><span data-stu-id="fcecb-107">If you're starting from the code you wrote in [dot.net](https://dot.net/), you already have the code written in this section.</span></span> <span data-ttu-id="fcecb-108">ジャンプ[一覧の内容を変更](#modify-list-contents)です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-108">Jump to [Modify list contents](#modify-list-contents).</span></span>

<span data-ttu-id="fcecb-109">このレッスンでは、オンラインのクイック スタートが終了したら、インストールされている前提としています、 [.NET Core SDK](http://dot.net/core)と[Visual Studio Code](https://code.visualstudio.com/)です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-109">This lesson assumes you've finished the online quick starts, and you've installed the [.NET Core SDK](http://dot.net/core) and [Visual Studio Code](https://code.visualstudio.com/).</span></span> 

<span data-ttu-id="fcecb-110">という名前のディレクトリを作成する**リスト クイック スタート**です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="fcecb-111">いることを現在のディレクトリと実行`dotnet new console`です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-111">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="fcecb-112">開いている**Program.cs**好みのエディターと置換、既存のコードを次に。</span><span class="sxs-lookup"><span data-stu-id="fcecb-112">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="fcecb-113">置き換える`<name>`名に置き換えています。</span><span class="sxs-lookup"><span data-stu-id="fcecb-113">Replace `<name>` with your name.</span></span> <span data-ttu-id="fcecb-114">保存**Program.cs**です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-114">Save **Program.cs**.</span></span> <span data-ttu-id="fcecb-115">型`dotnet run`コンソール ウィンドウしてみてください。</span><span class="sxs-lookup"><span data-stu-id="fcecb-115">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="fcecb-116">だけ文字列のリストを作成、そのリストに 3 つの名前を追加してすべて大文字で名前を印刷します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-116">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="fcecb-117">一覧をループする以前のクイック スタートで学習した概念を使用しています。</span><span class="sxs-lookup"><span data-stu-id="fcecb-117">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="fcecb-118">名前を表示するコードでは、使用**補間文字列**です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-118">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="fcecb-119">前に指定するときに、`string`で、`$`文字、文字列の宣言での c# コードを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="fcecb-119">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="fcecb-120">実際の文字列を生成値に c# コードを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fcecb-120">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="fcecb-121">この例では置き換えられます、`{name.ToUpper()}`各名前を持つために、変換英大文字、呼び出したのと、<xref:System.String.ToUpper%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fcecb-121">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="fcecb-122">みましょうの探索してください。</span><span class="sxs-lookup"><span data-stu-id="fcecb-122">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="fcecb-123">変更内容の一覧表示</span><span class="sxs-lookup"><span data-stu-id="fcecb-123">Modify list contents</span></span>

<span data-ttu-id="fcecb-124">使用して作成したコレクション、<xref:System.Collections.Generic.List%601>型です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-124">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="fcecb-125">この型は、要素のシーケンスを格納します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-125">This type stores sequences of elements.</span></span> <span data-ttu-id="fcecb-126">山かっこ間の要素の種類を指定するとします。</span><span class="sxs-lookup"><span data-stu-id="fcecb-126">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="fcecb-127">この 1 つの重要な側面<xref:System.Collections.Generic.List%601>型は、拡大または縮小、でく要素を追加または削除できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="fcecb-127">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="fcecb-128">終了する前にこのコードを追加`}`で、`Main`メソッド。</span><span class="sxs-lookup"><span data-stu-id="fcecb-128">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="fcecb-129">2 つ以上の名前は、リストの末尾に追加されました。</span><span class="sxs-lookup"><span data-stu-id="fcecb-129">You've added two more names to the end of the list.</span></span> <span data-ttu-id="fcecb-130">したも 1 つも削除します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-130">You've also removed one as well.</span></span> <span data-ttu-id="fcecb-131">ファイル、および種類保存`dotnet run`してみてください。</span><span class="sxs-lookup"><span data-stu-id="fcecb-131">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="fcecb-132"><xref:System.Collections.Generic.List%601>個々 のアイテムを参照することができます**インデックス**もします。</span><span class="sxs-lookup"><span data-stu-id="fcecb-132">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="fcecb-133">間でインデックスを配置する`[`と`]`リスト名の後にトークンです。</span><span class="sxs-lookup"><span data-stu-id="fcecb-133">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="fcecb-134">C# の場合 0 を最初のインデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-134">C# uses 0 for the first index.</span></span> <span data-ttu-id="fcecb-135">追加したコードのすぐ下には、このコードを追加して、それを再試行してください。</span><span class="sxs-lookup"><span data-stu-id="fcecb-135">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="fcecb-136">リストの末尾を越えるインデックスにアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="fcecb-136">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="fcecb-137">インデックスは、有効なインデックスの最大値であるため、0 から始まりますリスト内の項目の数よりも小さいです。</span><span class="sxs-lookup"><span data-stu-id="fcecb-137">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="fcecb-138">一覧がどのくらいの期間を使用しているかをチェックすることができます、<xref:System.Collections.Generic.List%601.Count%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="fcecb-138">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="fcecb-139">Main メソッドの最後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-139">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="fcecb-140">ファイル、および種類保存`dotnet run`結果を表示するには、もう一度です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-140">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="fcecb-141">検索および並べ替えリスト</span><span class="sxs-lookup"><span data-stu-id="fcecb-141">Search and sort lists</span></span>
<span data-ttu-id="fcecb-142">サンプルは、比較的小さいリストを使用してですが、アプリケーションで、多くの詳細要素と、数千に達しますのリストを作成ことが多くの場合、可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fcecb-142">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="fcecb-143">これらの大規模なコレクション内の要素を検索、さまざまなアイテムの一覧を検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fcecb-143">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="fcecb-144"><xref:System.Collections.Generic.List%601.IndexOf%2A>メソッド アイテムを検索し、項目のインデックスを返します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-144">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="fcecb-145">下に次のコードを追加、`Main`メソッド。</span><span class="sxs-lookup"><span data-stu-id="fcecb-145">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="fcecb-146">リスト内の項目も並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="fcecb-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="fcecb-147"><xref:System.Collections.Generic.List%601.Sort%2A>メソッド (文字列) の場合にアルファベット順に、通常の順序で一覧のすべての項目を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="fcecb-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="fcecb-148">下に次のコードを追加、`Main`メソッド。</span><span class="sxs-lookup"><span data-stu-id="fcecb-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="fcecb-149">ファイルの保存と型`dotnet run`を最新のバージョンを実行してください。</span><span class="sxs-lookup"><span data-stu-id="fcecb-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="fcecb-150">次のセクションを開始する前に別のメソッドに現在コードに移動してみましょう。</span><span class="sxs-lookup"><span data-stu-id="fcecb-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="fcecb-151">これにより新しい例の操作を開始します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="fcecb-152">名前を変更、`Main`メソッドを`WorkingWithStrings`と新しい書き込み`Main`メソッドを呼び出す`WorkingWithStrings`です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="fcecb-153">完了したら、コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fcecb-153">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="fcecb-154">その他の種類の一覧</span><span class="sxs-lookup"><span data-stu-id="fcecb-154">Lists of other types</span></span>

<span data-ttu-id="fcecb-155">使用した、`string`これまでのリストを入力します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="fcecb-156">こちらから、<xref:System.Collections.Generic.List%601>別の種類を使用します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="fcecb-157">数値のセットを構築してみましょう。</span><span class="sxs-lookup"><span data-stu-id="fcecb-157">Let's build a set of numbers.</span></span> 

<span data-ttu-id="fcecb-158">新しいの下部に次のコードを追加`Main`メソッド。</span><span class="sxs-lookup"><span data-stu-id="fcecb-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="fcecb-159">整数のリストを作成し、最初の 2 つの整数を値 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="fcecb-160">これは、値は、最初の 2 つの*フィボナッチ シーケンス*一連の数値。</span><span class="sxs-lookup"><span data-stu-id="fcecb-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="fcecb-161">各次のフィボナッチ数は、前の 2 つの数値の合計を取得して検出されます。</span><span class="sxs-lookup"><span data-stu-id="fcecb-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="fcecb-162">このコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="fcecb-163">ファイルの保存と型`dotnet run`結果を確認します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-163">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="fcecb-164">このセクションでを重点的にすることができますをコメント アウトを呼び出すコード`WorkingWithStrings();`です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="fcecb-165">2 つの配置だけ`/`次のように、呼び出しの前に文字:`// WorkingWithStrings();`です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="fcecb-166">チャレンジ</span><span class="sxs-lookup"><span data-stu-id="fcecb-166">Challenge</span></span>
<span data-ttu-id="fcecb-167">一緒に配置できるかどうかを参照してください。 ここから、前のレッスンの一部のレッスンです。</span><span class="sxs-lookup"><span data-stu-id="fcecb-167">See if you can put together some of the lessons from this and earlier lessons.</span></span> <span data-ttu-id="fcecb-168">新機能を作成したらこれまでフィボナッチの数列を展開します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="fcecb-169">シーケンスの最初の 20 個の番号を生成するコードを記述してください。</span><span class="sxs-lookup"><span data-stu-id="fcecb-169">Try and write the code to generate the first 20 numbers in the sequence.</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="fcecb-170">完全なチャレンジ</span><span class="sxs-lookup"><span data-stu-id="fcecb-170">Complete challenge</span></span>

<span data-ttu-id="fcecb-171">ソリューションの例を確認できます[GitHub の完成後のサンプル コードを見る](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs)</span><span class="sxs-lookup"><span data-stu-id="fcecb-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs)</span></span>

<span data-ttu-id="fcecb-172">一覧にその値を追加、集計、および、ループの反復ごとの最後の 2 つの整数の一覧でに移動しています。</span><span class="sxs-lookup"><span data-stu-id="fcecb-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="fcecb-173">ループは、20 個のアイテムを一覧に追加するまで繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="fcecb-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="fcecb-174">これで、一覧のチュートリアルを完了しました。</span><span class="sxs-lookup"><span data-stu-id="fcecb-174">Congratulations, you've completed the list tutorial.</span></span>

<span data-ttu-id="fcecb-175">作業方法について学習することができます、`List`に入力、 [.NET ガイド](../../standard/index.md)に関するトピック[コレクション](../../standard/collections/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="fcecb-175">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="fcecb-176">その他の多くのコレクション型についても学習します。</span><span class="sxs-lookup"><span data-stu-id="fcecb-176">You'll also learn about many other collection types.</span></span>
