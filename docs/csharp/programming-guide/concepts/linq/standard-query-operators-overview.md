---
title: 標準クエリ演算子の概要 (C#)
ms.date: 07/20/2015
ms.assetid: 812fa119-5f65-4139-b4fa-55dccd8dc3ac
ms.openlocfilehash: 36bd5927e64ffacb97beac28b8e7790204e08c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337325"
---
# <a name="standard-query-operators-overview-c"></a><span data-ttu-id="f3f7c-102">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-102">Standard Query Operators Overview (C#)</span></span>
<span data-ttu-id="f3f7c-103">"*標準クエリ演算子*" は、LINQ パターンを形成するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="f3f7c-104">これらのメソッドの大部分はシーケンスに対して機能します。ここでシーケンスとは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスまたは <xref:System.Linq.IQueryable%601> インターフェイスを実装している型のオブジェクトのことです。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="f3f7c-105">標準クエリ演算子には、フィルター処理、プロジェクション、集計、並べ替えなどのクエリ機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="f3f7c-106">LINQ 標準クエリ演算子には 2 つのセットがあります。1 つは <xref:System.Collections.Generic.IEnumerable%601> 型のオブジェクトを操作する演算子、もう 1 つは <xref:System.Linq.IQueryable%601> 型のオブジェクトを操作する演算子です。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="f3f7c-107">各セットを構成するメソッドは、それぞれ、<xref:System.Linq.Enumerable> および <xref:System.Linq.Queryable> クラスの静的メンバーです。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="f3f7c-108">そのメソッドの操作対象である型の "*拡張メソッド*" として定義されています。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="f3f7c-109">つまり、静的メソッド構文またはインスタンス メソッド構文のいずれかを使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="f3f7c-110">さらに、いくつかの標準クエリ演算子メソッドが、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を基にする型以外の型を操作します。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="f3f7c-111"><xref:System.Linq.Enumerable> 型は、このような 2 つのメソッドを定義し、その両方が <xref:System.Collections.IEnumerable> 型のオブジェクトを操作します。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="f3f7c-112">これらのメソッド <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> と <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> を使用して、LINQ パターンでクエリされるパラメーター化されていないまたは非ジェネリック型のコレクションを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="f3f7c-113">これを行うには、厳密に型指定されたオブジェクトのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="f3f7c-114"><xref:System.Linq.Queryable> クラスは、型 <xref:System.Linq.Queryable> のオブジェクトを操作する 2 つの類似したメソッド <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> と <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> を定義します。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="f3f7c-115">標準クエリ演算子の実行のタイミングは、シングルトン値を返すか、値のシーケンスを返すかで異なります。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="f3f7c-116">これらのシングルトン値を返すメソッド (たとえば、<xref:System.Linq.Enumerable.Average%2A> と <xref:System.Linq.Enumerable.Sum%2A>) は、すぐに実行されます。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="f3f7c-117">シーケンスを返すメソッドは、クエリの実行を遅延させ、列挙可能なオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="f3f7c-118">メモリ内コレクションを操作するメソッド、つまり <xref:System.Collections.Generic.IEnumerable%601> を拡張するメソッドの場合、返される列挙可能なオブジェクトは、メソッドに渡された引数をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="f3f7c-119">オブジェクトが列挙されると、クエリ演算子のロジックが使用され、クエリ結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="f3f7c-120">一方、<xref:System.Linq.IQueryable%601> を拡張するメソッドはクエリ動作を実装しませんが、実行されるクエリを表す式ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="f3f7c-121">クエリの処理は、ソース <xref:System.Linq.IQueryable%601> オブジェクトによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="f3f7c-122">クエリ メソッドの呼び出しは 1 回のクエリにまとめてチェーン化できるため、クエリが複雑になることがあります。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="f3f7c-123">次のコード例は、標準クエリ演算子を使用してシーケンスに関する情報を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```csharp  
string sentence = "the quick brown fox jumps over the lazy dog";  
// Split the string into individual words to create a collection.  
string[] words = sentence.Split(' ');  
  
// Using query expression syntax.  
var query = from word in words  
            group word.ToUpper() by word.Length into gr  
            orderby gr.Key  
            select new { Length = gr.Key, Words = gr };  
  
// Using method-based query syntax.  
var query2 = words.  
    GroupBy(w => w.Length, w => w.ToUpper()).  
    Select(g => new { Length = g.Key, Words = g }).  
    OrderBy(o => o.Length);  
  
foreach (var obj in query)  
{  
    Console.WriteLine("Words of length {0}:", obj.Length);  
    foreach (string word in obj.Words)  
        Console.WriteLine(word);  
}  
  
// This code example produces the following output:  
//  
// Words of length 3:  
// THE  
// FOX  
// THE  
// DOG  
// Words of length 4:  
// OVER  
// LAZY  
// Words of length 5:  
// QUICK  
// BROWN  
// JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="f3f7c-124">クエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="f3f7c-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="f3f7c-125">頻繁に使用される標準クエリ演算子の中には、C# および Visual Basic 言語専用のキーワード構文が使用されているものがあります。こうした構文では、標準クエリ演算子を、"*クエリ**式*" の一部として呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="f3f7c-126">専用キーワードおよびそれに対応する構文が使用されている標準クエリ演算子の詳細については、「[標準クエリ演算子のクエリ式構文 (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (C#)](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="f3f7c-127">標準クエリ演算子の拡張</span><span class="sxs-lookup"><span data-stu-id="f3f7c-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="f3f7c-128">標準クエリ演算子のセットを拡張するには、対象のドメインまたはテクノロジに適したドメイン固有のメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="f3f7c-129">また、標準クエリ演算子を、リモート評価、クエリ変換、最適化などの追加サービスが用意されている独自の実装で置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="f3f7c-130">例については、「<xref:System.Linq.Enumerable.AsEnumerable%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f3f7c-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="f3f7c-131">Related Sections</span></span>  
 <span data-ttu-id="f3f7c-132">次のリンクをクリックすると、さまざまな標準クエリ演算子に関する追加情報を機能別に確認することができます。</span><span class="sxs-lookup"><span data-stu-id="f3f7c-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="f3f7c-133">データの並べ替え (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-133">Sorting Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="f3f7c-134">セット操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-134">Set Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="f3f7c-135">データのフィルター処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-135">Filtering Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="f3f7c-136">量指定子操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-136">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="f3f7c-137">射影操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-137">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="f3f7c-138">データのパーティション分割</span><span class="sxs-lookup"><span data-stu-id="f3f7c-138">Partitioning Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="f3f7c-139">結合演算 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-139">Join Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="f3f7c-140">データのグループ化 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-140">Grouping Data (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="f3f7c-141">生成操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-141">Generation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="f3f7c-142">等価演算 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-142">Equality Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="f3f7c-143">要素操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-143">Element Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="f3f7c-144">データ型の変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-144">Converting Data Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="f3f7c-145">連結演算 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-145">Concatenation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="f3f7c-146">集計操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-146">Aggregation Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="f3f7c-147">参照</span><span class="sxs-lookup"><span data-stu-id="f3f7c-147">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [<span data-ttu-id="f3f7c-148">LINQ クエリの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-148">Introduction to LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [<span data-ttu-id="f3f7c-149">標準クエリ演算子のクエリ式構文 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-149">Query Expression Syntax for Standard Query Operators (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [<span data-ttu-id="f3f7c-150">実行方法による標準クエリ演算子の分類 (C#)</span><span class="sxs-lookup"><span data-stu-id="f3f7c-150">Classification of Standard Query Operators by Manner of Execution (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [<span data-ttu-id="f3f7c-151">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="f3f7c-151">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
