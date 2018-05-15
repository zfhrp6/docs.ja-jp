---
title: '方法: XmlWriter (LINQ to XML) を XML ツリーを設定します (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
ms.openlocfilehash: bc17b84b945e93443ab6d9f337e852feba5b0662
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml-visual-basic"></a><span data-ttu-id="67914-102">方法: XmlWriter (LINQ to XML) を XML ツリーを設定します (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67914-102">How to: Populate an XML Tree with an XmlWriter (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="67914-103">XML ツリーを設定する方法の 1 つは、<xref:System.Xml.Linq.XContainer.CreateWriter%2A> を使用して <xref:System.Xml.XmlWriter> を作成し、この <xref:System.Xml.XmlWriter> に書き込みを行うことです。</span><span class="sxs-lookup"><span data-stu-id="67914-103">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="67914-104">XML ツリーには、<xref:System.Xml.XmlWriter> に書き込まれたすべてのノードが挿入されます。</span><span class="sxs-lookup"><span data-stu-id="67914-104">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="67914-105">通常この方法は、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] と、<xref:System.Xml.XmlWriter> への書き込みを必要とする別のクラス (<xref:System.Xml.Xsl.XslCompiledTransform> など) を併用する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="67914-105">You would typically use this method when you use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67914-106">例</span><span class="sxs-lookup"><span data-stu-id="67914-106">Example</span></span>  
 <span data-ttu-id="67914-107"><xref:System.Xml.Linq.XContainer.CreateWriter%2A> は、XSLT 変換を呼び出すときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="67914-107">One possible use for <xref:System.Xml.Linq.XContainer.CreateWriter%2A> is when invoking an XSLT transformation.</span></span> <span data-ttu-id="67914-108">この例では、XML ツリーを作成し、この XML ツリーから <xref:System.Xml.XmlReader> を作成して、新しいドキュメントを作成します。次に、この新しいドキュメントに書き込むために <xref:System.Xml.XmlWriter> を作成します。</span><span class="sxs-lookup"><span data-stu-id="67914-108">This example creates an XML tree, creates an <xref:System.Xml.XmlReader> from the XML tree, creates a new document, and then creates an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="67914-109">次に、XSLT 変換を呼び出して、<xref:System.Xml.XmlReader> と <xref:System.Xml.XmlWriter> を渡します。</span><span class="sxs-lookup"><span data-stu-id="67914-109">It then invokes the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="67914-110">変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="67914-110">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="67914-111">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="67914-111">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="67914-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="67914-112">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>  
 <xref:System.Xml.XmlWriter>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 [<span data-ttu-id="67914-113">XML ツリー (Visual Basic) を作成します。</span><span class="sxs-lookup"><span data-stu-id="67914-113">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
