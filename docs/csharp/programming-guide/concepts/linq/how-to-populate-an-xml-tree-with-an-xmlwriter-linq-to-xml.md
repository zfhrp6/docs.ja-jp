---
title: "方法: XmlWriter を使用して XML ツリーを設定する (LINQ to XML) (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 225aa8a39a973ba8d4f199ccfce68e2dc16d8aa2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-c"></a>方法: XmlWriter を使用して XML ツリーを設定する (LINQ to XML) (C#)
XML ツリーを設定する方法の 1 つに、<xref:System.Xml.Linq.XContainer.CreateWriter%2A> を使用して <xref:System.Xml.XmlWriter> を作成し、その <xref:System.Xml.XmlWriter> に書き込むという方法があります。 XML ツリーには、<xref:System.Xml.XmlWriter> に書き込まれたすべてのノードが挿入されます。  
  
 通常この方法は、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] と、<xref:System.Xml.XmlWriter> への書き込みを必要とする別のクラス (<xref:System.Xml.Xsl.XslCompiledTransform> など) を併用する場合に使用します。  
  
## <a name="example"></a>例  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> は、XSLT 変換を呼び出すときに使用できます。 この例では、XML ツリーを作成し、この XML ツリーから <xref:System.Xml.XmlReader> を作成して、新しいドキュメントを作成します。次に、この新しいドキュメントに書き込むための <xref:System.Xml.XmlWriter> を作成します。 その後、XSLT 変換を呼び出して、<xref:System.Xml.XmlReader> と <xref:System.Xml.XmlWriter> を渡します。 変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
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
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter())  
{  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>   
 <xref:System.Xml.XmlWriter>   
 <xref:System.Xml.Xsl.XslCompiledTransform>   
 [XML ツリーの作成 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
