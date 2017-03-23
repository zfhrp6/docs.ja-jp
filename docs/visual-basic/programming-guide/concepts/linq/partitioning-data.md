---
title: "(Visual Basic) のデータをパーティション分割 |Microsoft ドキュメント"
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
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a746ce3e24812d1df6b6e221cca0364bf2cc7f1c
ms.lasthandoff: 03/13/2017

---
# <a name="partitioning-data-visual-basic"></a>データのパーティション分割 (Visual Basic)
LINQ でのパーティション分割は、要素を再配置して、セクションでは、のいずれかを返すことがなく、入力シーケンスを&2; つのセクションに分割の操作です。  
  
 次の図は、文字のシーケンスに対して次の&3; つの異なる方法でパーティション分割に操作の結果を示しています。 最初の操作は、シーケンス内の最初の&3; つの要素を返します。 2 番目の操作では、最初の&3; つの要素をスキップし、残りの要素を返します。 3 番目の操作では、シーケンス内の最初の&2; つの要素をスキップし、次の&3; つの要素を返します。  
  
 ![LINQ の操作をパーティション分割](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 次のセクションでは、シーケンスのパーティション分割する標準クエリ演算子のメソッドが一覧表示します。  
  
## <a name="operators"></a>演算子  
  
|演算子名|説明|Visual Basic のクエリ式の構文|説明|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|シーケンス内の指定した位置までの要素をスキップします。|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|SkipWhile|要素が条件を満たさないまでは、述語関数に基づいて要素をスキップします。|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|Take|シーケンス内の指定した位置までの要素を取得します。|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|TakeWhile|要素が条件を満たさないまでは、述語関数に基づいて要素を取得します。|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>クエリ式の構文例  
  
### <a name="skip"></a>Skip  
 次のコード例では、`Skip`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を配列内の残りの文字列を返す前に、文字列の配列内の最初の&4; つの文字列をスキップします。  
  
 [!code-vb[CsLINQPartitioning&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 次のコード例では、`Skip While`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列の最初の文字の中に、配列内の文字列をスキップするは、"a"です。 配列内の残りの文字列が返されます。  
  
 [!code-vb[CsLINQPartitioning&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 次のコード例では、`Take`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列の配列の最初の&2; つの文字列を取得します。  
  
 [!code-vb[CsLINQPartitioning&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 次のコード例では、`Take While`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]文字列の長さが&5; 個以下に、配列から文字列を取得します。  
  
 [!code-vb[CsLINQPartitioning&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Skip 句](../../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Skip While 句](../../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take 句](../../../../visual-basic/language-reference/queries/take-clause.md)   
 [Take While 句](../../../../visual-basic/language-reference/queries/take-while-clause.md)
