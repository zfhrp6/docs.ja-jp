---
title: "XSLT を使用して XML ツリー (Visual Basic) を変換する |Microsoft ドキュメント"
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
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 860f6b9debae37059bb15ad6bb5de2ed6f9292cb
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a><span data-ttu-id="b9320-102">XSLT を使用して XML ツリー (Visual Basic) を変換するには</span><span class="sxs-lookup"><span data-stu-id="b9320-102">Using XSLT to Transform an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="b9320-103">XML ツリーを作成したり、作成できます、 <xref:System.Xml.XmlReader>XML ツリーから、新しいドキュメントを作成し、作成、<xref:System.Xml.XmlWriter>ですが、新しいドキュメントに書き込む</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="b9320-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="b9320-104">次に、渡す、XSLT 変換を呼び出すことができます、<xref:System.Xml.XmlReader>と<xref:System.Xml.XmlWriter>に変換します</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="b9320-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="b9320-105">変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="b9320-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9320-106">例</span><span class="sxs-lookup"><span data-stu-id="b9320-106">Example</span></span>  
  
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
  
Dim xmlTree As XElement = _   
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = _  
        New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 <span data-ttu-id="b9320-107">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="b9320-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9320-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9320-108">See Also</span></span>  
 <span data-ttu-id="b9320-109"><xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b9320-109"><xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="b9320-110"><xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=fullName></xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b9320-110"><xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="b9320-111"> [高度な LINQ to XML のプログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)</span><span class="sxs-lookup"><span data-stu-id="b9320-111"> [Advanced LINQ to XML Programming (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)</span></span>
