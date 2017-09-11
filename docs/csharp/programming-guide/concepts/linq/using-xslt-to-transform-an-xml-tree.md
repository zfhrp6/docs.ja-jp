---
title: "XSLT を使用した XML ツリーの変換 (C#)"
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
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b6ec4a04bebd39ecb6a90dfc48729fa8696a2ab5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="21c05-102">XSLT を使用した XML ツリーの変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="21c05-102">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="21c05-103">この例では、XML ツリーを作成し、この XML ツリーから <xref:System.Xml.XmlReader> を作成して、新しいドキュメントを作成します。次に、この新しいドキュメントに書き込むために <xref:System.Xml.XmlWriter> を作成します。</span><span class="sxs-lookup"><span data-stu-id="21c05-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="21c05-104">次に、XSLT 変換を呼び出し、変換処理に <xref:System.Xml.XmlReader> および <xref:System.Xml.XmlWriter> を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="21c05-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="21c05-105">変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="21c05-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21c05-106">例</span><span class="sxs-lookup"><span data-stu-id="21c05-106">Example</span></span>  
  
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
  
    // Execute the transform and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="21c05-107">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="21c05-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="21c05-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="21c05-108">See Also</span></span>  
 <span data-ttu-id="21c05-109"><xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="21c05-109"><xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="21c05-110"><xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="21c05-110"><xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=fullName></span></span>   
 [<span data-ttu-id="21c05-111">高度な LINQ to XML プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="21c05-111">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)

