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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: af870389e34dd480e3db9a09bdffd2d3998747a1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="c3b65-102">方法: XmlWriter (LINQ to XML) を使用して XML ツリーを作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c3b65-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="c3b65-103">XML ツリーを設定する方法の&1; つを使用して<xref:System.Xml.Linq.XContainer.CreateWriter%2A>を作成する、 <xref:System.Xml.XmlWriter>、 <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter>に書き込む</xref:System.Xml.XmlWriter></xref:System.Xml.Linq.XContainer.CreateWriter%2A></span><span class="sxs-lookup"><span data-stu-id="c3b65-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="c3b65-104">XML ツリーには、 <xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter>に書き込まれるすべてのノードが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="c3b65-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="c3b65-105">使用するときに通常、このメソッドを使用する[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]への書き込みに必要とする別のクラスで、 <xref:System.Xml.XmlWriter>、 <xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform>など</xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="c3b65-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3b65-106">例</span><span class="sxs-lookup"><span data-stu-id="c3b65-106">Example</span></span>  
 <span data-ttu-id="c3b65-107">用途の&1; つ<xref:System.Xml.Linq.XContainer.CreateWriter%2A>は XSLT 変換を呼び出すときに</xref:System.Xml.Linq.XContainer.CreateWriter%2A>。</span><span class="sxs-lookup"><span data-stu-id="c3b65-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="c3b65-108">この例では、XML ツリーを作成して、作成、 <xref:System.Xml.XmlReader>XML ツリーから、新しいドキュメントを作成し、作成、<xref:System.Xml.XmlWriter>に新しいドキュメントに書き込む</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="c3b65-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="c3b65-109">次に<xref:System.Xml.XmlReader><xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>を渡して、XSLT 変換を呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="c3b65-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="c3b65-110">変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="c3b65-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="c3b65-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c3b65-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3b65-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3b65-112">See Also</span></span>  
 <span data-ttu-id="c3b65-113"><xref:System.Xml.Linq.XContainer.CreateWriter%2A></xref:System.Xml.Linq.XContainer.CreateWriter%2A></span><span class="sxs-lookup"><span data-stu-id="c3b65-113"><xref:System.Xml.Linq.XContainer.CreateWriter%2A></span></span>   
 <span data-ttu-id="c3b65-114"><xref:System.Xml.XmlWriter></xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="c3b65-114"><xref:System.Xml.XmlWriter></span></span>   
 <span data-ttu-id="c3b65-115"><xref:System.Xml.Xsl.XslCompiledTransform></xref:System.Xml.Xsl.XslCompiledTransform></span><span class="sxs-lookup"><span data-stu-id="c3b65-115"><xref:System.Xml.Xsl.XslCompiledTransform></span></span>   
<span data-ttu-id="c3b65-116"> [XML ツリー (Visual Basic) の作成](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)</span><span class="sxs-lookup"><span data-stu-id="c3b65-116"> [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)</span></span>
