---
title: "Visual Basic2 内の XML リテラルの概要 |Microsoft ドキュメント"
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
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
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
ms.openlocfilehash: 391dd14f971f91d4d128841a7ebd24981266846a
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-xml-literals-in-visual-basic"></a>Visual Basic の XML リテラルの概要
ここでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] での XML ツリーの作成について説明します。  
  
 LINQ クエリの結果をコンテンツとして XML ツリーの使用方法の詳細については、次を参照してください。[関数型構築 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)します。  
  
 詳細については、XML リテラルの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を参照してください[概要の LINQ to Visual Basic で XML](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)します。  
  
## <a name="creating-xml-trees"></a>XML ツリーの作成  
 次の例では、作成する方法、 <xref:System.Xml.Linq.XElement>、ここで`contacts`:</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
### <a name="creating-an-xelement-with-simple-content"></a>単純コンテンツを持つ XElement の作成  
 作成することができます、<xref:System.Xml.Linq.XElement>次のように、単純コンテンツを含む:</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a>空要素の作成  
 空を作成する<xref:System.Xml.Linq.XElement>、次のように:</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a>組み込み式の使用  
 XML リテラルの重要な機能は、組み込み式を利用できることです。 組み込み式を使用すると、式を評価してその式の結果を XML ツリーに挿入できます。 型に式が評価された場合に<xref:System.Xml.Linq.XElement>、要素がツリーに挿入します</xref:System.Xml.Linq.XElement>。 型に式が評価された場合に<xref:System.Xml.Linq.XAttribute>、属性がツリーに挿入します</xref:System.Xml.Linq.XAttribute>。 要素および属性は、それらが有効となるツリーにのみ挿入できます。  
  
 組み込み式に含めることができるのは&1; つの式だけであることに注意してください。 複数のステートメントを組み込むことはできません。 式が複数の行にまたがる場合は、行連結文字を使用する必要があります。  
  
 組み込み式を使用して既存のノード (要素を含む) や属性を新しい XML ツリーに追加する場合に、その既存のノードに既に親があるときは、ノードが複製されます。 新しく複製されたノードは、新しい XML ツリーにアタッチされます。 既存のノードに親がない場合は、単にノードが新しい XML ツリーにアタッチされます。 このトピックの最後の例では、この動作について説明します。  
  
 次の例では、組み込み式を使用して要素をツリーに挿入します。  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a>コンテンツに対する組み込み式の使用  
 組み込み式を使用して要素のコンテンツを指定できます。  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a>組み込み式での LINQ クエリの使用  
 要素のコンテンツに対する LINQ クエリの結果を使用できます。  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a>ノード名に対する組み込み式の使用  
 組み込み式を使用して、属性名、属性値、要素名、および要素値を計算することもできます。  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a>複製とアタッチ  
 既に説明したとおり、組み込み式を使用して既存のノード (要素を含む) や属性を新しい XML ツリーに追加する場合に、その既存のノードに既に親があるときは、ノードが複製され、新しく複製されたノードが新しい XML ツリーにアタッチされます。 既存のノードに親がない場合は、単にノードが新しい XML ツリーにアタッチされます。  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ツリー (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
