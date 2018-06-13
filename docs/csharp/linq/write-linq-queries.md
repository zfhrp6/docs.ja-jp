---
title: C# での LINQ クエリの作成
description: クエリの記述方法について説明します。
ms.date: 12/1/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: a9683dbf3c4101829054477824ccc7135f20f535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33288838"
---
# <a name="write-linq-queries-in-c"></a><span data-ttu-id="d1bbd-103">C# での LINQ クエリの作成</span><span class="sxs-lookup"><span data-stu-id="d1bbd-103">Write LINQ queries in C#</span></span>

<span data-ttu-id="d1bbd-104">このトピックでは、C# で LINQ クエリを記述できる 3 つの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-104">This topic shows the three ways in which you can write a LINQ query in C#:</span></span>  
  
1.  <span data-ttu-id="d1bbd-105">クエリ構文を使用する。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-105">Use query syntax.</span></span>  
  
2.  <span data-ttu-id="d1bbd-106">メソッド構文を使用する。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-106">Use method syntax.</span></span>  
  
3.  <span data-ttu-id="d1bbd-107">クエリ構文とメソッド構文を組み合わせて使用する。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-107">Use a combination of query syntax and method syntax.</span></span>  
  
 <span data-ttu-id="d1bbd-108">以下の例では、上記の各アプローチを使用したシンプルな LINQ クエリを示します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-108">The following examples demonstrate some simple LINQ queries by using each approach listed previously.</span></span> <span data-ttu-id="d1bbd-109">一般に、可能であれば常に (1) を使用し、(2) と (3) は必要に応じて使用するというのがルールになっています。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-109">In general, the rule is to use (1) whenever possible, and use (2) and (3) whenever necessary.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1bbd-110">これらのクエリでは、シンプルなメモリ内コレクションに対して操作を実行します。ただし、基本的な構文は、LINQ to Entities および LINQ to XML で使用されるのと同じものです。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-110">These queries operate on simple in-memory collections; however, the basic syntax is identical to that used in LINQ to Entities and LINQ to XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1bbd-111">例</span><span class="sxs-lookup"><span data-stu-id="d1bbd-111">Example</span></span>  
  
## <a name="query-syntax"></a><span data-ttu-id="d1bbd-112">クエリ構文</span><span class="sxs-lookup"><span data-stu-id="d1bbd-112">Query syntax</span></span>  
 <span data-ttu-id="d1bbd-113">ほとんどのクエリ記述については、*クエリの構文*を使用して*クエリ式*を作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-113">The recommended way to write most queries is to use *query syntax* to create *query expressions*.</span></span> <span data-ttu-id="d1bbd-114">次の例は、3 つのクエリ式を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-114">The following example shows three query expressions.</span></span> <span data-ttu-id="d1bbd-115">1 つ目のクエリ式は、`where` 句を使用した条件を適用することで、結果をフィルター処理または制限する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-115">The first query expression demonstrates how to filter or restrict results by applying conditions with a `where` clause.</span></span> <span data-ttu-id="d1bbd-116">このクエリは、値が 7 より大きいか、または 3 より小さいソース シーケンス内のすべての要素を返します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-116">It returns all elements in the source sequence whose values are greater than 7 or less than 3.</span></span> <span data-ttu-id="d1bbd-117">2 つ目の式は、返された結果を並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-117">The second expression demonstrates how to order the returned results.</span></span> <span data-ttu-id="d1bbd-118">3 つ目の式は、キーに基づいて結果をグループ化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-118">The third expression demonstrates how to group results according to a key.</span></span> <span data-ttu-id="d1bbd-119">このクエリは、単語の頭文字に基づいて 2 つのグループを返します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-119">This query returns two groups based on the first letter of the word.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#5](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]  
  
 <span data-ttu-id="d1bbd-120">クエリの型が <xref:System.Collections.Generic.IEnumerable%601> であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-120">Note that the type of the queries is <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="d1bbd-121">これらのクエリはすべて、次の例で示すように、`var` を使用しても記述できます。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-121">All of these queries could be written using `var` as shown in the following example:</span></span>  
  
 `var query = from num in numbers...`  
  
 <span data-ttu-id="d1bbd-122">上記の各例では、`foreach` ステートメントまたはその他のステートメントでクエリ変数を反復処理するまで、クエリは実際には実行されません。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-122">In each previous example, the queries do not actually execute until you iterate over the query variable in a `foreach` statement or other statement.</span></span> <span data-ttu-id="d1bbd-123">詳しくは、「[LINQ クエリの概要](../programming-guide/concepts/linq/introduction-to-linq-queries.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-123">For more information, see [Introduction to LINQ Queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1bbd-124">例</span><span class="sxs-lookup"><span data-stu-id="d1bbd-124">Example</span></span>  
  
## <a name="method-syntax"></a><span data-ttu-id="d1bbd-125">メソッド構文</span><span class="sxs-lookup"><span data-stu-id="d1bbd-125">Method syntax</span></span>  
 <span data-ttu-id="d1bbd-126">一部のクエリ操作は、メソッド呼び出しとして表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-126">Some query operations must be expressed as a method call.</span></span> <span data-ttu-id="d1bbd-127">このようなメソッドで最も一般的なものは、<xref:System.Linq.Enumerable.Sum%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A>、<xref:System.Linq.Enumerable.Average%2A> のような単一の数値を返すメソッドです。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-127">The most common such methods are those that return singleton numeric values, such as <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>, and so on.</span></span> <span data-ttu-id="d1bbd-128">これらのメソッドは、単一の値のみを表し、追加のクエリ操作のソースとしては使用できないため、常に、どのクエリよりも後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-128">These methods must always be called last in any query because they represent only a single value and cannot serve as the source for an additional query operation.</span></span> <span data-ttu-id="d1bbd-129">次の例は、クエリ式でのメソッド呼び出しを示したものです。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-129">The following example shows a method call in a query expression:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#6](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="d1bbd-130">例</span><span class="sxs-lookup"><span data-stu-id="d1bbd-130">Example</span></span>  
 <span data-ttu-id="d1bbd-131">メソッドに Action または Func パラメーターがある場合、それらは[ラムダ](../programming-guide/statements-expressions-operators/lambda-expressions.md)式の形式で提供されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-131">If the method has  Action or Func parameters, these are provided in the form of a [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) expression, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#7](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]  
  
 <span data-ttu-id="d1bbd-132">上記のクエリでは Query #4 だけが直ちに実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-132">In the previous queries, only Query #4 executes immediately.</span></span> <span data-ttu-id="d1bbd-133">これは、それがジェネリック <xref:System.Collections.Generic.IEnumerable%601> コレクションではなく、単一値を返すためです。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-133">This is because it returns a single value, and not a generic <xref:System.Collections.Generic.IEnumerable%601> collection.</span></span> <span data-ttu-id="d1bbd-134">メソッド自体は、値を計算するために `foreach` を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-134">The method itself has to use `foreach` in order to compute its value.</span></span>  
  
 <span data-ttu-id="d1bbd-135">上記の各クエリは、[var](../language-reference/keywords/var.md) による暗黙的型指定を使用しても記述できます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-135">Each of the previous queries can be written by using implicit typing with [var](../language-reference/keywords/var.md), as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#8](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="d1bbd-136">例</span><span class="sxs-lookup"><span data-stu-id="d1bbd-136">Example</span></span>  
  
## <a name="mixed-query-and-method-syntax"></a><span data-ttu-id="d1bbd-137">クエリとメソッド構文の併用</span><span class="sxs-lookup"><span data-stu-id="d1bbd-137">Mixed query and method syntax</span></span>  
 <span data-ttu-id="d1bbd-138">この例では、クエリ句の結果に対してメソッド構文を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-138">This example shows how to use method syntax on the results of a query clause.</span></span> <span data-ttu-id="d1bbd-139">方法は、クエリ式をかっこで囲み、ドット演算子を適用して、メソッドを呼び出すだけです。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-139">Just enclose the query expression in parentheses, and then apply the dot operator and call the method.</span></span> <span data-ttu-id="d1bbd-140">次の例では、Query #7 は、値が 3 ～ 7 である数値のカウントを返します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-140">In the following example, query #7 returns a count of the numbers whose value is between 3 and 7.</span></span> <span data-ttu-id="d1bbd-141">ただし一般的には、メソッド呼び出しの結果の格納には、2 番目の変数を使うほうが賢明です。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-141">In general, however, it is better to use a second variable to store the result of the method call.</span></span> <span data-ttu-id="d1bbd-142">この方法のほうが、クエリをクエリ結果と混同する恐れがありません。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-142">In this manner, the query is less likely to be confused with the results of the query.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#9](../../../samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]  
  
 <span data-ttu-id="d1bbd-143">Query #7 はコレクションではなく単一の値を返すので、クエリはすぐに実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-143">Because Query #7 returns a single value and not a collection, the query executes immediately.</span></span>  
  
 <span data-ttu-id="d1bbd-144">上記のクエリは、`var` による暗黙的型指定を使用しても記述できます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-144">The previous query can be written by using implicit typing with `var`, as follows:</span></span>  
  
```csharp  
var numCount = (from num in numbers...  
```  
  
 <span data-ttu-id="d1bbd-145">次のように、メソッド構文で記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-145">It can be written in method syntax as follows:</span></span>  
  
```csharp  
var numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
 <span data-ttu-id="d1bbd-146">次のように、明示的な型指定を使用して記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1bbd-146">It can be written by using explicit typing, as follows:</span></span>  
  
```csharp  
int numCount = numbers.Where(n => n < 3 || n > 7).Count();  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1bbd-147">参照</span><span class="sxs-lookup"><span data-stu-id="d1bbd-147">See Also</span></span>  
  <span data-ttu-id="d1bbd-148">[チュートリアル: C# でのクエリの作成](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span><span class="sxs-lookup"><span data-stu-id="d1bbd-148">[Walkthrough: Writing Queries in C#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md) </span></span>  
 [<span data-ttu-id="d1bbd-149">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="d1bbd-149">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="d1bbd-150">where 句</span><span class="sxs-lookup"><span data-stu-id="d1bbd-150">where clause</span></span>](../language-reference/keywords/where-clause.md)
