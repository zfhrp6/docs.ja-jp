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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bca1e63bbe5b3ccd13f183c3cc6081917624ad94
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>XmlReader (XSLT の呼び出し) にシリアル化する (Visual Basic)
使用すると、<xref:System.Xml?displayProperty=fullName>の相互運用機能[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]、 <xref:System.Xml.Linq.XNode.CreateReader%2A> <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader>を作成に</xref:System.Xml.Linq.XNode.CreateReader%2A>使用できる</xref:System.Xml?displayProperty=fullName> これから読み取りを行うモジュール<xref:System.Xml.XmlReader>XML ツリーからノードを読み取って適宜処理します</xref:System.Xml.XmlReader>。  
  
## <a name="invoking-an-xslt-transformation"></a>XSLT 変換の呼び出し  
 このメソッドは、XSLT 変換を呼び出すときに使用できます。 XML ツリーを作成したり、作成できます、 <xref:System.Xml.XmlReader>XML ツリーから 新しいドキュメントを作成し、作成、<xref:System.Xml.XmlWriter>に新しいドキュメントに書き込む</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>。 次に、 <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter></xref:System.Xml.XmlReader>を渡して、XSLT 変換を呼び出すことができます。 変換が正常に完了すると、新しい XML ツリーに変換結果が挿入されます。  
  
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
 [XML ツリーをシリアル化する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
