---
title: "ジェネリック型 (ジェネリック) の概要"
description: "実際のデータ型をいじらずにタイプ セーフなデータ構造を定義できるコード テンプレートとしてジェネリックがどのように機能するかを説明します。"
keywords: .NET, .NET Core
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.openlocfilehash: 08b8de2fe17a0032a1c1180667f39b1d6ce0feb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="generic-types-generics-overview"></a><span data-ttu-id="3f56e-104">ジェネリック型 (ジェネリック) の概要</span><span class="sxs-lookup"><span data-stu-id="3f56e-104">Generic Types (Generics) Overview</span></span>

<span data-ttu-id="3f56e-105">暗黙的か明示的かに関わらず、C# では常にジェネリックを使用します。</span><span class="sxs-lookup"><span data-stu-id="3f56e-105">We use generics all the time in C#, whether implicitly or explicitly.</span></span> <span data-ttu-id="3f56e-106">C# で LINQ を使用していると、IEnumerable<T> を操作することがあります。</span><span class="sxs-lookup"><span data-stu-id="3f56e-106">When you use LINQ in C#, did you ever notice that you are working with IEnumerable<T>?</span></span> <span data-ttu-id="3f56e-107">または、Entity Framework を使用してデータベースと通信するための "汎用リポジトリ" のオンライン サンプルでは、ほとんどのメソッドが IQueryable<T> を返すことに気付きます。</span><span class="sxs-lookup"><span data-stu-id="3f56e-107">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="3f56e-108">これらの例の **T** とは何で、なぜそこにあるのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="3f56e-108">You may have wondered what the **T** is in these examples and why is it in there?</span></span>

<span data-ttu-id="3f56e-109">.NET Framework 2.0 で最初に導入されたジェネリックには、C# 言語と共通言語ランタイム (CLR) の両方に関連する変更が含まれました。</span><span class="sxs-lookup"><span data-stu-id="3f56e-109">First introduced to the .NET Framework 2.0, generics involved changes to both the C# language and the Common Language Runtime (CLR).</span></span> <span data-ttu-id="3f56e-110">**ジェネリック**は本質的に "コード テンプレート" であり、開発者は実際のデータ型をいじらずに[タイプ セーフな](https://msdn.microsoft.com/library/hbzz1a9a.aspx)データ構造を定義できます。</span><span class="sxs-lookup"><span data-stu-id="3f56e-110">**Generics** are essentially a "code template" that allows developers to define [type-safe](https://msdn.microsoft.com/library/hbzz1a9a.aspx) data structures without committing to an actual data type.</span></span> <span data-ttu-id="3f56e-111">たとえば、`List<T>` は[ジェネリック コレクション](xref:System.Collections.Generic)であり、`List<int>`、`List<string>`、`List<Person>` などの任意の型で宣言および使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f56e-111">For example, `List<T>` is a [Generic Collection](xref:System.Collections.Generic) that can be declared and used with any type: `List<int>`, `List<string>`, `List<Person>`, etc.</span></span>

<span data-ttu-id="3f56e-112">重点および</span><span class="sxs-lookup"><span data-stu-id="3f56e-112">So, what’s the point?</span></span> <span data-ttu-id="3f56e-113">ジェネリックの有用性を</span><span class="sxs-lookup"><span data-stu-id="3f56e-113">Why are generics useful?</span></span> <span data-ttu-id="3f56e-114">理解するためには、ジェネリックを追加する前と後の特定のクラスを調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f56e-114">In order to understand this, we need to take a look at a specific class before and after adding generics.</span></span> <span data-ttu-id="3f56e-115">`ArrayList` を見てみます。</span><span class="sxs-lookup"><span data-stu-id="3f56e-115">Let’s look at the `ArrayList`.</span></span> <span data-ttu-id="3f56e-116">C# 1.0 では、`ArrayList` 要素は `object` 型でした。</span><span class="sxs-lookup"><span data-stu-id="3f56e-116">In C# 1.0, the `ArrayList` elements were of type `object`.</span></span> <span data-ttu-id="3f56e-117">これは、追加されたすべての要素は暗黙的に `object` に変換されることを意味します。リストから要素を読み取るときも同じです (この処理はそれぞれ、[ボックス化](https://msdn.microsoft.com/library/yz2be5wk.aspx)およびボックス化解除と呼ばれます)。</span><span class="sxs-lookup"><span data-stu-id="3f56e-117">This meant that any element that was added was silently converted into an `object`; same thing happens on reading the elements from the list (this process is known as [boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) and unboxing respectively).</span></span> <span data-ttu-id="3f56e-118">ボックス化とボックス化解除はパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="3f56e-118">Boxing and unboxing have an impact of performance.</span></span> <span data-ttu-id="3f56e-119">そうはいっても、コンパイル時にリスト内のデータの実際の型を確認する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="3f56e-119">More than that, however, there is no way to tell at compile time what is the actual type of the data in the list.</span></span> <span data-ttu-id="3f56e-120">これは脆弱なコードを助長します。</span><span class="sxs-lookup"><span data-stu-id="3f56e-120">This makes for some fragile code.</span></span> <span data-ttu-id="3f56e-121">ジェネリックは、リストの各インスタンスに含まれるデータの型の追加情報を提供することによってこの問題を解決します。</span><span class="sxs-lookup"><span data-stu-id="3f56e-121">Generics solve this problem by providing additional information the type of data each instance of list will contain.</span></span> <span data-ttu-id="3f56e-122">簡単に言うと、`List<int>` には整数だけを追加でき、`List<Person>` には Persons だけを追加できます。</span><span class="sxs-lookup"><span data-stu-id="3f56e-122">Put simply, you can only add integers to `List<int>` and only add Persons to `List<Person>`, etc.</span></span>

<span data-ttu-id="3f56e-123">ジェネリックは、実行時または**具体化**にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="3f56e-123">Generics are also available at runtime, or **reified**.</span></span> <span data-ttu-id="3f56e-124">これは、使用されているデータ構造の型をランタイムが認識し、より効率的メモリに格納できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="3f56e-124">This means the runtime knows what type of data structure you are using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="3f56e-125">次に示すのは、実行時にデータ構造の型がわかるといかに効率的かということを示す小さなプログラムです。</span><span class="sxs-lookup"><span data-stu-id="3f56e-125">Here is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="3f56e-126">このプログラムの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3f56e-126">This program yields the following output:</span></span>

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

<span data-ttu-id="3f56e-127">最初にわかるのは、非ジェネリック リストよりジェネリック リストの方が並べ替えがはるかに高速であるということです。</span><span class="sxs-lookup"><span data-stu-id="3f56e-127">The first thing you notice here is that sorting the generic list is significantly faster than for the non-generic list.</span></span> <span data-ttu-id="3f56e-128">また、ジェネリック リストの型が具体的 ([System.Int32]) であるのに対して、非ジェネリック リストの型は一般的であることもわかります。</span><span class="sxs-lookup"><span data-stu-id="3f56e-128">You might also notice that the type for the generic list is distinct ([System.Int32]) whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="3f56e-129">ジェネリック `List<int>` の場合はランタイムはそれを int 型と認識してメモリの整数配列にリストの要素を格納できるのに対し、非ジェネリック `ArrayList` の場合はメモリではオブジェクト配列に格納されるので各リスト要素をオブジェクトとしてキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f56e-129">Because the runtime knows the generic `List<int>` is of type int, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element as an object as stored in an object array in memory.</span></span> <span data-ttu-id="3f56e-130">この例にわかるように、余分なキャストに時間がかかり、リストの並べ替え速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="3f56e-130">As shown through this example, the extra castings take up time and slow down the list sort.</span></span>

<span data-ttu-id="3f56e-131">ジェネリックの型をランタイムが認識することの最後の利点は、デバッグ エクスペリエンスの向上です。</span><span class="sxs-lookup"><span data-stu-id="3f56e-131">The last useful thing about the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="3f56e-132">C# でジェネリックをデバッグすると、データ構造内の各要素の型がわかります。</span><span class="sxs-lookup"><span data-stu-id="3f56e-132">When you are debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="3f56e-133">ジェネリックでない場合は、各要素の型を知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="3f56e-133">Without generics, you would have no idea what type each element was.</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="3f56e-134">参考資料とリソース</span><span class="sxs-lookup"><span data-stu-id="3f56e-134">Further reading and resources</span></span>

*   [<span data-ttu-id="3f56e-135">C# のジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="3f56e-135">An Introduction to C# Generics</span></span>](https://msdn.microsoft.com/library/ms379564.aspx)
*   [<span data-ttu-id="3f56e-136">ジェネリック (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3f56e-136">C# Programming Guide - Generics</span></span>](https://msdn.microsoft.com/library/512aeb7t.aspx)
