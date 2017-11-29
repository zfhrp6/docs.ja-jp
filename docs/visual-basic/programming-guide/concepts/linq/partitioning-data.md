---
title: "データのパーティション分割 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ea305a67765e1b11ceebbf65c48a685024a41f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-visual-basic"></a>データのパーティション分割 (Visual Basic)
LINQ におけるパーティション分割とは、要素を並べ替えずに入力シーケンスを 2 つのセクションに分割し、それらのセクションの 1 つを返す操作を指します。  
  
 次の図は、文字のシーケンスに対して 3 つの異なるパーティション分割操作を実行した結果を示しています。 最初の操作では、シーケンスの最初の 3 つの要素が返されます。 2 番目の操作では、最初の 3 つの要素がスキップされ、残りの要素が返されます。 3 番目の操作では、シーケンスの最初の 2 つの要素がスキップされ、次の 3 つの要素が返されます。  
  
 ![LINQ パーティション分割操作](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 次のセクションに、シーケンスのパーティション分割を実行する標準クエリ演算子メソッドの一覧を示します。  
  
## <a name="operators"></a>演算子  
  
|演算子名|説明|Visual Basic のクエリ式の構文|説明|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Skip|シーケンス内の指定した位置まで要素をスキップします。|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|述語関数に基づき、条件を満たさない要素が出現する位置まで要素をスキップします。|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|シーケンス内の指定した位置までの要素を取得します。|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|述語関数に基づき、条件を満たさない要素が出現する位置までの要素を取得します。|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>クエリ式の構文例  
  
### <a name="skip"></a>Skip  
 次のコード例では、`Skip`句[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を配列内の残りの文字列を返す前に、文字列の配列内の最初の 4 つの文字列をスキップします。  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 次のコード例では、`Skip While`句[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]文字列の最初の文字の中に、配列内の文字列をスキップするは、"a"です。 配列内の残りの文字列が返されます。  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 次のコード例では、`Take`句[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]文字列の配列の最初の 2 つの文字列を取得します。  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 次のコード例では、`Take While`句[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]文字列の長さが 5 個以下に、配列から文字列を取得します。  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq>  
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Skip 句](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Skip While 句](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take 句](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [Take While 句](../../../../visual-basic/language-reference/queries/take-while-clause.md)
