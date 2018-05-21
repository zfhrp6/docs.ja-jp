---
title: LINQ の使用
description: このチュートリアルでは、LINQ を使用してシーケンスを生成し、LINQ クエリで使用するためのメソッドを作成し、先行評価と遅延評価を区別する方法を説明します。
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 17c294a372a05a05d3893fce7b3adc426c6305fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-linq"></a><span data-ttu-id="8d474-103">LINQ の使用</span><span class="sxs-lookup"><span data-stu-id="8d474-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="8d474-104">はじめに</span><span class="sxs-lookup"><span data-stu-id="8d474-104">Introduction</span></span>

<span data-ttu-id="8d474-105">このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。</span><span class="sxs-lookup"><span data-stu-id="8d474-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="8d474-106">内容は以下の通りです。</span><span class="sxs-lookup"><span data-stu-id="8d474-106">You’ll learn:</span></span>

*   <span data-ttu-id="8d474-107">LINQ を使用してシーケンスを生成する方法</span><span class="sxs-lookup"><span data-stu-id="8d474-107">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="8d474-108">LINQ クエリで簡単に使用できるメソッドを記述する方法</span><span class="sxs-lookup"><span data-stu-id="8d474-108">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="8d474-109">先行評価と遅延評価を区別する方法</span><span class="sxs-lookup"><span data-stu-id="8d474-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="8d474-110">これらの方法を、マジシャンの基本的スキルの 1 つである[ファロ― シャッフル](https://en.wikipedia.org/wiki/Faro_shuffle)を再現するアプリケーションを作成しながら学習していきます。</span><span class="sxs-lookup"><span data-stu-id="8d474-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="8d474-111">ファロ― シャッフルとは、簡単に言うと、カード デッキを正確に 2 等分し、双方のデッキから 1 枚ずつ交互に並ぶようにシャッフルして、元のデッキを並べ替えることです。</span><span class="sxs-lookup"><span data-stu-id="8d474-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="8d474-112">マジシャンがこの手法を使用するのは、シャッフルした後もそれぞれのカードの位置がわかり、カードの順序が繰り返しのパターンになるからです。</span><span class="sxs-lookup"><span data-stu-id="8d474-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="8d474-113">ここでは、データ シーケンスの操作として簡単に見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-113">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="8d474-114">これから作成するアプリケーションでは、カード デッキを構築し、シャッフルのシーケンスを実行し、その都度シーケンスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="8d474-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="8d474-115">また、更新された順序を元の順序と比較します。</span><span class="sxs-lookup"><span data-stu-id="8d474-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="8d474-116">このチュートリアルには、複数の手順があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="8d474-117">各手順の後に、アプリケーションを実行して進行状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="8d474-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="8d474-118">GitHub の dotnet/samples リポジトリでは、[完全版のサンプル](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq)を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d474-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="8d474-119">ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d474-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d474-120">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8d474-120">Prerequisites</span></span>

<span data-ttu-id="8d474-121">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="8d474-122">インストールの手順については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d474-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="8d474-123">このアプリケーションは、Windows、Ubuntu Linux、OS X または Docker コンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="8d474-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="8d474-124">お好みのコード エディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="8d474-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="8d474-125">次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="8d474-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="8d474-126">しかし、他の使い慣れたツールを使用しても構いません。</span><span class="sxs-lookup"><span data-stu-id="8d474-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="8d474-127">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="8d474-127">Create the Application</span></span>

<span data-ttu-id="8d474-128">最初に新しいアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d474-128">The first step is to create a new application.</span></span> <span data-ttu-id="8d474-129">コマンド プロンプトを開き、アプリケーション用の新しいディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d474-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="8d474-130">それを、現在のディレクトリとしてください。</span><span class="sxs-lookup"><span data-stu-id="8d474-130">Make that the current directory.</span></span> <span data-ttu-id="8d474-131">コマンド プロンプトで `dotnet new console` のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="8d474-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="8d474-132">これで、基本的な "Hello World" アプリケーションのスターター ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="8d474-133">C# を始めて使用する方向けに、[このチュートリアル](console-teleprompter.md)で C# プログラムの構造について説明しています。</span><span class="sxs-lookup"><span data-stu-id="8d474-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="8d474-134">そのチュートリアルを先に読んでから、ここに戻って LINQ の詳細について学ぶのも良いでしょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-134">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="8d474-135">データ セットの作成</span><span class="sxs-lookup"><span data-stu-id="8d474-135">Creating the Data Set</span></span>

<span data-ttu-id="8d474-136">まず、カードのデッキを作りましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-136">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="8d474-137">2 つのソースを持つ LINQ クエリを使用してデッキを作成します。ソースの 1 つは 4 種類のスート (スペードなどのマークのこと)、もう 1 つは 13 個の値です。</span><span class="sxs-lookup"><span data-stu-id="8d474-137">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="8d474-138">これらのソースを組み合わせて、52 枚のカード デッキを作ります。</span><span class="sxs-lookup"><span data-stu-id="8d474-138">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="8d474-139">`foreach` ループ内の `Console.WriteLine` ステートメントがカードを表示します。</span><span class="sxs-lookup"><span data-stu-id="8d474-139">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="8d474-140">クエリは以下の通りです。</span><span class="sxs-lookup"><span data-stu-id="8d474-140">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="8d474-141">複数の `from` 句は 1 つの `SelectMany` を生成し、これが、最初のシーケンス内の各要素と 2 番目のシーケンス内の各要素とを組み合わせた 1 つのシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8d474-141">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="8d474-142">ここでは順序が重要です。</span><span class="sxs-lookup"><span data-stu-id="8d474-142">The order is important for our purposes.</span></span> <span data-ttu-id="8d474-143">最初のソース シーケンス (Suits) 内の最初の要素は、2 番目のシーケンス (Values) のすべての要素と組み合わされます。</span><span class="sxs-lookup"><span data-stu-id="8d474-143">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="8d474-144">これで、最初のスートのカード 13 枚すべてが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-144">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="8d474-145">このプロセスを、最初のシーケンス (Suits) 内の各要素について繰り返します。</span><span class="sxs-lookup"><span data-stu-id="8d474-145">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="8d474-146">その結果、はじめにスート順に並んで、次に値の順に並んだカード デッキができます。</span><span class="sxs-lookup"><span data-stu-id="8d474-146">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="8d474-147">次に、Suits() メソッドおよび Ranks() メソッドをビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-147">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="8d474-148">列挙可能な文字列としてシーケンスを生成する、非常に単純な*反復子メソッド* のセットから始めましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-148">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

```csharp
static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="8d474-149">これら 2 つのメソッドは両方とも、`yield return` 構文を使用して実行中にシーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="8d474-149">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="8d474-150">コンパイラは `IEnumerable<T>` を実装するオブジェクトをビルドし、要求に応じて文字列のシーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="8d474-150">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="8d474-151">この時点で、作成したサンプルを実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="8d474-151">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="8d474-152">デッキにある 52 枚のカードがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-152">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="8d474-153">デバッガ―でこのサンプルを実行すると、`Suits()` メソッドと `Values()` メソッドがどのように実行されるか理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8d474-153">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="8d474-154">各シーケンス内の各文字列が必要な場合にのみ生成されることがよくわかります。</span><span class="sxs-lookup"><span data-stu-id="8d474-154">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![52 枚のカードをアプリケーションが書きだしているコンソール ウィンドウ](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="8d474-156">順序の操作</span><span class="sxs-lookup"><span data-stu-id="8d474-156">Manipulating the Order</span></span>

<span data-ttu-id="8d474-157">次に、シャッフルを実行できるユーティリティ メソッドをビルドしてみましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-157">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="8d474-158">最初の手順では、デッキを 2 つに分割します。</span><span class="sxs-lookup"><span data-stu-id="8d474-158">The first step is to split the deck in two.</span></span> <span data-ttu-id="8d474-159">LINQ API の一部である `Take()` メソッドと `Skip()` メソッドにより、この機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d474-159">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="8d474-160">シャッフル メソッドは標準ライブラリに存在しないので、独自に作成しなければいけません。</span><span class="sxs-lookup"><span data-stu-id="8d474-160">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="8d474-161">この新しいメソッドでは、LINQ ベースのプログラムで使用するいくつかの手法が示されます。メソッドの各部分を順序立てて説明します。</span><span class="sxs-lookup"><span data-stu-id="8d474-161">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="8d474-162">このメソッドの署名により、*拡張メソッド*が作成されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-162">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="8d474-163">拡張メソッドは、特殊な目的を持つ*静的メソッド*です。</span><span class="sxs-lookup"><span data-stu-id="8d474-163">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="8d474-164">メソッドの最初の引数に `this` 修飾子が追加されているのがわかります。</span><span class="sxs-lookup"><span data-stu-id="8d474-164">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="8d474-165">つまり、最初の引数の型のメンバー メソッドと同じように、メソッドを呼び出すということです。</span><span class="sxs-lookup"><span data-stu-id="8d474-165">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="8d474-166">拡張メソッドは `static` クラスの内部でしか宣言できないので、この機能のために `extensions` という新しい静的クラスを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-166">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="8d474-167">このチュートリアルでは、さらに拡張メソッドを追加していき、そのメソッドは同じクラスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-167">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="8d474-168">また、このメソッドの宣言は標準的な表現形式に従い、入力と出力の型が `IEnumerable<T>` となります。</span><span class="sxs-lookup"><span data-stu-id="8d474-168">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="8d474-169">これによって LINQ メソッドが連結され、より複雑なクエリを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8d474-169">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

<span data-ttu-id="8d474-170">要素をインターリーブし、オブジェクトを 1 つ作成しながら、両方のシーケンスを同時に列挙することになります。</span><span class="sxs-lookup"><span data-stu-id="8d474-170">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="8d474-171">2 つのシーケンスで動作する LINQ メソッドを作成するには、`IEnumerable` がどのように動作するかを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-171">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="8d474-172">`IEnumerable` インターフェイスには `GetEnumerator()` のメソッドが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="8d474-172">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="8d474-173">`GetEnumerator()` によって返されるオブジェクトには、次の要素に移動するメソッドと、シーケンス内の現在の要素を取得するプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8d474-173">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="8d474-174">これら 2 つのメンバーを使用して、コレクションを列挙し、要素を返します。</span><span class="sxs-lookup"><span data-stu-id="8d474-174">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="8d474-175">このインターリーブ メソッドは反復子メソッドになるので、コレクションを作成してそのコレクションを返す代わりに、上記の `yield return` 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d474-175">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="8d474-176">そのメソッドの実装を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="8d474-176">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="8d474-177">このメソッドが作成できたので、`Main` メソッドに戻り、デッキを 1 回シャッフルします。</span><span class="sxs-lookup"><span data-stu-id="8d474-177">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="8d474-178">比較</span><span class="sxs-lookup"><span data-stu-id="8d474-178">Comparisons</span></span>

<span data-ttu-id="8d474-179">デッキを元の順序に戻すまでにシャッフルが何回必要かを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-179">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="8d474-180">2 つのシーケンスが等しいかどうかを判断するメソッドを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-180">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="8d474-181">そのメソッドを記述したら、デッキをループでシャッフルするコードを配置し、どの時点で元の順序に戻るかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-181">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="8d474-182">2 つのシーケンスが等しいかどうかを判断するメソッドの記述は簡単です。</span><span class="sxs-lookup"><span data-stu-id="8d474-182">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="8d474-183">デッキのシャッフル用に記述したメソッドと似た構造です。</span><span class="sxs-lookup"><span data-stu-id="8d474-183">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="8d474-184">今回に限り、各要素を yield return するのではなく、各シーケンスの一致する要素を比較します。</span><span class="sxs-lookup"><span data-stu-id="8d474-184">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="8d474-185">シーケンス全体が列挙されている場合、各要素が一致すれば、シーケンスは同じです。</span><span class="sxs-lookup"><span data-stu-id="8d474-185">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="8d474-186">これは 2 つ目の LINQ の表現形式、ターミナル メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="8d474-186">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="8d474-187">これらは、シーケンスを入力として受け取り (この場合 2 つのシーケンス)、単一のスカラー値を返します。</span><span class="sxs-lookup"><span data-stu-id="8d474-187">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="8d474-188">これらのメソッドが使用される場合は常に、クエリの最後のメソッドとなります。</span><span class="sxs-lookup"><span data-stu-id="8d474-188">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="8d474-189">(ターミナル メソッドという名前なのはそのためです)。</span><span class="sxs-lookup"><span data-stu-id="8d474-189">(Hence the name).</span></span> 

<span data-ttu-id="8d474-190">これは、デッキが元の順序に戻るタイミングの判定に使用すると、どのように動作するかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="8d474-190">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="8d474-191">ループ内にシャッフルのコードを配置し、`SequenceEquals()` メソッドを適用して、シーケンスが元の順序に戻った時点で停止します。</span><span class="sxs-lookup"><span data-stu-id="8d474-191">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="8d474-192">シーケンスではなく単一の値を返すため、常にクエリ内の最後のメソッドになることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8d474-192">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

<span data-ttu-id="8d474-193">サンプルを実行して、8 回反復して元の構成に戻るまで、デッキがシャッフルごとにどのように配置されるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d474-193">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="8d474-194">最適化</span><span class="sxs-lookup"><span data-stu-id="8d474-194">Optimizations</span></span>

<span data-ttu-id="8d474-195">ここまでで構築したサンプルは、*イン シャッフル* (一番上と一番下のカードが毎回同じになること) を実行するものです。</span><span class="sxs-lookup"><span data-stu-id="8d474-195">The sample you've built so far executes an *in shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="8d474-196">ここで 1 つ変更を加え、*アウト シャッフル* (52 枚のカードすべてが位置を変えること) を実行しましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-196">Let's make one change, and run an *out shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="8d474-197">アウト シャッフルでは、下半分の一番上のカードが、デッキの最上部に来るように、デッキをインターウィーブします。</span><span class="sxs-lookup"><span data-stu-id="8d474-197">For an out shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="8d474-198">つまり、上半分の一番下のカードがデッキの最下部のカードになります。</span><span class="sxs-lookup"><span data-stu-id="8d474-198">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="8d474-199">これは 1 行だけの変更です。</span><span class="sxs-lookup"><span data-stu-id="8d474-199">That's just a one line change.</span></span> <span data-ttu-id="8d474-200">シャッフルの呼び出しを更新して、デッキの上半分と下半分の順序を変更します。</span><span class="sxs-lookup"><span data-stu-id="8d474-200">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="8d474-201">プログラムを再実行すると、デッキが元の順序に戻るのに反復が 52 回行われることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8d474-201">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="8d474-202">プログラムを実行し続けると、著しくパフォーマンスが低下することがわかります。</span><span class="sxs-lookup"><span data-stu-id="8d474-202">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="8d474-203">これには多くの理由があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-203">There are a number of reasons for this.</span></span> <span data-ttu-id="8d474-204">主な原因の 1 つを見ていきましょう。*遅延評価*の非効率的な使用です。</span><span class="sxs-lookup"><span data-stu-id="8d474-204">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="8d474-205">LINQ クエリが遅延して評価されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-205">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="8d474-206">シーケンスは、要素が要求された場合にのみ生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-206">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="8d474-207">通常、これは LINQ の利点です。</span><span class="sxs-lookup"><span data-stu-id="8d474-207">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="8d474-208">しかし、このプログラムのような使い方をする場合、実行時間が急激に増加する要因となります。</span><span class="sxs-lookup"><span data-stu-id="8d474-208">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="8d474-209">元のデッキは LINQ クエリを使用して生成されました。</span><span class="sxs-lookup"><span data-stu-id="8d474-209">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="8d474-210">毎回のシャッフルは、直前のデッキに LINQ クエリを 3 回実行することによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-210">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="8d474-211">これらはすべて遅延実行されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-211">All these are performed lazily.</span></span> <span data-ttu-id="8d474-212">つまり、シーケンスが要求されるたびに再度実行されるということです。</span><span class="sxs-lookup"><span data-stu-id="8d474-212">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="8d474-213">52 回反復されるまでに、元のデッキを何度も何度も再生成しているのです。</span><span class="sxs-lookup"><span data-stu-id="8d474-213">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="8d474-214">ログを記述してこの動作を示しましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-214">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="8d474-215">その次に修正します。</span><span class="sxs-lookup"><span data-stu-id="8d474-215">Then, you'll fix it.</span></span>

<span data-ttu-id="8d474-216">次のログ メソッドは、どんなクエリにも追加して、クエリが実行されたことをマークすることができます。</span><span class="sxs-lookup"><span data-stu-id="8d474-216">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="8d474-217">次に、各クエリの定義をログ メッセージでインストルメントします。</span><span class="sxs-lookup"><span data-stu-id="8d474-217">Next, instrument the definition of each query with a log message:</span></span>

```csharp
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
            .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
            .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="8d474-218">クエリにアクセスするたびにログをとるわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8d474-218">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="8d474-219">元のクエリを作成する場合にのみログをとります。</span><span class="sxs-lookup"><span data-stu-id="8d474-219">You log only when you create the original query.</span></span> <span data-ttu-id="8d474-220">プログラムの実行にはまだ時間がかかりますが、これで理由がわかるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8d474-220">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="8d474-221">ログを有効にしたままアウト シャッフルを実行すると時間がかかりすぎると感じる場合は、イン シャッフルに戻してください。</span><span class="sxs-lookup"><span data-stu-id="8d474-221">If you run out of patience running the outer shuffle with logging turned on, switch back to the inner shuffle.</span></span> <span data-ttu-id="8d474-222">それでも遅延評価の影響はわかります。</span><span class="sxs-lookup"><span data-stu-id="8d474-222">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="8d474-223">1 回の実行で、すべての値とスートの生成を含めてクエリを 2592 回実行します。</span><span class="sxs-lookup"><span data-stu-id="8d474-223">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="8d474-224">このプログラムを更新すると、このようにたくさんの実行をせずに簡単に済ませることができます。</span><span class="sxs-lookup"><span data-stu-id="8d474-224">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="8d474-225">LINQ メソッドには `ToArray()` および `ToList()` があり、これらはクエリを実行させ、その結果をそれぞれ配列またはリストに格納するものです。</span><span class="sxs-lookup"><span data-stu-id="8d474-225">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="8d474-226">ソース クエリを再実行するのではなく、クエリのデータ結果をキャッシュする場合に、これらのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8d474-226">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="8d474-227">カード デッキを生成するクエリに `ToArray()` の呼び出しを追加して、クエリを再実行します。</span><span class="sxs-lookup"><span data-stu-id="8d474-227">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="8d474-228">再実行すると、イン シャッフルが 30 回のクエリまでに減ります。</span><span class="sxs-lookup"><span data-stu-id="8d474-228">Run again, and the inner shuffle is down to 30 queries.</span></span> <span data-ttu-id="8d474-229">アウト シャッフルで再実行しても、同様の改善がみられます。</span><span class="sxs-lookup"><span data-stu-id="8d474-229">Run again with the outer shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="8d474-230">(クエリ実行は 162 回になります)。</span><span class="sxs-lookup"><span data-stu-id="8d474-230">(It now executes 162 queries).</span></span>

<span data-ttu-id="8d474-231">この例をもとに、クエリはすべて先行評価で実行すべきだと誤解しないでください。</span><span class="sxs-lookup"><span data-stu-id="8d474-231">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="8d474-232">この例は、遅延評価がパフォーマンス問題を引き起こすユース ケースに着目するように設計されたものです。</span><span class="sxs-lookup"><span data-stu-id="8d474-232">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="8d474-233">これは、カード デッキの新しい並びが毎回、直前の並びをもとに作成されるからです。</span><span class="sxs-lookup"><span data-stu-id="8d474-233">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="8d474-234">遅延評価を使用すると、`startingDeck` を作成したコードを実行するときでさえも、新しいデッキ構成が毎回最初のデッキから作成されることになります。</span><span class="sxs-lookup"><span data-stu-id="8d474-234">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="8d474-235">これでは、余分な作業が多く発生してしまいます。</span><span class="sxs-lookup"><span data-stu-id="8d474-235">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="8d474-236">実際には、先行評価を使用すると効率的に動作するアルゴリズムもあれば、遅延評価を使用したほうがよいアルゴリズムもあります。</span><span class="sxs-lookup"><span data-stu-id="8d474-236">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="8d474-237">(一般に、データ ソースがデータベース エンジンのように個別のプロセスである場合は、遅延評価のほうがはるかに適しています。</span><span class="sxs-lookup"><span data-stu-id="8d474-237">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="8d474-238">このような場合、遅延評価では、より複雑なクエリの実行がデータベース処理に対して 1 往復だけ可能になります。)LINQ では遅延評価と先行評価の両方が可能です。</span><span class="sxs-lookup"><span data-stu-id="8d474-238">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="8d474-239">検討し最適な方法を選んでください。</span><span class="sxs-lookup"><span data-stu-id="8d474-239">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="8d474-240">新機能の準備</span><span class="sxs-lookup"><span data-stu-id="8d474-240">Preparing for New Features</span></span>

<span data-ttu-id="8d474-241">このサンプルで記述したコードは、目的を果たすために作成された単純なプロトタイプの例です。</span><span class="sxs-lookup"><span data-stu-id="8d474-241">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="8d474-242">問題の範囲を調査するのに優れた方法であり、多くの機能ではこれが最適な恒久策となりえます。</span><span class="sxs-lookup"><span data-stu-id="8d474-242">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="8d474-243">カードに*匿名型*を利用したので、それぞれのカードは文字列で表されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-243">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="8d474-244">生産性の観点から、*匿名型*には多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-244">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="8d474-245">記憶域を表すクラスを自分で定義する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8d474-245">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="8d474-246">型は、コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="8d474-246">The compiler generates the type for you.</span></span> <span data-ttu-id="8d474-247">コンパイラによって生成された型では、単純なデータ オブジェクトのベスト プラクティスを多く使用します。</span><span class="sxs-lookup"><span data-stu-id="8d474-247">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="8d474-248">この型は*不変*で、構築後はどのプロパティも変更することができないことになります。</span><span class="sxs-lookup"><span data-stu-id="8d474-248">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="8d474-249">匿名型はアセンブリ内のものであるため、そのアセンブリのパブリック API の一部としては認識されません。</span><span class="sxs-lookup"><span data-stu-id="8d474-249">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="8d474-250">匿名型にはまた、それぞれの値を使用して書式設定された文字列を返す `ToString()` メソッドのオーバーライドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8d474-250">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="8d474-251">匿名型には欠点もあります。</span><span class="sxs-lookup"><span data-stu-id="8d474-251">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="8d474-252">アクセス可能な名前がないので、戻り値または引数として使用することができません。</span><span class="sxs-lookup"><span data-stu-id="8d474-252">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="8d474-253">これらの匿名型を使用した上記のメソッドはすべて、ジェネリック メソッドであることがわかります。</span><span class="sxs-lookup"><span data-stu-id="8d474-253">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="8d474-254">アプリケーションがより多くの機能を持つようになると、`ToString()` オーバーライドは望ましくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-254">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="8d474-255">このサンプルではまた、各カードのスートとランクに文字列を使用しています。</span><span class="sxs-lookup"><span data-stu-id="8d474-255">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="8d474-256">これはかなりオープン エンドな状態です。</span><span class="sxs-lookup"><span data-stu-id="8d474-256">That's quite open ended.</span></span> <span data-ttu-id="8d474-257">C# 型システムでは、こうした値に `enum` 型を利用することで、より優れたコードを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="8d474-257">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="8d474-258">スートから始めましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-258">Start with the suits.</span></span> <span data-ttu-id="8d474-259">ここが `enum` の使用に最適なタイミングです。</span><span class="sxs-lookup"><span data-stu-id="8d474-259">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="8d474-260">`Suits()` メソッドは、型と実装も変更します。</span><span class="sxs-lookup"><span data-stu-id="8d474-260">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="8d474-261">次に、カードのランクについても同じ変更を行います。</span><span class="sxs-lookup"><span data-stu-id="8d474-261">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="8d474-262">それらを生成するメソッドについても同様です。</span><span class="sxs-lookup"><span data-stu-id="8d474-262">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="8d474-263">最後のクリーンアップとして、匿名型を使うのではなく、カードを表す型を作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="8d474-263">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="8d474-264">匿名型は軽量でローカルな型に適していますが、ここではカード ゲームをすることに焦点を置いています。</span><span class="sxs-lookup"><span data-stu-id="8d474-264">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="8d474-265">ですから、具象型を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d474-265">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="8d474-266">この型は、コンストラクターに設定されている*自動実装された読み取り専用プロパティ*が使用しているため、変更することができません。</span><span class="sxs-lookup"><span data-stu-id="8d474-266">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="8d474-267">また、[文字列補間](../language-reference/tokens/interpolated.md)機能を活用していて、文字列出力の書式設定が簡単です。</span><span class="sxs-lookup"><span data-stu-id="8d474-267">It also makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature that makes it easier to format string output.</span></span>

<span data-ttu-id="8d474-268">最初のデッキを生成するクエリを更新して、新しい型を使用します。</span><span class="sxs-lookup"><span data-stu-id="8d474-268">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="8d474-269">コンパイルして再実行します。</span><span class="sxs-lookup"><span data-stu-id="8d474-269">Compile and run again.</span></span> <span data-ttu-id="8d474-270">出力が少し読みやすくなり、コードが少し明確になってより簡単に拡張できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8d474-270">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="8d474-271">まとめ</span><span class="sxs-lookup"><span data-stu-id="8d474-271">Conclusion</span></span>

<span data-ttu-id="8d474-272">このサンプルでは、LINQ で使用されるいくつかのメソッドと、LINQ が有効なコードで簡単に使えるメソッドの作成方法を紹介しました。</span><span class="sxs-lookup"><span data-stu-id="8d474-272">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="8d474-273">さらに、遅延評価と先行評価の違いを示し、どちらを選ぶかによってパフォーマンスにどのような影響があるかを説明しました。</span><span class="sxs-lookup"><span data-stu-id="8d474-273">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="8d474-274">マジシャンのテクニックについて少し学びました。</span><span class="sxs-lookup"><span data-stu-id="8d474-274">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="8d474-275">マジシャンは、ファロー シャッフルを使ってデッキでの各カードの位置をコントロールします。</span><span class="sxs-lookup"><span data-stu-id="8d474-275">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="8d474-276">中には、マジシャンが観客にデッキの一番上にカードを置いてもらい、そのカードの行き先を把握しながら何回かシャッフルするトリックもあります。</span><span class="sxs-lookup"><span data-stu-id="8d474-276">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="8d474-277">デッキを特定の方法で置いておく必要があるトリックもあります。</span><span class="sxs-lookup"><span data-stu-id="8d474-277">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="8d474-278">こうしたトリックの場合は、デッキを事前にセットしておきます。</span><span class="sxs-lookup"><span data-stu-id="8d474-278">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="8d474-279">次にデッキをイン シャッフルの形で 5 回シャッフルします。</span><span class="sxs-lookup"><span data-stu-id="8d474-279">Then she will shuffle the deck 5 times using an inner shuffle.</span></span> <span data-ttu-id="8d474-280">ステージで、マジシャンはランダムに並べ替えられたように見えるデッキをさらに 3 回シャッフルして、思い通りのようにデッキをセットするのです。</span><span class="sxs-lookup"><span data-stu-id="8d474-280">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
