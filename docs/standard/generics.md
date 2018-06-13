---
title: ジェネリック型 (ジェネリック) の概要
description: 実際のデータ型をいじらずにタイプ セーフなデータ構造を定義できるコード テンプレートとしてジェネリックがどのように機能するかを説明します。
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.openlocfilehash: ad6216998dff70ca7e36b52b374c5ffb9fd0cd45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575480"
---
# <a name="generic-types-generics-overview"></a><span data-ttu-id="f072f-103">ジェネリック型 (ジェネリック) の概要</span><span class="sxs-lookup"><span data-stu-id="f072f-103">Generic Types (Generics) Overview</span></span>

<span data-ttu-id="f072f-104">暗黙的か明示的かに関わらず、C# では常にジェネリックを使用します。</span><span class="sxs-lookup"><span data-stu-id="f072f-104">We use generics all the time in C#, whether implicitly or explicitly.</span></span> <span data-ttu-id="f072f-105">C# で LINQ を使用していると、IEnumerable<T> を操作することがあります。</span><span class="sxs-lookup"><span data-stu-id="f072f-105">When you use LINQ in C#, did you ever notice that you are working with IEnumerable<T>?</span></span> <span data-ttu-id="f072f-106">または、Entity Framework を使用してデータベースと通信するための "汎用リポジトリ" のオンライン サンプルでは、ほとんどのメソッドが IQueryable<T> を返すことに気付きます。</span><span class="sxs-lookup"><span data-stu-id="f072f-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="f072f-107">これらの例の **T** とは何で、なぜそこにあるのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="f072f-107">You may have wondered what the **T** is in these examples and why is it in there?</span></span>

<span data-ttu-id="f072f-108">.NET Framework 2.0 で最初に導入されたジェネリックには、C# 言語と共通言語ランタイム (CLR) の両方に関連する変更が含まれました。</span><span class="sxs-lookup"><span data-stu-id="f072f-108">First introduced to the .NET Framework 2.0, generics involved changes to both the C# language and the Common Language Runtime (CLR).</span></span> <span data-ttu-id="f072f-109">**ジェネリック**は本質的に "コード テンプレート" であり、開発者は実際のデータ型をいじらずに[タイプ セーフな](https://msdn.microsoft.com/library/hbzz1a9a.aspx)データ構造を定義できます。</span><span class="sxs-lookup"><span data-stu-id="f072f-109">**Generics** are essentially a "code template" that allows developers to define [type-safe](https://msdn.microsoft.com/library/hbzz1a9a.aspx) data structures without committing to an actual data type.</span></span> <span data-ttu-id="f072f-110">たとえば、`List<T>` は[ジェネリック コレクション](xref:System.Collections.Generic)であり、`List<int>`、`List<string>`、`List<Person>` などの任意の型で宣言および使用できます。</span><span class="sxs-lookup"><span data-stu-id="f072f-110">For example, `List<T>` is a [Generic Collection](xref:System.Collections.Generic) that can be declared and used with any type: `List<int>`, `List<string>`, `List<Person>`, etc.</span></span>

<span data-ttu-id="f072f-111">重点および</span><span class="sxs-lookup"><span data-stu-id="f072f-111">So, what’s the point?</span></span> <span data-ttu-id="f072f-112">ジェネリックの有用性を</span><span class="sxs-lookup"><span data-stu-id="f072f-112">Why are generics useful?</span></span> <span data-ttu-id="f072f-113">理解するためには、ジェネリックを追加する前と後の特定のクラスを調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f072f-113">In order to understand this, we need to take a look at a specific class before and after adding generics.</span></span> <span data-ttu-id="f072f-114">`ArrayList` を見てみます。</span><span class="sxs-lookup"><span data-stu-id="f072f-114">Let’s look at the `ArrayList`.</span></span> <span data-ttu-id="f072f-115">C# 1.0 では、`ArrayList` 要素は `object` 型でした。</span><span class="sxs-lookup"><span data-stu-id="f072f-115">In C# 1.0, the `ArrayList` elements were of type `object`.</span></span> <span data-ttu-id="f072f-116">これは、追加されたすべての要素は暗黙的に `object` に変換されることを意味します。リストから要素を読み取るときも同じです (この処理はそれぞれ、[ボックス化](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md)およびボックス化解除と呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="f072f-116">This meant that any element that was added was silently converted into an `object`; same thing happens on reading the elements from the list (this process is known as [boxing](../../docs/csharp/programming-guide/types/boxing-and-unboxing.md) and unboxing respectively).</span></span> <span data-ttu-id="f072f-117">ボックス化とボックス化解除はパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="f072f-117">Boxing and unboxing have an impact of performance.</span></span> <span data-ttu-id="f072f-118">そうはいっても、コンパイル時にリスト内のデータの実際の型を確認する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="f072f-118">More than that, however, there is no way to tell at compile time what is the actual type of the data in the list.</span></span> <span data-ttu-id="f072f-119">これは脆弱なコードを助長します。</span><span class="sxs-lookup"><span data-stu-id="f072f-119">This makes for some fragile code.</span></span> <span data-ttu-id="f072f-120">ジェネリックは、リストの各インスタンスに含まれるデータの型の追加情報を提供することによってこの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="f072f-120">Generics solve this problem by providing additional information the type of data each instance of list will contain.</span></span> <span data-ttu-id="f072f-121">簡単に言うと、`List<int>` には整数だけを追加でき、`List<Person>` には Persons だけを追加できます。</span><span class="sxs-lookup"><span data-stu-id="f072f-121">Put simply, you can only add integers to `List<int>` and only add Persons to `List<Person>`, etc.</span></span>

<span data-ttu-id="f072f-122">ジェネリックは、実行時または**具体化**にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f072f-122">Generics are also available at runtime, or **reified**.</span></span> <span data-ttu-id="f072f-123">これは、使用されているデータ構造の型をランタイムが認識し、より効率的メモリに格納できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f072f-123">This means the runtime knows what type of data structure you are using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="f072f-124">次に示すのは、実行時にデータ構造の型がわかるといかに効率的かということを示す小さなプログラムです。</span><span class="sxs-lookup"><span data-stu-id="f072f-124">Here is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

<span data-ttu-id="f072f-125">このプログラムの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f072f-125">This program yields the following output:</span></span>

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

<span data-ttu-id="f072f-126">最初にわかるのは、非ジェネリック リストよりジェネリック リストの方が並べ替えがはるかに高速であるということです。</span><span class="sxs-lookup"><span data-stu-id="f072f-126">The first thing you notice here is that sorting the generic list is significantly faster than for the non-generic list.</span></span> <span data-ttu-id="f072f-127">また、ジェネリック リストの型が具体的 ([System.Int32]) であるのに対して、非ジェネリック リストの型は一般的であることもわかります。</span><span class="sxs-lookup"><span data-stu-id="f072f-127">You might also notice that the type for the generic list is distinct ([System.Int32]) whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="f072f-128">ジェネリック `List<int>` の場合はランタイムはそれを int 型と認識してメモリの整数配列にリストの要素を格納できるのに対し、非ジェネリック `ArrayList` の場合はメモリではオブジェクト配列に格納されるので各リスト要素をオブジェクトとしてキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f072f-128">Because the runtime knows the generic `List<int>` is of type int, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element as an object as stored in an object array in memory.</span></span> <span data-ttu-id="f072f-129">この例にわかるように、余分なキャストに時間がかかり、リストの並べ替え速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="f072f-129">As shown through this example, the extra castings take up time and slow down the list sort.</span></span>

<span data-ttu-id="f072f-130">ジェネリックの型をランタイムが認識することの最後の利点は、デバッグ エクスペリエンスの向上です。</span><span class="sxs-lookup"><span data-stu-id="f072f-130">The last useful thing about the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="f072f-131">C# でジェネリックをデバッグすると、データ構造内の各要素の型がわかります。</span><span class="sxs-lookup"><span data-stu-id="f072f-131">When you are debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="f072f-132">ジェネリックでない場合は、各要素の型を知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="f072f-132">Without generics, you would have no idea what type each element was.</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="f072f-133">参考資料とリソース</span><span class="sxs-lookup"><span data-stu-id="f072f-133">Further reading and resources</span></span>

*   [<span data-ttu-id="f072f-134">C# のジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="f072f-134">An Introduction to C# Generics</span></span>](https://msdn.microsoft.com/library/ms379564.aspx)
*   [<span data-ttu-id="f072f-135">ジェネリック (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f072f-135">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
