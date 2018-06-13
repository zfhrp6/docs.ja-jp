---
title: 量指定子操作 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0a0a5fae35a14ab6451f2f56fb2eedd92ac437e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645835"
---
# <a name="quantifier-operations-visual-basic"></a>量指定子操作 (Visual Basic)
量指定子操作は、シーケンス内の要素の一部またはすべてが条件を満たしているかどうかを示す <xref:System.Boolean> 値を返します。  
  
 次の図は、2 つの異なるソース シーケンスに対する、2 つの異なる量指定子操作を示しています。 最初の操作では、1 つ以上の要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。 2 番目の操作では、すべての要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。  
  
 ![LINQ 量指定子操作](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 次のセクションでは、量指定子操作を実行する標準クエリ演算子のメソッドの一覧を示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|すべて|シーケンス内のすべての要素が条件を満たしているかどうかを調べます。|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|どれでも可|シーケンス内のいずれかの要素が条件を満たしているかどうかを調べます。|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|内容|指定した要素がシーケンスに格納されているかどうかを調べます。|該当なし。|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>クエリ式の構文例  
 これらの例を使用して、 `Aggregate` LINQ クエリのフィルター条件の一部として Visual Basic での句。  
  
 次の例では、`Aggregate`句と<xref:System.Linq.Enumerable.All%2A>のペットは指定された有効期間より古いすべての人をコレクションから取得する拡張メソッド。  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 次の例では、`Aggregate`句と<xref:System.Linq.Enumerable.Any%2A>を少なくとも 1 つ所有するユーザーにペットをコレクションから返す拡張メソッドが指定した期限を過ぎています。  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq>  
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
