---
title: '方法: クエリを記述複雑なフィルター (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: bf286ffc-7990-4b00-a4eb-ee3d70129950
ms.openlocfilehash: 500cd9cdc62252eff3addc26006c4ce815ae1b4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645864"
---
# <a name="how-to-write-queries-with-complex-filtering-visual-basic"></a>方法: クエリを記述複雑なフィルター (Visual Basic)
複雑なフィルターを使用して LINQ to XML クエリを記述することが必要になる場合があります。 たとえば、特定の名前と値を持つ子要素を含む要素をすべて検索しなければならない場合があります。 このトピックでは、複雑なフィルターを使用してクエリを記述する例について説明します。  
  
## <a name="example"></a>例  
 この例では、`PurchaseOrder` 属性が "Shipping" で `Address` 子要素が "NY" である `Type` 子要素を含む `State` 要素をすべて検索します。 この例では、入れ子になったクエリを `Where` 句で使用しています。コレクションに要素が含まれる場合、`Any` 演算子は `True` を返します。  
  
 この例では、「[サンプル XML ファイル: 複数の購買発注書 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)」の XML ドキュメントを使用します。  
  
 詳細については、`Any`演算子を参照してください[量指定子操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)です。  
  
```vb  
Dim root As XElement = XElement.Load("PurchaseOrders.xml")  
Dim purchaseOrders As IEnumerable(Of XElement) = _  
    From el In root.<PurchaseOrder> _  
    Where _  
        (From add In el.<Address> _  
        Where _  
             add.@Type = "Shipping" And _  
             add.<State>.Value = "NY" _  
        Select add) _  
    .Any() _  
    Select el  
For Each el As XElement In purchaseOrders  
    Console.WriteLine(el.@PurchaseOrderNumber)  
Next  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
99505  
```  
  
## <a name="example"></a>例  
 次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。 詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の操作](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)です。  
  
 この例では、「[サンプル XML ファイル: 名前空間内の複数の購買発注書](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)」の XML ドキュメントを使用します。  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("PurchaseOrdersInNamespace.xml")  
        Dim purchaseOrders As IEnumerable(Of XElement) = _  
            From el In root.<aw:PurchaseOrder> _  
            Where _  
                (From add In el.<aw:Address> _  
                Where _  
                     add.@aw:Type = "Shipping" And _  
                     add.<aw:State>.Value = "NY" _  
                Select add) _  
            .Any() _  
            Select el  
        For Each el As XElement In purchaseOrders  
            Console.WriteLine(el.@aw:PurchaseOrderNumber)  
        Next  
    End Sub  
End Module  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
99505  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XElement.Attribute%2A>  
 <xref:System.Xml.Linq.XContainer.Elements%2A>  
 [基本的なクエリ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)  
 [XML 子軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)  
 [XML Value プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [射影操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
 [量指定子操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)
