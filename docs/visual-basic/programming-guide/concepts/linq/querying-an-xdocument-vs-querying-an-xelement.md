---
title: "XDocument のクエリと (Visual Basic) XElement のクエリ |Microsoft ドキュメント"
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
ms.assetid: 2d111f84-0ded-4cde-8d93-5440557a726d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 29044cd118bfd8ecc12bddca722ee3656d455e0f
ms.lasthandoff: 03/13/2017


---
# <a name="querying-an-xdocument-vs-querying-an-xelement-visual-basic"></a>XDocument のクエリと (Visual Basic) XElement のクエリ
<xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>。</xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>を使用して読み込む場合よりも少し異なる方法でクエリを記述する必要があることを確認は、</xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>使用してドキュメントを読み込む場合  
  
## <a name="comparison-of-xdocumentload-and-xelementload"></a>XDocument.Load と XElement.Load の比較  
 XML ドキュメントを読み込む場合、<xref:System.Xml.Linq.XElement>経由で<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XElement>ツリーには XML のルートには、読み込んだドキュメントのルート要素が含まれています</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement>。 ただし、読み込む場合、同じ XML ドキュメントに、<xref:System.Xml.Linq.XDocument><xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>ツリーのルートの<xref:System.Xml.Linq.XDocument>ノードで、読み込んだドキュメントのルート要素は&1; つの許可されている子<xref:System.Xml.Linq.XElement><xref:System.Xml.Linq.XDocument>。</xref:System.Xml.Linq.XDocument>ノード</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XDocument>、</xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>使用して</xref:System.Xml.Linq.XDocument> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 軸は、ルート ノードを基準に動作します。  
  
 この最初の例は、 <xref:System.Xml.Linq.XElement.Load%2A>。</xref:System.Xml.Linq.XElement.Load%2A>を使用して XML ツリーを読み込みます 次に、ツリーのルートの子要素をクエリします。  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XElement.Load")  
Console.WriteLine("----")  
Dim doc As XElement = XElement.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 この例では、次の出力が生成されることが想定されます。  
  
```  
Querying tree loaded with XElement.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
 次の例は、1 つとして前、に、 <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>ではなく</xref:System.Xml.Linq.XDocument>XML ツリーが読み込まれている例外で同じ  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
</Root>  
```  
  
 この同じクエリでは、3 つの子ノードではなく&1; つの `Root` ノードが返されたことがわかります。  
  
 これに対処する方法の&1; つは、使用する、<xref:System.Xml.Linq.XDocument.Root%2A>軸メソッドを次のようにアクセスする前にプロパティ:</xref:System.Xml.Linq.XDocument.Root%2A>  
  
```vb  
' Create a simple document and  write it to a file  
File.WriteAllText("Test.xml", "<Root>" + Environment.NewLine + _  
    "    <Child1>1</Child1>" + Environment.NewLine + _  
    "    <Child2>2</Child2>" + Environment.NewLine + _  
    "    <Child3>3</Child3>" + Environment.NewLine + _  
    "</Root>")  
  
Console.WriteLine("Querying tree loaded with XDocument.Load")  
Console.WriteLine("----")  
Dim doc As XDocument = XDocument.Load("Test.xml")  
Dim childList As IEnumerable(Of XElement) = _  
        From el In doc.Root.Elements() _  
        Select el  
For Each e As XElement In childList  
    Console.WriteLine(e)  
Next  
```  
  
 このクエリは、同じようになりました実行<xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>ルートとすると、ツリーのクエリ方法。 この例では次の出力が生成されます。  
  
```  
Querying tree loaded with XDocument.Load  
----  
<Child1>1</Child1>  
<Child2>2</Child2>  
<Child3>3</Child3>  
```  
  
## <a name="see-also"></a>関連項目  
 [基本的なクエリ (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
