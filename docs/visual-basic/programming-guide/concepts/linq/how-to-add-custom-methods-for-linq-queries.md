---
title: "方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加 |Microsoft ドキュメント"
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
ms.assetid: 099b2e2a-83cd-45c6-aa4d-01b398b5faaf
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
ms.openlocfilehash: 166eb731d41e009c374ba55f929eed302793ecd0
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-add-custom-methods-for-linq-queries-visual-basic"></a>方法: LINQ クエリ (Visual Basic) のカスタム メソッドを追加
LINQ クエリを使用する拡張メソッドを追加することでメソッドのセットを拡張する、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。 たとえば、だけでなく、標準的な平均または操作の最大数は、値のシーケンスから単一の値を計算する場合は、カスタム集計メソッドを作成できます。 カスタム フィルターまたは一連の値の変換を特定のデータとして機能し、新しいシーケンスを返すメソッドを作成することもできます。 このようなメソッドの例としては<xref:System.Linq.Enumerable.Distinct%2A>、 <xref:System.Linq.Enumerable.Skip%2A>、 <xref:System.Linq.Enumerable.Reverse%2A>.</xref:System.Linq.Enumerable.Reverse%2A> </xref:System.Linq.Enumerable.Skip%2A> </xref:System.Linq.Enumerable.Distinct%2A>  
  
 拡張すると、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス、列挙可能なコレクションにカスタム メソッドを適用することができます</xref:System.Collections.Generic.IEnumerable%601>。 詳細については、次を参照してください。[拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)します。  
  
## <a name="adding-an-aggregate-method"></a>集計メソッドの追加  
 集計メソッドは、一連の値から単一の値を計算します。 LINQ を含むいくつかの集計メソッドを提供する<xref:System.Linq.Enumerable.Average%2A>、 <xref:System.Linq.Enumerable.Min%2A>、 <xref:System.Linq.Enumerable.Max%2A>.</xref:System.Linq.Enumerable.Max%2A> </xref:System.Linq.Enumerable.Min%2A> </xref:System.Linq.Enumerable.Average%2A> 拡張メソッドを追加することで、独自の集計メソッドを作成することができます、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。  
  
 次のコード例は、という拡張メソッドを作成する方法を示しています。`Median`型の数値のシーケンスの中央値を計算する`double`です。  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module LINQExtension  
  
    ' Extension method for the IEnumerable(of T) interface.   
    ' The method accepts only values of the Double type.  
    <Extension()>   
    Function Median(ByVal source As IEnumerable(Of Double)) As Double  
        If source.Count = 0 Then  
            Throw New InvalidOperationException("Cannot compute median for an empty set.")  
        End If  
  
        Dim sortedSource = From number In source   
                           Order By number  
  
        Dim itemIndex = sortedSource.Count \ 2  
  
        If sortedSource.Count Mod 2 = 0 Then  
            ' Even number of items in list.  
            Return (sortedSource(itemIndex) + sortedSource(itemIndex - 1)) / 2  
        Else  
            ' Odd number of items in list.  
            Return sortedSource(itemIndex)  
        End If  
    End Function  
End Module  
```  
  
 他の集計メソッドを呼び出すのと同じ方法で、列挙可能なコレクションに対してこの拡張メソッドを呼び出す、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス</xref:System.Collections.Generic.IEnumerable%601>。  
  
> [!NOTE]
>  Visual Basic ではできますか、または使用するメソッドの呼び出しの標準的なクエリ構文、`Aggregate`または`Group By`句。 詳細については、次を参照してください。 [Aggregate 句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ By 句](../../../../visual-basic/language-reference/queries/group-by-clause.md)します。  
  
 次のコード例を使用する方法を示しています、`Median`型の配列をメソッド`double`します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>さまざまな種類をそのまま使用する集計メソッドのオーバー ロード  
 さまざまな種類のシーケンスを受け入れるように、集計メソッドをオーバー ロードできます。 標準的なアプローチでは、各種類のオーバー ロードを作成します。 別の方法では、ジェネリック型を受け取るはデリゲートを使用して、特定の種類に変換するオーバー ロードを作成します。 どちらの方法を組み合わせることもできます。  
  
#### <a name="to-create-an-overload-for-each-type"></a>各種類のオーバー ロードを作成するには  
 サポートする各種類の特定のオーバー ロードを作成することができます。 次のコード例のオーバー ロードを示しています、`Median`のメソッド、`integer`型です。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 呼び出せるように、`Median`両方のオーバー ロード`integer`と`double`型の場合、次のコードに示すようにします。  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
#### <a name="to-create-a-generic-overload"></a>ジェネリック オーバー ロードを作成するには  
 汎用オブジェクトのシーケンスを受け入れるオーバー ロードを作成することもできます。 このオーバー ロードは、パラメーターとしてデリゲートを受け取るし、それを使用してジェネリック型のオブジェクトのシーケンスを特定の種類に変換します。  
  
 次のコードはのオーバー ロード、`Median`を受け取るメソッド、<xref:System.Func%602>をパラメーターとしてデリゲートします</xref:System.Func%602>。 このデリゲートがジェネリック型 T のオブジェクトを受け取るし、型のオブジェクトを返します`double`します。  
  
```vb  
' Generic overload.  
  
<Extension()>   
Function Median(Of T)(ByVal source As IEnumerable(Of T),   
                      ByVal selector As Func(Of T, Double)) As Double  
    Return Aggregate num In source Select selector(num) Into med = Median()  
End Function  
```  
  
 呼び出せるように、`Median`任意の型のオブジェクトの順序のメソッドです。 型が、独自のメソッド オーバー ロードを持たない場合に、デリゲートのパラメーターを渡す必要あります。 Visual basic では、この目的のため、ラムダ式を使用できます。 また、使用する場合、`Aggregate`または`Group By`句メソッドの呼び出しではなく、任意の値またはこの句は、スコープ内の式を渡すことができます。  
  
 次のコード例を呼び出す方法を示します、`Median`方法の整数の配列と文字列の配列。 文字列の場合は、配列内の文字列の長さの中央値が計算されます。 渡す方法の例、<xref:System.Func%602>にパラメーターをデリゲート、`Median`各ケースのメソッドです</xref:System.Func%602>。  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
## <a name="adding-a-method-that-returns-a-collection"></a>コレクションを返すメソッドを追加します。  
 拡張する、<xref:System.Collections.Generic.IEnumerable%601>を一連の値を返すカスタム クエリ メソッドを持つインターフェイスです</xref:System.Collections.Generic.IEnumerable%601>。 この場合、メソッドが型<xref:System.Collections.Generic.IEnumerable%601>。</xref:System.Collections.Generic.IEnumerable%601>のコレクションを返す必要があります。 値のシーケンスをフィルターまたはデータ変換を適用するのには、このようなメソッドを使用できます。  
  
 次の例は、という名前の拡張メソッドを作成する方法を示しています。`AlternateElements`最初の要素を起点として、コレクション内のその他のすべての要素を返します。  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 他のメソッドを呼び出すと同様に、列挙可能なコレクションに対してこの拡張メソッドを呼び出すことができます、<xref:System.Collections.Generic.IEnumerable%601>次のコードに示すように、インターフェイス:</xref:System.Collections.Generic.IEnumerable%601>  
  
```vb  
Dim strings() As String = {"a", "b", "c", "d", "e"}  
  
Dim query = strings.AlternateElements()  
  
For Each element In query  
    Console.WriteLine(element)  
Next  
  
' This code produces the following output:  
'  
' a  
' c  
' e  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 [拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
