---
title: "標準クエリ演算子の概要 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f9ad39b4890455f7d03f0b9bbfc51264d98d56b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="90cf2-102">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-102">Standard Query Operators Overview (Visual Basic)</span></span>
<span data-ttu-id="90cf2-103">"*標準クエリ演算子*" は、LINQ パターンを形成するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="90cf2-103">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="90cf2-104">これらのメソッドの大部分はシーケンスに対して機能します。ここでシーケンスとは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスまたは <xref:System.Linq.IQueryable%601> インターフェイスを実装している型のオブジェクトのことです。</span><span class="sxs-lookup"><span data-stu-id="90cf2-104">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="90cf2-105">標準クエリ演算子には、フィルター処理、プロジェクション、集計、並べ替えなどのクエリ機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="90cf2-105">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>  
  
 <span data-ttu-id="90cf2-106">LINQ 標準クエリ演算子には 2 つのセットがあります。1 つは <xref:System.Collections.Generic.IEnumerable%601> 型のオブジェクトを操作する演算子、もう 1 つは <xref:System.Linq.IQueryable%601> 型のオブジェクトを操作する演算子です。</span><span class="sxs-lookup"><span data-stu-id="90cf2-106">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="90cf2-107">各セットを構成するメソッドは、それぞれ、<xref:System.Linq.Enumerable> および <xref:System.Linq.Queryable> クラスの静的メンバーです。</span><span class="sxs-lookup"><span data-stu-id="90cf2-107">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="90cf2-108">そのメソッドの操作対象である型の "*拡張メソッド*" として定義されています。</span><span class="sxs-lookup"><span data-stu-id="90cf2-108">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="90cf2-109">つまり、静的メソッド構文またはインスタンス メソッド構文のいずれかを使用して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="90cf2-109">This means that they can be called by using either static method syntax or instance method syntax.</span></span>  
  
 <span data-ttu-id="90cf2-110">さらに、いくつかの標準クエリ演算子メソッドが、<xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Linq.IQueryable%601> を基にする型以外の型を操作します。</span><span class="sxs-lookup"><span data-stu-id="90cf2-110">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="90cf2-111"><xref:System.Linq.Enumerable> 型は、このような 2 つのメソッドを定義し、その両方が <xref:System.Collections.IEnumerable> 型のオブジェクトを操作します。</span><span class="sxs-lookup"><span data-stu-id="90cf2-111">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="90cf2-112">これらのメソッド <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> と <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> を使用して、LINQ パターンでクエリされるパラメーター化されていないまたは非ジェネリック型のコレクションを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="90cf2-112">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="90cf2-113">これを行うには、厳密に型指定されたオブジェクトのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="90cf2-113">They do this by creating a strongly-typed collection of objects.</span></span> <span data-ttu-id="90cf2-114"><xref:System.Linq.Queryable> クラスは、型 <xref:System.Linq.Queryable> のオブジェクトを操作する 2 つの類似したメソッド <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> と <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> を定義します。</span><span class="sxs-lookup"><span data-stu-id="90cf2-114">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>  
  
 <span data-ttu-id="90cf2-115">標準クエリ演算子の実行のタイミングは、シングルトン値を返すか、値のシーケンスを返すかで異なります。</span><span class="sxs-lookup"><span data-stu-id="90cf2-115">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="90cf2-116">これらのシングルトン値を返すメソッド (たとえば、<xref:System.Linq.Enumerable.Average%2A> と <xref:System.Linq.Enumerable.Sum%2A>) は、すぐに実行されます。</span><span class="sxs-lookup"><span data-stu-id="90cf2-116">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="90cf2-117">シーケンスを返すメソッドは、クエリの実行を遅延させ、列挙可能なオブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="90cf2-117">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>  
  
 <span data-ttu-id="90cf2-118">メモリ内コレクションを操作するメソッド、つまり <xref:System.Collections.Generic.IEnumerable%601> を拡張するメソッドの場合、返される列挙可能なオブジェクトは、メソッドに渡された引数をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="90cf2-118">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="90cf2-119">オブジェクトが列挙されると、クエリ演算子のロジックが使用され、クエリ結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="90cf2-119">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>  
  
 <span data-ttu-id="90cf2-120">一方、<xref:System.Linq.IQueryable%601> を拡張するメソッドはクエリ動作を実装しませんが、実行されるクエリを表す式ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="90cf2-120">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="90cf2-121">クエリの処理は、ソース <xref:System.Linq.IQueryable%601> オブジェクトによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="90cf2-121">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>  
  
 <span data-ttu-id="90cf2-122">クエリ メソッドの呼び出しは 1 回のクエリにまとめてチェーン化できるため、クエリが複雑になることがあります。</span><span class="sxs-lookup"><span data-stu-id="90cf2-122">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>  
  
 <span data-ttu-id="90cf2-123">次のコード例は、標準クエリ演算子を使用してシーケンスに関する情報を取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="90cf2-123">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a><span data-ttu-id="90cf2-124">クエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="90cf2-124">Query Expression Syntax</span></span>  
 <span data-ttu-id="90cf2-125">頻繁に使用される標準クエリ演算子の中には、C# および Visual Basic 言語専用のキーワード構文が使用されているものがあります。こうした構文では、標準クエリ演算子を、"*クエリ**式*" の一部として呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="90cf2-125">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="90cf2-126">専用のキーワードと対応する構文では、標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子 (Visual Basic) のクエリ式構文](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)です。</span><span class="sxs-lookup"><span data-stu-id="90cf2-126">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).</span></span>  
  
## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="90cf2-127">標準クエリ演算子の拡張</span><span class="sxs-lookup"><span data-stu-id="90cf2-127">Extending the Standard Query Operators</span></span>  
 <span data-ttu-id="90cf2-128">標準クエリ演算子のセットを拡張するには、対象のドメインまたはテクノロジに適したドメイン固有のメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="90cf2-128">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="90cf2-129">また、標準クエリ演算子を、リモート評価、クエリ変換、最適化などの追加サービスが用意されている独自の実装で置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="90cf2-129">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="90cf2-130">例については、「<xref:System.Linq.Enumerable.AsEnumerable%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90cf2-130">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="90cf2-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="90cf2-131">Related Sections</span></span>  
 <span data-ttu-id="90cf2-132">次のリンクをクリックすると、さまざまな標準クエリ演算子に関する追加情報を機能別に確認することができます。</span><span class="sxs-lookup"><span data-stu-id="90cf2-132">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>  
  
 [<span data-ttu-id="90cf2-133">データの並べ替え</span><span class="sxs-lookup"><span data-stu-id="90cf2-133">Sorting Data</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [<span data-ttu-id="90cf2-134">セット操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-134">Set Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [<span data-ttu-id="90cf2-135">データのフィルター処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-135">Filtering Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [<span data-ttu-id="90cf2-136">量指定子操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-136">Quantifier Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [<span data-ttu-id="90cf2-137">射影操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-137">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [<span data-ttu-id="90cf2-138">データのパーティション分割 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-138">Partitioning Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [<span data-ttu-id="90cf2-139">結合操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-139">Join Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [<span data-ttu-id="90cf2-140">データのグループ化 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-140">Grouping Data (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [<span data-ttu-id="90cf2-141">生成操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-141">Generation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [<span data-ttu-id="90cf2-142">等値演算 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-142">Equality Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [<span data-ttu-id="90cf2-143">要素の操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-143">Element Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [<span data-ttu-id="90cf2-144">変換する際のデータ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-144">Converting Data Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [<span data-ttu-id="90cf2-145">連結演算 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-145">Concatenation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [<span data-ttu-id="90cf2-146">集計操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-146">Aggregation Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="90cf2-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="90cf2-147">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 <xref:System.Linq.Queryable>  
 [<span data-ttu-id="90cf2-148">LINQ の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90cf2-148">Introduction to LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 [<span data-ttu-id="90cf2-149">標準クエリ演算子 (Visual Basic) のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="90cf2-149">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)  
 [<span data-ttu-id="90cf2-150">実行 (Visual Basic) 方法による標準クエリ演算子の分類</span><span class="sxs-lookup"><span data-stu-id="90cf2-150">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)  
 [<span data-ttu-id="90cf2-151">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="90cf2-151">Extension Methods</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
