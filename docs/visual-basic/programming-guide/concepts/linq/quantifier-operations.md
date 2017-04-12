---
title: "量指定子操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
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
ms.openlocfilehash: 7f69aed2e0e6791ca7f17c3420ff75a1ba220187
ms.lasthandoff: 03/13/2017

---
# <a name="quantifier-operations-visual-basic"></a>量指定子操作 (Visual Basic)
量指定子操作を返す、<xref:System.Boolean>シーケンス内の要素の一部またはすべてが、条件を満たすかどうかを示す値</xref:System.Boolean>。  
  
 次の図は、2 つの異なるソース シーケンス上の&2; つの異なる量指定子操作を示しています。 最初の操作が文字 'A' の&1; つ以上の要素のかどうか、結果を要求する`true`です。 2 番目の操作要求のかどうかは、すべての要素は文字 'A' され、結果は`true`です。  
  
 ![LINQ 量指定子操作](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 量指定子操作を実行する標準クエリ演算子メソッドは、次のように記載されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|すべて|シーケンス内のすべての要素が条件を満たすかどうかを決定します。|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></xref:System.Linq.Enumerable.All%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=fullName></xref:System.Linq.Queryable.All%2A?displayProperty=fullName>|  
|どれでも可|シーケンス内の各要素が条件を満たすかどうかを決定します。|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></xref:System.Linq.Queryable.Any%2A?displayProperty=fullName>|  
|内容|指定した要素を格納するシーケンスがサポートされるかどうかを決定します。|該当なし。|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>クエリ式の構文例  
 これらの例を使用して、 `Aggregate` LINQ クエリでフィルター条件の一部として Visual Basic での句。  
  
 次の例では、`Aggregate`句と<xref:System.Linq.Enumerable.All%2A>を持つペットは、指定された保有期間より古いすべての人をコレクションから返す拡張メソッド</xref:System.Linq.Enumerable.All%2A>。  
  
 [!code-vb[CsLINQAnyAll&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 次の例では、`Aggregate`句と<xref:System.Linq.Enumerable.Any%2A>を少なくとも&1; つを所有するユーザーには pet をコレクションから返す拡張メソッドは、指定された保有期間より古い</xref:System.Linq.Enumerable.Any%2A>。  
  
 [!code-vb[CsLINQAnyAll&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [方法: 指定された単語 (LINQ) (Visual Basic) のセットを含む文章を照会します。](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
