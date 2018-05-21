---
title: XmlReader へのシリアル化 (XSLT の呼び出し) (C#)
ms.date: 07/20/2015
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
ms.openlocfilehash: 0663bf2e2c83524e94c91f436ca0146f2dcd68ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="8085c-102">XmlReader へのシリアル化 (XSLT の呼び出し) (C#)</span><span class="sxs-lookup"><span data-stu-id="8085c-102">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="8085c-103">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の <xref:System.Xml?displayProperty=nameWithType> 相互運用機能を使用する場合、<xref:System.Xml.Linq.XNode.CreateReader%2A> を使用して <xref:System.Xml.XmlReader> を作成できます。</span><span class="sxs-lookup"><span data-stu-id="8085c-103">When you use the <xref:System.Xml?displayProperty=nameWithType> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="8085c-104">この <xref:System.Xml.XmlReader> から読み取りを行うモジュールは、XML ツリーからノードを読み取って適宜処理します。</span><span class="sxs-lookup"><span data-stu-id="8085c-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="8085c-105">XSLT 変換の呼び出し</span><span class="sxs-lookup"><span data-stu-id="8085c-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="8085c-106">このメソッドは、XSLT 変換を呼び出すときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="8085c-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="8085c-107">この例では、XML ツリーを作成し、この XML ツリーから <xref:System.Xml.XmlReader> を作成して、新しいドキュメントを作成します。次に、この新しいドキュメントに書き込むために <xref:System.Xml.XmlWriter> を作成します。</span><span class="sxs-lookup"><span data-stu-id="8085c-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="8085c-108">次に、XSLT 変換を呼び出して、<xref:System.Xml.XmlReader> と <xref:System.Xml.XmlWriter> を渡します。</span><span class="sxs-lookup"><span data-stu-id="8085c-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="8085c-109">変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="8085c-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="8085c-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8085c-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8085c-111">参照</span><span class="sxs-lookup"><span data-stu-id="8085c-111">See Also</span></span>  
 [<span data-ttu-id="8085c-112">XML ツリーのシリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="8085c-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
