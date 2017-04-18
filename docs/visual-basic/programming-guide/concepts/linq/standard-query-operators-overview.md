---
title: "標準クエリ演算子の概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
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
ms.openlocfilehash: eb28988ef49e0583fb7e9197c4e13c84665074ac
ms.lasthandoff: 03/13/2017

---
# <a name="standard-query-operators-overview-visual-basic"></a>標準クエリ演算子の概要 (Visual Basic)
*標準クエリ演算子*メソッドの LINQ パターンを形成します。 これらのメソッドの大部分はシーケンスがある型を実装するオブジェクトは、シーケンスに対して機能、<xref:System.Collections.Generic.IEnumerable%601>インターフェイスまたは<xref:System.Linq.IQueryable%601>インターフェイス</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>。 標準クエリ演算子は、フィルター処理、投影、集計、並べ替えなどを含むクエリ機能を提供します。  
  
 いずれかの操作対象のオブジェクトの種類<xref:System.Collections.Generic.IEnumerable%601>とその他の<xref:System.Linq.IQueryable%601>。</xref:System.Linq.IQueryable%601>の種類のオブジェクトを操作</xref:System.Collections.Generic.IEnumerable%601>である LINQ 標準クエリ演算子の&2; つのセットがあります。 各セットを構成するメソッドが静的メンバーの<xref:System.Linq.Enumerable>と<xref:System.Linq.Queryable>クラスそれぞれ</xref:System.Linq.Queryable></xref:System.Linq.Enumerable>。 として定義されている*拡張メソッド*型上で動作するのです。 つまり、静的メソッドの構文またはインスタンス メソッドの構文を使用して呼び出すことがあります。  
  
 さらに、いくつかの標準クエリ演算子メソッド操作<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>に基づいて作成された以外の型 <xref:System.Linq.Enumerable>型は、このような&2; つのメソッドを定義が両方とも<xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable>の種類のオブジェクトを対象</xref:System.Linq.Enumerable> これらのメソッドを<xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29>と<xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>に、LINQ パターンでクエリを実行するパラメーターのない、または非ジェネリック コレクションを有効にします</xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29></xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29>。 厳密に型指定されたオブジェクトのコレクションを作成することで行います。 <xref:System.Linq.Queryable>クラス<xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29>と<xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29><xref:System.Linq.Queryable>。</xref:System.Linq.Queryable>の種類のオブジェクトで動作する、</xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29>&2; つのようなメソッドを定義</xref:System.Linq.Queryable>する  
  
 標準クエリ演算子は、シングルトン値または値のシーケンスを返しているかどうかに応じて、実行のタイミングは異なります。 シングルトン値を返すメソッド (たとえば、<xref:System.Linq.Enumerable.Average%2A>と<xref:System.Linq.Enumerable.Sum%2A>) をすぐに実行します</xref:System.Linq.Enumerable.Sum%2A></xref:System.Linq.Enumerable.Average%2A>。 シーケンスを返すメソッドは、クエリの実行を延期して、列挙可能なオブジェクトを取得します。  
  
 これらを拡張するメソッドは、メモリ内コレクションに対して実行されるメソッドの場合<xref:System.Collections.Generic.IEnumerable%601>、返された列挙可能なオブジェクトは、メソッドに渡された引数をキャプチャします</xref:System.Collections.Generic.IEnumerable%601>。 そのオブジェクトを列挙した場合にクエリ演算子のロジックが採用されているし、クエリの結果が返されます。  
  
 これに対し、メソッドを拡張する<xref:System.Linq.IQueryable%601>、クエリの動作を実装していませんが、実行するクエリを表す式ツリーを構築します</xref:System.Linq.IQueryable%601>。 クエリ処理は、ソースによって処理<xref:System.Linq.IQueryable%601>オブジェクト</xref:System.Linq.IQueryable%601>。  
  
 クエリ メソッドへの呼び出しは、によりクエリには任意に複雑になる&1; つのクエリに連結できます。  
  
 次のコード例では、標準クエリ演算子を使用して、シーケンスに関する情報を取得する方法を示します。  
  
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
  
## <a name="query-expression-syntax"></a>クエリ式の構文  
 頻繁に使用される標準クエリ演算子のいくつか専用の一部として呼び出せるようにする c# および Visual Basic の言語キーワード構文のある、*クエリ**式*します。 専用のキーワードと対応する構文では、標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子 (Visual Basic) のクエリ式構文](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)します。  
  
## <a name="extending-the-standard-query-operators"></a>標準クエリ演算子の拡張  
 移行先ドメインまたはテクノロジの適切な作成のドメイン固有のメソッドによって、標準クエリ演算子のセットを強化できます。 リモートの評価、クエリの変換、および最適化などの他のサービスを提供する、独自の実装と共に、標準クエリ演算子を置き換えることもできます。 参照してください<xref:System.Linq.Enumerable.AsEnumerable%2A>例については、</xref:System.Linq.Enumerable.AsEnumerable%2A> 。  
  
## <a name="related-sections"></a>関連項目  
 次のリンクでは、機能に基づいて、さまざまな標準クエリ演算子に関する追加情報を提供するトピックへ移動します。  
  
 [データの並べ替え](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [集合演算 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [データのフィルター処理 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [量指定子操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [射影操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [データのパーティション分割 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [結合操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [データのグループ化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [生成操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [等値演算 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [要素操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [データ型 (Visual Basic) に変換します。](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [連結演算 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [集計操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 <xref:System.Linq.Queryable></xref:System.Linq.Queryable>   
 [LINQ (Visual Basic) の概要](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)   
 [標準クエリ演算子 (Visual Basic) のクエリ式の構文](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)   
 [(Visual Basic) の実行方法による標準クエリ演算子の分類](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)   
 [拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
