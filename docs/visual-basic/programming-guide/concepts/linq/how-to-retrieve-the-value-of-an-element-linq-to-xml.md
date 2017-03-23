---
title: "方法: 要素 (LINQ to XML) の値を取得 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 76b9b2a5-b3ba-49da-ba74-82100e1bd21c
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d38928df51006a8db9417d34ccbe6cd03091db66
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-visual-basic"></a>方法: 要素 (LINQ to XML) の値を取得 (Visual Basic)
このトピックでは、要素の値を取得する方法について説明します。 これには主に&2; つの方法があります。 キャストする方法の&1; つは、<xref:System.Xml.Linq.XElement>または<xref:System.Xml.Linq.XAttribute>を目的の型</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>。 その後、明示的な変換演算子によって、要素または属性のコンテンツが指定した型に変換され、変数に代入されます。 また、使用することができます、<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>プロパティまたは<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>プロパティ</xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>。  
  
 Visual Basic、最良のアプローチを使用するが、<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>プロパティ</xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>。  
  
## <a name="example"></a>例  
 要素の値を取得するには、キャスト、<xref:System.Xml.Linq.XElement>目的の型のオブジェクト</xref:System.Xml.Linq.XElement>。 次に示すように、要素はいつでも文字列にキャストできます。  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>例  
 文字列以外の型に要素をキャストすることもできます。 たとえば、次のコードに示すように、整数を含んだ要素を `int` にキャストできます。  
  
```vb  
Dim e As XElement = <Age>44</Age>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & CInt(e))  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]同様のキャスト演算子は、<xref:System.Xml.Linq.XAttribute>オブジェクト</xref:System.Xml.Linq.XAttribute>。  
  
## <a name="example"></a>例  
 使用することができます、<xref:System.Xml.Linq.XElement.Value%2A>要素の内容を取得するプロパティ</xref:System.Xml.Linq.XElement.Value%2A>。  
  
```vb  
Dim e As XElement = <StringElement>abcde</StringElement>  
Console.WriteLine(e)  
Console.WriteLine("Value of e:" & e.Value)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a>例  
 存在しているかどうかが明確でない要素の値の取得を試行する場合があります。 この場合は、キャストの要素を null 許容型に代入すると (どちらか`string`またはいずれかの null 許容型の[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]) 要素に割り当てられているが存在しない場合、変数が同じに設定されている`Nothing`します。 次のコードは、要素は、可能性がありますかが存在しないかが簡単であるよりもキャストを使用する、<xref:System.Xml.Linq.XElement.Value%2A>プロパティ</xref:System.Xml.Linq.XElement.Value%2A>。  
  
```vb  
Dim root As XElement = <Root>  
                           <Child1>child 1 content</Child1>  
                           <Child2>2</Child2>  
                       </Root>  
  
' The following assignments show why it is easier to use  
' casting when the element might or might not exist.  
  
Dim c1 As String = CStr(root.Element("Child1"))  
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element does not exist", c1))  
  
Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))  
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element does not exist", c2.ToString()))  
  
Dim c3 As String = CStr(root.Element("Child3"))  
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element does not exist", c3))  
  
Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))  
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element does not exist", c4.ToString()))  
  
Console.WriteLine()  
  
' The following assignments show the required code when using  
' the Value property when the attribute might or might not exist.  
' Notice that this is more difficult than the casting approach.  
  
Dim e1 As XElement = root.Element("Child1")  
Dim v1 As String  
If (e1 Is Nothing) Then  
    v1 = Nothing  
Else  
    v1 = e1.Value  
End If  
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element does not exist", v1))  
  
Dim e2 As XElement = root.Element("Child2")  
Dim v2 As Nullable(Of Integer)  
If (e2 Is Nothing) Then  
    v2 = Nothing  
Else  
    v2 = e2.Value  
End If  
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element does not exist", v2))  
  
Dim e3 As XElement = root.Element("Child3")  
Dim v3 As String  
If (e3 Is Nothing) Then  
    v3 = Nothing  
Else  
    v3 = e3.Value  
End If  
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element does not exist", v3))  
  
Dim e4 As XElement = root.Element("Child4")  
Dim v4 As Nullable(Of Integer)  
If (e4 Is Nothing) Then  
    v4 = Nothing  
Else  
    v4 = e4.Value  
End If  
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element does not exist", v4))  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 通常、要素や属性のコンテンツを取得するには、キャストを使用する方が単純なコードになります。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
