---
title: "LINQ to XML における遅延実行とレイジー評価 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 10ecebc2563df5a12b71a743727b1be21b19b671
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a><span data-ttu-id="41b58-102">LINQ to XML における遅延実行とレイジー評価 (C#)</span><span class="sxs-lookup"><span data-stu-id="41b58-102">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>
<span data-ttu-id="41b58-103">クエリと軸の操作は、多くの場合、遅延実行を使用するように実装されています。</span><span class="sxs-lookup"><span data-stu-id="41b58-103">Query and axis operations are often implemented to use deferred execution.</span></span> <span data-ttu-id="41b58-104">このトピックでは、遅延実行の要件と利点、および実装に関する注意点について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b58-104">This topic explains the requirements and advantages of deferred execution, and some implementation considerations.</span></span>  
  
## <a name="deferred-execution"></a><span data-ttu-id="41b58-105">遅延実行</span><span class="sxs-lookup"><span data-stu-id="41b58-105">Deferred Execution</span></span>  
 <span data-ttu-id="41b58-106">遅延実行とは、"*具体*" 値が実際に必要となるまで、式の評価を遅らせることを意味します。</span><span class="sxs-lookup"><span data-stu-id="41b58-106">Deferred execution means that the evaluation of an expression is delayed until its *realized* value is actually required.</span></span> <span data-ttu-id="41b58-107">大きなデータ コレクションの操作が必要な場合、特に連結されたクエリや操作が含まれているプログラムでは、遅延実行によってパフォーマンスが大幅に向上することがあります。</span><span class="sxs-lookup"><span data-stu-id="41b58-107">Deferred execution can greatly improve performance when you have to manipulate large data collections, especially in programs that contain a series of chained queries or manipulations.</span></span> <span data-ttu-id="41b58-108">最も効果的なケースでは、遅延実行を使用することによって、ソース コレクションの繰り返し処理を 1 度行うだけで済むようになります。</span><span class="sxs-lookup"><span data-stu-id="41b58-108">In the best case, deferred execution enables only a single iteration through the source collection.</span></span>  
  
 <span data-ttu-id="41b58-109">LINQ テクノロジでは、コア <xref:System.Linq?displayProperty=fullName> クラスのメンバーにおいても、<xref:System.Xml.Linq.Extensions?displayProperty=fullName> などのさまざまな LINQ 名前空間の拡張メソッドにおいても、遅延実行が広く利用されています。</span><span class="sxs-lookup"><span data-stu-id="41b58-109">The LINQ technologies make extensive use of deferred execution in both the members of core <xref:System.Linq?displayProperty=fullName> classes and in the extension methods in the various LINQ namespaces, such as <xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="41b58-110">C# 言語では、反復子ブロック内で [yield](../../../../csharp/language-reference/keywords/yield.md) キーワード (`yield-return` ステートメントの形式) を使用することにより、遅延実行が直接サポートされます。</span><span class="sxs-lookup"><span data-stu-id="41b58-110">Deferred execution is supported directly in the C# language by the [yield](../../../../csharp/language-reference/keywords/yield.md) keyword (in the form of the `yield-return` statement) when used within an iterator block.</span></span> <span data-ttu-id="41b58-111">このような反復子は <xref:System.Collections.IEnumerator> 型または <xref:System.Collections.Generic.IEnumerator%601> 型 (または派生型) のコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="41b58-111">Such an iterator must return a collection of type <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> (or a derived type).</span></span>  
  
## <a name="eager-vs-lazy-evaluation"></a><span data-ttu-id="41b58-112">集中評価とレイジー評価</span><span class="sxs-lookup"><span data-stu-id="41b58-112">Eager vs. Lazy Evaluation</span></span>  
 <span data-ttu-id="41b58-113">遅延実行を実装するメソッドを記述するときは、レイジー評価と集中評価のどちらを使用してメソッドを実装するかについても決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41b58-113">When you write a method that implements deferred execution, you also have to decide whether to implement the method using lazy evaluation or eager evaluation.</span></span>  
  
-   <span data-ttu-id="41b58-114">"*レイジー評価*" では、反復子を呼び出すたびに、ソース コレクションの 1 つの要素が処理されます。</span><span class="sxs-lookup"><span data-stu-id="41b58-114">In *lazy evaluation*, a single element of the source collection is processed during each call to the iterator.</span></span> <span data-ttu-id="41b58-115">これが、一般的な反復子の実装方法です。</span><span class="sxs-lookup"><span data-stu-id="41b58-115">This is the typical way in which iterators are implemented.</span></span>  
  
-   <span data-ttu-id="41b58-116">"*集中評価*" では、反復子への最初の呼び出しの結果として、コレクション全体が処理されます。</span><span class="sxs-lookup"><span data-stu-id="41b58-116">In *eager evaluation*, the first call to the iterator will result in the entire collection being processed.</span></span> <span data-ttu-id="41b58-117">ソース コレクションの一時的なコピーが必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="41b58-117">A temporary copy of the source collection might also be required.</span></span> <span data-ttu-id="41b58-118">たとえば <xref:System.Linq.Enumerable.OrderBy%2A> メソッドでは、最初の要素を返す前に、コレクション全体を並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="41b58-118">For example, the <xref:System.Linq.Enumerable.OrderBy%2A> method has to sort the entire collection before it returns the first element.</span></span>  
  
 <span data-ttu-id="41b58-119">通常は、レイジー評価を使用するとパフォーマンスが向上します。コレクション評価時のオーバーヘッド処理が均等に分散され、一時データの使用が最小限に抑えられるためです。</span><span class="sxs-lookup"><span data-stu-id="41b58-119">Lazy evaluation usually yields better performance because it distributes overhead processing evenly throughout the evaluation of the collection and minimizes the use of temporary data.</span></span> <span data-ttu-id="41b58-120">もちろん、操作によっては、中間結果を具体化するより他に方法がない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="41b58-120">Of course, for some operations, there is no other option than to materialize intermediate results.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="41b58-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="41b58-121">Next Steps</span></span>  
 <span data-ttu-id="41b58-122">このチュートリアルの次のトピックでは、遅延実行について説明します。</span><span class="sxs-lookup"><span data-stu-id="41b58-122">The next topic in this tutorial illustrates deferred execution:</span></span>  
  
-   [<span data-ttu-id="41b58-123">遅延実行の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="41b58-123">Deferred Execution Example (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="41b58-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="41b58-124">See Also</span></span>  
 <span data-ttu-id="41b58-125">[チュートリアル: クエリの連結 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) </span><span class="sxs-lookup"><span data-stu-id="41b58-125">[Tutorial: Chaining Queries Together (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md) </span></span>  
 <span data-ttu-id="41b58-126">[概念と用語 (関数型変換) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="41b58-126">[Concepts and Terminology (Functional Transformation) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md) </span></span>  
 <span data-ttu-id="41b58-127">[集計操作 (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md) </span><span class="sxs-lookup"><span data-stu-id="41b58-127">[Aggregation Operations (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md) </span></span>  
 [<span data-ttu-id="41b58-128">yield</span><span class="sxs-lookup"><span data-stu-id="41b58-128">yield</span></span>](../../../../csharp/language-reference/keywords/yield.md)

