---
title: "方法: XML ツリー全体 (Visual Basic) の Namespace の変更 |Microsoft ドキュメント"
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
ms.assetid: 1837324b-5cb5-4fa8-95b9-3071efa0f913
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: af216e734c85806056e37d92733a3e4d49f8b73c
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-change-the-namespace-for-an-entire-xml-tree-visual-basic"></a>方法: Namespace、全体 XML ツリーの変更 (Visual Basic)
要素または属性の名前空間をプログラムで変更しなければならない場合があります。 LINQ to XML では、この操作を簡単に行うことができます。 <xref:System.Xml.Linq.XElement.Name%2A?displayProperty=fullName>プロパティを設定することができます</xref:System.Xml.Linq.XElement.Name%2A?displayProperty=fullName>。 <xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=fullName>プロパティを設定することはできませんに属性を簡単にコピーすることができます、 <xref:System.Collections.Generic.List%601?displayProperty=fullName>、既存の属性を削除してから目的の新しい名前空間に含まれる新しい属性を追加します</xref:System.Collections.Generic.List%601?displayProperty=fullName></xref:System.Xml.Linq.XAttribute.Name%2A?displayProperty=fullName>。  
  
 詳細については、次を参照してください。 [XML 名前空間 (Visual Basic) の使用](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)します。  
  
## <a name="example"></a>例  
 次のコードは、名前空間に含まれない&2; つの XML ツリーを作成します。 次に、各ツリーの名前空間を変更して、1 つのツリーに結合します。  
  
```vb  
Dim tree1 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim tree2 As XElement = _  
    <Data>  
        <Child MyAttr="content">content</Child>  
    </Data>  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim ad As XNamespace = "http://www.adatum.com"  
' change the namespace of every element and attribute in the first tree  
For Each el As XElement In tree1.DescendantsAndSelf  
    el.Name = aw.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(aw.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' change the namespace of every element and attribute in the second tree  
For Each el As XElement In tree2.DescendantsAndSelf()  
    el.Name = ad.GetName(el.Name.LocalName)  
    Dim atList As List(Of XAttribute) = el.Attributes().ToList()  
    el.Attributes().Remove()  
    For Each at As XAttribute In atList  
        el.Add(New XAttribute(ad.GetName(at.Name.LocalName), at.Value))  
    Next  
Next  
' add attribute namespaces so that the tree will be serialized with  
' the aw and ad namespace prefixes  
tree1.Add( _  
    New XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com") _  
)  
tree2.Add( _  
    New XAttribute(XNamespace.Xmlns + "ad", "http://www.adatum.com") _  
)  
' create a new composite tree  
Dim root As XElement = _  
    <Root>  
        <%= tree1 %>  
        <%= tree2 %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <aw:Data xmlns:aw="http://www.adventure-works.com">  
    <aw:Child aw:MyAttr="content">content</aw:Child>  
  </aw:Data>  
  <ad:Data xmlns:ad="http://www.adatum.com">  
    <ad:Child ad:MyAttr="content">content</ad:Child>  
  </ad:Data>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目  
 [XML ツリー (LINQ to XML) の変更 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
