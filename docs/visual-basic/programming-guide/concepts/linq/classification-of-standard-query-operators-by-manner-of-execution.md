---
title: "(Visual Basic) の実行方法による標準クエリ演算子の分類 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 7f55b0be-9f6e-44f8-865c-6afbea50cc54
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a13f2fcf33c2faacd5b2662cd96d0f962b54322f
ms.lasthandoff: 03/13/2017

---
# <a name="classification-of-standard-query-operators-by-manner-of-execution-visual-basic"></a>(Visual Basic) の実行方法による標準クエリ演算子の分類
LINQ 標準クエリ演算子メソッドの実装をオブジェクトには&2; つの方法のいずれかで実行します。 即時します。 遅延実行を使用するクエリ演算子は&2; つのカテゴリにさらに分類できます。 ストリーミングとストリーミング以外です。 別のクエリ演算子の実行方法がわかっている場合と役に立ちます、特定のクエリから取得した結果を理解します。 これは、データ ソースを変更する場合、または別のクエリに基づくクエリを作成する場合に特に当てはまります。 このトピックでは、実行の方法に基づいて、標準クエリ演算子を分類します。  
  
## <a name="manners-of-execution"></a>実行方法  
  
### <a name="immediate"></a>イミディエイト  
 即時実行では、データ ソースを読み取るし、クエリが宣言されているコード内の位置に、操作が実行されることを示します。 1 つの列挙可能でない結果を返すすべての標準クエリ演算子は、直ちに実行されます。  
  
### <a name="deferred"></a>遅延  
 遅延実行すると、操作がない実行、コード内の位置に、クエリが宣言されています。 クエリ変数を列挙すると、たとえばを使用する場合にのみ操作が実行される、`For Each`ステートメントです。 つまり、クエリの実行の結果は、クエリが定義されている場合ではなく、クエリを実行すると、データ ソースの内容に依存します。 クエリ変数が複数回列挙結果は毎回を異なる場合があります。 戻り値の型は、ほとんどすべての標準クエリ演算子<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IOrderedEnumerable%601>遅延形式で実行されます</xref:System.Linq.IOrderedEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>。  
  
 遅延実行を使用するクエリ演算子は、ストリーミングとストリーミング以外、さらに分類できます。  
  
#### <a name="streaming"></a>ストリーム  
 ストリーミング演算子は、要素を生成する前に、すべてのソース データを読み取ることはありません。 実行時に、ストリーミング演算子による演算の各ソース要素に対しては読み取りし、適切な場合は、要素が生成されます。 ストリーミング演算子は、結果の要素を生成するまで、ソース要素を読み取りを続行します。 つまり、1 つの結果の要素を生成する&1; つ以上のソース要素を読み取ることがあります。  
  
#### <a name="non-streaming"></a>非ストリーミング  
 非ストリーミング演算子は、結果の要素を生成する前に、すべてのソース データを読み取る必要があります。 並べ替えやグループ化などの操作は、このカテゴリに分類されます。 実行時に、ストリーミング以外のクエリ演算子すべてのソース データを読み取り、データ構造に配置、操作を実行および結果として得られる要素を生成します。  
  
## <a name="classification-table"></a>分類テーブル  
 次の表では、各標準クエリ演算子のメソッドの実行には、その方法に従って分類しています。  
  
> [!NOTE]
>  演算子が&2; つの列にマークされている場合は、2 つの入力シーケンスが、操作に関係しているし、各シーケンスの評価方法が異なります。 このような場合は常に評価されるパラメーター リストの最初のシーケンス、遅延実行の方法をストリーミングします。  
  
|標準クエリ演算子|戻り値の型|即時実行|遅延実行 (ストリーミング)|非ストリーミングの実行を遅延|  
|-----------------------------|-----------------|-------------------------|----------------------------------|---------------------------------------|  
|<xref:System.Linq.Enumerable.Aggregate%2A></xref:System.Linq.Enumerable.Aggregate%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.All%2A></xref:System.Linq.Enumerable.All%2A>|<xref:System.Boolean></xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Any%2A></xref:System.Linq.Enumerable.Any%2A>|<xref:System.Boolean></xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.AsEnumerable%2A></xref:System.Linq.Enumerable.AsEnumerable%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Average%2A></xref:System.Linq.Enumerable.Average%2A>|1 つの数値|X|||  
|<xref:System.Linq.Enumerable.Cast%2A></xref:System.Linq.Enumerable.Cast%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Concat%2A></xref:System.Linq.Enumerable.Concat%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Contains%2A></xref:System.Linq.Enumerable.Contains%2A>|<xref:System.Boolean></xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Count%2A></xref:System.Linq.Enumerable.Count%2A>|<xref:System.Int32></xref:System.Int32>|X|||  
|<xref:System.Linq.Enumerable.DefaultIfEmpty%2A></xref:System.Linq.Enumerable.DefaultIfEmpty%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Distinct%2A></xref:System.Linq.Enumerable.Distinct%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ElementAt%2A></xref:System.Linq.Enumerable.ElementAt%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.ElementAtOrDefault%2A></xref:System.Linq.Enumerable.ElementAtOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Empty%2A></xref:System.Linq.Enumerable.Empty%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>|X|||  
|<xref:System.Linq.Enumerable.Except%2A></xref:System.Linq.Enumerable.Except%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.First%2A></xref:System.Linq.Enumerable.First%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.FirstOrDefault%2A></xref:System.Linq.Enumerable.FirstOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.GroupBy%2A></xref:System.Linq.Enumerable.GroupBy%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.GroupJoin%2A></xref:System.Linq.Enumerable.GroupJoin%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X|X|  
<xref:System.Linq.Enumerable.Intersect%2A></xref:System.Linq.Enumerable.Intersect%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Join%2A></xref:System.Linq.Enumerable.Join%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X|X|  
|<xref:System.Linq.Enumerable.Last%2A></xref:System.Linq.Enumerable.Last%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LastOrDefault%2A></xref:System.Linq.Enumerable.LastOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.LongCount%2A></xref:System.Linq.Enumerable.LongCount%2A>|<xref:System.Int64></xref:System.Int64>|X|||  
|<xref:System.Linq.Enumerable.Max%2A></xref:System.Linq.Enumerable.Max%2A>|1 つの数値、TSource、または TResult|X|||  
|<xref:System.Linq.Enumerable.Min%2A></xref:System.Linq.Enumerable.Min%2A>|1 つの数値、TSource、または TResult|X|||  
|<xref:System.Linq.Enumerable.OfType%2A></xref:System.Linq.Enumerable.OfType%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.OrderBy%2A></xref:System.Linq.Enumerable.OrderBy%2A>|<xref:System.Linq.IOrderedEnumerable%601></xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.OrderByDescending%2A></xref:System.Linq.Enumerable.OrderByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601></xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Range%2A></xref:System.Linq.Enumerable.Range%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Repeat%2A></xref:System.Linq.Enumerable.Repeat%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Reverse%2A></xref:System.Linq.Enumerable.Reverse%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.Select%2A></xref:System.Linq.Enumerable.Select%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SelectMany%2A></xref:System.Linq.Enumerable.SelectMany%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SequenceEqual%2A></xref:System.Linq.Enumerable.SequenceEqual%2A>|<xref:System.Boolean></xref:System.Boolean>|X|||  
|<xref:System.Linq.Enumerable.Single%2A></xref:System.Linq.Enumerable.Single%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.SingleOrDefault%2A></xref:System.Linq.Enumerable.SingleOrDefault%2A>|TSource|X|||  
|<xref:System.Linq.Enumerable.Skip%2A></xref:System.Linq.Enumerable.Skip%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.SkipWhile%2A></xref:System.Linq.Enumerable.SkipWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Sum%2A></xref:System.Linq.Enumerable.Sum%2A>|1 つの数値|X|||  
|<xref:System.Linq.Enumerable.Take%2A></xref:System.Linq.Enumerable.Take%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
<xref:System.Linq.Enumerable.TakeWhile%2A></xref:System.Linq.Enumerable.TakeWhile%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.ThenBy%2A></xref:System.Linq.Enumerable.ThenBy%2A>|<xref:System.Linq.IOrderedEnumerable%601></xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ThenByDescending%2A></xref:System.Linq.Enumerable.ThenByDescending%2A>|<xref:System.Linq.IOrderedEnumerable%601></xref:System.Linq.IOrderedEnumerable%601>|||X|  
|<xref:System.Linq.Enumerable.ToArray%2A></xref:System.Linq.Enumerable.ToArray%2A>|TSource 配列|X|||  
|<xref:System.Linq.Enumerable.ToDictionary%2A></xref:System.Linq.Enumerable.ToDictionary%2A>|<xref:System.Collections.Generic.Dictionary%602></xref:System.Collections.Generic.Dictionary%602>|X|||  
|<xref:System.Linq.Enumerable.ToList%2A></xref:System.Linq.Enumerable.ToList%2A>|<xref:System.Collections.Generic.IList%601></xref:System.Collections.Generic.IList%601>|X|||  
|<xref:System.Linq.Enumerable.ToLookup%2A></xref:System.Linq.Enumerable.ToLookup%2A>|<xref:System.Linq.ILookup%602></xref:System.Linq.ILookup%602>|X|||  
|<xref:System.Linq.Enumerable.Union%2A></xref:System.Linq.Enumerable.Union%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
|<xref:System.Linq.Enumerable.Where%2A></xref:System.Linq.Enumerable.Where%2A>|<xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>||X||  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [標準クエリ演算子 (Visual Basic) のクエリ式の構文](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)   
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
