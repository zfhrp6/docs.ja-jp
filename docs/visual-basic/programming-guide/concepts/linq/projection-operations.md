---
title: "射影操作 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
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
ms.openlocfilehash: 8876e65e752e0b18404ec32aecdcad7805533840
ms.lasthandoff: 03/13/2017

---
# <a name="projection-operations-visual-basic"></a>射影操作 (Visual Basic)
射影は、多くの場合のみで構成される、後で使用されるこれらのプロパティを新しいフォームにオブジェクトを変換する処理を指します。 射影を使用することにより、個々のオブジェクトから構築された新しい型を作成できます。 プロパティを投影し、それに数学関数を実行できます。 これを変更することがなく、元のオブジェクトを射影することもできます。  
  
 射影を実行する標準クエリ演算子メソッドは、次のように記載されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド名|説明|Visual Basic のクエリ式の構文|説明|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|選択|変換関数に基づくプロジェクト値です。|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Select%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=fullName></xref:System.Linq.Queryable.Select%2A?displayProperty=fullName>|  
|SelectMany|変換関数に基づいており、その&1; つのシーケンスへの射影する値のシーケンスを射影します。|複数回使用`From`句|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName></xref:System.Linq.Queryable.SelectMany%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>クエリ式の構文例  
  
### <a name="select"></a>[選択]  
 次の例では、`Select`文字列のリスト内の各文字列から先頭の文字を射影する句。  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a>SelectMany  
 次のコードの例では、複数`From`文字列のリスト内の各文字列から各単語を射影する句。  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a>SelectMany と選択します。  
 両方の作業`Select()`と`SelectMany()`ソースの値から結果値 (または値) を作成することです。 `Select()`ソース値ごとに&1; つの結果値を生成します。 全体の結果は、ソース コレクションと同じ数の要素のコレクションではこのためです。 これに対し、`SelectMany()`を各ソース値から、連結されたサブ コレクションを含む単一の全体的な結果が生成されます。 変換関数に渡す引数として渡される`SelectMany()`の各ソース値の値の列挙可能なシーケンスを返す必要があります。 これらの列挙可能なシーケンスに連結して`SelectMany()`大きな&1; つのシーケンスを作成します。  
  
 次の&2; つの図は、これら&2; つのメソッドのアクションの概念の違いを示しています。 各ケースでは、セレクター (変換) 関数が、各ソース値から花の配列を選択することを仮定します。  
  
 この図を示して 方法`Select()`をソース コレクションと同じ数の要素を持つコレクションを返します。  
  
 ![Select() のアクションの概念を示す図](../../../../csharp/programming-guide/concepts/linq/media/selectaction.png "SelectAction")  
  
 この図を示して 方法`SelectMany()`各中間配列から各値を含む&1; つの最終的な結果値に中間一連の配列を連結します。  
  
 ![SelectMany() のアクションを示すグラフィック。] (../../../../csharp/programming-guide/concepts/linq/media/selectmany.png "SelectMany")  
  
### <a name="code-example"></a>コード例  
 次の例の動作を比較する`Select()`と`SelectMany()`です。 コードは、ソース コレクション内のそれぞれの花の名前の一覧から最初の&2; つの項目を実行することで、花の「いつも」を作成します。 この例は、「単一の値」でを変換関数は、<xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>はそれ自体が値のコレクション</xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29>。 余分な必要があります`For Each`各サブ シーケンス内の各文字列を列挙するためにループします。  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Linq></xref:System.Linq>   
 [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)   
 [方法: 結合を使用したデータを結合](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)   
 [方法: 複数のソース (LINQ) (Visual Basic の場合) からオブジェクトのコレクション設定](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)   
 [方法: 特定の種類での LINQ クエリ結果を返す](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)   
 [方法: 多くのファイルのファイル グループ (LINQ) (Visual Basic) を使用して分割](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
