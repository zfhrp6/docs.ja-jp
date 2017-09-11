---
title: "XmlReader (XSLT の呼び出し) にシリアル化する (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
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
ms.openlocfilehash: 7e1af87fceb9f3f7eae6af6f917037ba80908827
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a><span data-ttu-id="1abbf-102">XmlReader (XSLT の呼び出し) にシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1abbf-102">Serializing to an XmlReader (Invoking XSLT) (Visual Basic)</span></span>
<span data-ttu-id="1abbf-103">使用すると、<xref:System.Xml?displayProperty=fullName>の相互運用機能[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]、 <xref:System.Xml.Linq.XNode.CreateReader%2A> <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>を作成に</xref:System.Xml.Linq.XNode.CreateReader%2A>使用できる</xref:System.Xml?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1abbf-103">When you use the <xref:System.Xml?displayProperty=fullName> interoperability capabilities of [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="1abbf-104">これから読み取りを行うモジュール<xref:System.Xml.XmlReader>XML ツリーからノードを読み取って適宜処理します</xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="1abbf-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="1abbf-105">XSLT 変換の呼び出し</span><span class="sxs-lookup"><span data-stu-id="1abbf-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="1abbf-106">このメソッドは、XSLT 変換を呼び出すときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="1abbf-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="1abbf-107">XML ツリーを作成したり、作成できます、 <xref:System.Xml.XmlReader>XML ツリーから 新しいドキュメントを作成し、作成、<xref:System.Xml.XmlWriter>に新しいドキュメントに書き込む</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>。</span><span class="sxs-lookup"><span data-stu-id="1abbf-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="1abbf-108">次に、 <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>を渡して、XSLT 変換を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1abbf-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="1abbf-109">変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="1abbf-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
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
  
 <span data-ttu-id="1abbf-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1abbf-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1abbf-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="1abbf-111">See Also</span></span>  
 [<span data-ttu-id="1abbf-112">XML ツリーをシリアル化する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1abbf-112">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
