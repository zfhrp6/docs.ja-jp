---
title: "セット操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
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
ms.openlocfilehash: e835737b388427445a15b6658c7d148801f29b79
ms.lasthandoff: 03/13/2017

---
# <a name="set-operations-visual-basic"></a>集合演算 (Visual Basic)
LINQ のセット操作は、同じまたは別のコレクション (またはセット) 内に等しい要素が存在するかに基づいて、結果セットを生成するクエリ操作を参照してください。  
  
 次のセクションでは、集合演算を実行する標準クエリ演算子のメソッドが一覧表示します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Distinct|重複するコレクションから値を削除します。|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName>|  
|除く|差集合を&1; つのコレクションのうち、2 番目のコレクションに表示されない要素を返します。|該当なし。|<xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></xref:System.Linq.Queryable.Except%2A?displayProperty=fullName>|  
|交差|積集合、2 つのコレクションのそれぞれに出現する要素を返します。|該当なし。|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName>|  
|和集合|和集合を&2; つのコレクションのいずれかで表示されている一意の要素を返します。|該当なし。|<xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></xref:System.Linq.Queryable.Union%2A?displayProperty=fullName>|  
  
## <a name="comparison-of-set-operations"></a>セット操作の比較  
  
### <a name="distinct"></a>Distinct  
 次の図の動作を示しています、<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName>メソッドを文字のシーケンス</xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName>。 返されるシーケンスには、入力シーケンスから一意の要素が含まれています。  
  
 ![Distinct() の動作を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "個別")  
  
### <a name="except"></a>除く  
 次の図は、 <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>。</xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>の動作を示しています。 返されるシーケンスには、2 番目の入力シーケンスに含まれていない最初の入力シーケンスから要素のみが含まれています。  
  
 ![Except() のアクションを示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")  
  
### <a name="intersect"></a>交差  
 次の図は、 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>。</xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>の動作を示しています。 返されるシーケンスには、入力シーケンスの両方に共通する要素が含まれています。  
  
 ![2 つのシーケンスの積集合を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "交差しています。")  
  
### <a name="union"></a>和集合  
 次の図は、文字の&2; つのシーケンスの和集合演算を示しています。 返されるシーケンスには、両方の入力シーケンスから一意の要素が含まれています。  
  
 ![2 つのシーケンスの和集合を示すグラフィック。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## <a name="query-expression-syntax-example"></a>クエリ式の構文例  
 次の例では、`Distinct`整数のリストから一意の番号を返す LINQ クエリ句で使用します。  
  
 [!code-vb[CsLINQSetOps&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Distinct 句](../../../../visual-basic/language-reference/queries/distinct-clause.md)   
 [方法: 結合および比較文字列のコレクション (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)   
 [方法:&2; つのリスト (LINQ) (Visual Basic) の差集合を検索](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
