---
title: "方法: XmlWriter (LINQ to XML) を使用して XML ツリーを作成 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
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
ms.openlocfilehash: dfd10ec04e7293d90929d6f629201868028819ad
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a>方法: XmlWriter (LINQ to XML) を使用して XML ツリーを作成 (Visual Basic)
XML ツリーを設定する方法の&1; つを使用して<xref:System.Xml.Linq.XContainer.CreateWriter%2A>を作成する、 <xref:System.Xml.XmlWriter>、 <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>に書き込む</xref:System.Xml.XmlWriter></xref:System.Xml.Linq.XContainer.CreateWriter%2A> XML ツリーには、 <xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter>に書き込まれるすべてのノードが挿入されます。  
  
 使用するときに通常、このメソッドを使用する[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]への書き込みに必要とする別のクラスで、 <xref:System.Xml.XmlWriter>、 <xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform>など</xref:System.Xml.XmlWriter>  
  
## <a name="example"></a>例  
 用途の&1; つ<xref:System.Xml.Linq.XContainer.CreateWriter%2A>は XSLT 変換を呼び出すときに</xref:System.Xml.Linq.XContainer.CreateWriter%2A>。 この例では、XML ツリーを作成して、作成、 <xref:System.Xml.XmlReader>XML ツリーから、新しいドキュメントを作成し、作成、<xref:System.Xml.XmlWriter>に新しいドキュメントに書き込む</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>。 次に<xref:System.Xml.XmlReader><xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>を渡して、XSLT 変換を呼び出してください。 変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>   
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A></xref:System.Xml.Linq.XContainer.CreateWriter%2A>   
 <xref:System.Xml.XmlWriter></xref:System.Xml.XmlWriter>   
 <xref:System.Xml.Xsl.XslCompiledTransform></xref:System.Xml.Xsl.XslCompiledTransform>   
 [XML ツリー (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
