---
title: "データ型 (Visual Basic) に変換する |Microsoft ドキュメント"
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
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
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
ms.openlocfilehash: 53d8ad292891a567e13ec8a5396bcc114b379351
ms.lasthandoff: 03/13/2017

---
# <a name="converting-data-types-visual-basic"></a>データ型 (Visual Basic) に変換します。
変換メソッドは、入力オブジェクトの種類を変更します。  
  
 変換操作は、LINQ クエリでは、さまざまなアプリケーションで役立ちます。 いくつかの例を次に示します。  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>メソッドは、標準クエリ演算子の型のカスタム実装を非表示にするために使用できます</xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>。  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>の LINQ クエリのコレクションの非パラメーター化を有効にするメソッドを使用できます</xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName>。  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>、 <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>、 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>、および<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>メソッドは、クエリが列挙されるまで遅延させることではなく、クエリの即時実行を強制するために使用できます</xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>。  
  
## <a name="methods"></a>メソッド  
 次の表は、データ型変換を実行する標準クエリ演算子メソッドを一覧表示します。  
  
 このテーブルの"As"で始まる名前の変換メソッドは、ソース コレクションの静的な型の変更が、列挙しません。 "To ソース コレクションを列挙し、それらの項目を対応するコレクション"で始まる名前のメソッドを入力します。  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|<xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601>として型指定された入力を返します|該当なし。|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName></xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=fullName>|  
|AsQueryable|変換する (汎用) <xref:System.Collections.IEnumerable> <xref:System.Linq.IQueryable>。</xref:System.Linq.IQueryable> (汎用)</xref:System.Collections.IEnumerable>|該当なし。|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName></xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>|  
|Cast|指定した型のコレクションの要素をキャストします。|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Cast%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName></xref:System.Linq.Queryable.Cast%2A?displayProperty=fullName>|  
|OfType|指定した型にキャストするかどうかによって、値をフィルター処理します。|該当なし。|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|ToArray|コレクションを配列に変換します。 このメソッドは、クエリの実行を強制します。|該当なし。|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToArray%2A?displayProperty=fullName>|  
|ToDictionary|要素を配置、<xref:System.Collections.Generic.Dictionary%602>されたキー セレクター関数に基づいて</xref:System.Collections.Generic.Dictionary%602>。 このメソッドは、クエリの実行を強制します。|該当なし。|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=fullName>|  
|ToList|<xref:System.Collections.Generic.List%601>。</xref:System.Collections.Generic.List%601>コレクションに変換します このメソッドは、クエリの実行を強制します。|該当なし。|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>|  
|ToLookup|要素を配置、<xref:System.Linq.Lookup%602>されたキー セレクター関数に基づいて、(一対多辞書).</xref:System.Linq.Lookup%602> このメソッドは、クエリの実行を強制します。|該当なし。|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>クエリ式の構文例  
 次のコード例では、`From As`のサブタイプでのみ使用可能なメンバーにアクセスする前にサブタイプの型をキャストする句。  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [From 句](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [方法: クエリ、LINQ で ArrayList を (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
