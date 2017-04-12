---
title: "集計操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
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
ms.openlocfilehash: 17d1f18f9acc2f3a62c106f7cff2cf68f8f58a07
ms.lasthandoff: 03/13/2017

---
# <a name="aggregation-operations-visual-basic"></a>集計操作 (Visual Basic)
集計の操作では、値の集合体から単一の値が計算されます。 たとえば、1 か月分の毎日の気温値から&1; 日あたりの平均の気温値を計算することが集計操作です。  
  
 次の図は、数値のシーケンスに対して次の&2; つの異なる集計操作の結果を示します。 最初の操作は、数値を合計します。 2 番目の操作は、シーケンスの最大値を返します。  
  
 ![LINQ 集計操作](../../../../csharp/programming-guide/concepts/linq/media/linq_aggregation.png "LINQ_Aggregation")  
  
 集計操作を実行する標準クエリ演算子メソッドは、次のように記載されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Aggregate|コレクションの値をカスタム集計操作を実行します。|該当なし。|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=fullName></xref:System.Linq.Queryable.Aggregate%2A?displayProperty=fullName>|  
|平均|値のコレクションの平均値を計算します。|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Average%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=fullName></xref:System.Linq.Queryable.Average%2A?displayProperty=fullName>|  
|カウント|必要に応じて要素のみを述語関数を満たすコレクションでは、要素の数をカウントします。|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=fullName></xref:System.Linq.Queryable.Count%2A?displayProperty=fullName>|  
|LongCount|必要に応じて要素のみを述語関数を満たす大規模なコレクションの要素の数をカウントします。|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=fullName></xref:System.Linq.Enumerable.LongCount%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=fullName></xref:System.Linq.Queryable.LongCount%2A?displayProperty=fullName>|  
|最大|コレクション内の最大値を決定します。|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Max%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=fullName></xref:System.Linq.Queryable.Max%2A?displayProperty=fullName>|  
|最小|コレクション内の最小値を決定します。|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Min%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=fullName></xref:System.Linq.Queryable.Min%2A?displayProperty=fullName>|  
|Sum|コレクション内の値の合計を計算します。|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Sum%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=fullName></xref:System.Linq.Queryable.Sum%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>クエリ式の構文例  
  
### <a name="average"></a>Average  
 次のコード例では、`Aggregate Into Average`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]温度を表す数値の配列での平均の気温を計算します。  
  
 [!code-vb[CsLINQAggregating&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_1.vb)]  
  
### <a name="count"></a>カウント  
 次のコード例では、`Aggregate Into Count`句[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]80 以上である、配列の値の数をカウントします。  
  
 [!code-vb[CsLINQAggregating&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_2.vb)]  
  
### <a name="longcount"></a>LongCount  
 次のコード例では、`Aggregate Into LongCount`句、配列の値の数をカウントします。  
  
 [!code-vb[CsLINQAggregating&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_3.vb)]  
  
### <a name="max"></a>最大  
 次のコード例では、`Aggregate Into Max`温度を表す数値の配列内の最高温度を計算する句。  
  
 [!code-vb[CsLINQAggregating&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_4.vb)]  
  
### <a name="min"></a>最小  
 次のコード例では、`Aggregate Into Min`温度を表す数値の配列で最小の温度を計算する句。  
  
 [!code-vb[CsLINQAggregating&#5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_5.vb)]  
  
### <a name="sum"></a>Sum  
 次のコード例では、`Aggregate Into Sum`経費を表す値の配列から経費合計金額を計算する句。  
  
 [!code-vb[CsLINQAggregating&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/aggregation-operations_6.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [方法: CSV テキスト ファイル (LINQ) (Visual Basic) の列の値を計算](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)   
 [方法: カウント、合計、または平均のデータ](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)   
 [方法: クエリ結果内の最小値と最大値の検索](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)   
 [方法: ファイルまたはディレクトリ ツリー (LINQ) (Visual Basic) 内のファイル サイズの大きい照会](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)   
 [方法: 一連のフォルダー (LINQ) (Visual Basic) のバイト数の合計数を問い合わせる](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
