---
title: "XElement クラスの概要 (Visual Basic) |Microsoft ドキュメント"
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
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
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
ms.openlocfilehash: 4b46f3cb5e0d59105fbc31424a0408c3421d9cac
ms.lasthandoff: 03/13/2017

---
# <a name="xelement-class-overview-visual-basic"></a>XElement クラスの概要 (Visual Basic)
<xref:System.Xml.Linq.XElement>クラスは、基礎クラスのいずれかの[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]</xref:System.Xml.Linq.XElement>。 これは XML 要素を表します。 このクラスを使用すると、要素の作成、要素のコンテンツの変更、子要素の追加、変更、削除、要素への属性の追加、および要素のコンテンツのテキスト形式へのシリアル化を行うことができます。 他のクラスと相互運用することも<xref:System.Xml?displayProperty=fullName>など<xref:System.Xml.XmlReader>、 <xref:System.Xml.XmlWriter>、 <xref:System.Xml.Xsl.XslCompiledTransform>.</xref:System.Xml.Xsl.XslCompiledTransform> </xref:System.Xml.XmlWriter> </xref:System.Xml.XmlReader> </xref:System.Xml?displayProperty=fullName>  
  
## <a name="xelement-functionality"></a>XElement の機能  
 このトピックの<xref:System.Xml.Linq.XElement>クラス</xref:System.Xml.Linq.XElement>によって提供される機能について説明します。  
  
### <a name="constructing-xml-trees"></a>XML ツリーの構築  
 次のようなさまざまな方法で XML ツリーを構築できます。  
  
-   コードで XML ツリーを構築できます。 詳細については、次を参照してください。 [XML ツリーを作成する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)します。  
  
-   などのさまざまなソースから XML を解析して、 <xref:System.IO.TextReader>、テキスト ファイル、または Web アドレス (URL).</xref:System.IO.TextReader> 詳細については、次を参照してください。 [XML の解析 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)します。  
  
-   使用することができます、<xref:System.Xml.XmlReader>ツリーを設定します</xref:System.Xml.XmlReader>。 詳細については、 <xref:System.Xml.Linq.XNode.ReadFrom%2A>。</xref:System.Xml.Linq.XNode.ReadFrom%2A>を参照してください。  
  
-   コンテンツを書き込むことができるモジュールがあるかどうか、 <xref:System.Xml.XmlWriter>、使用することができます、<xref:System.Xml.Linq.XContainer.CreateWriter%2A>ライターを作成され、このライターをモジュールに渡しに書き込まれたコンテンツが使用するメソッド、 <xref:System.Xml.XmlWriter>XML ツリーを作成する</xref:System.Xml.XmlWriter></xref:System.Xml.Linq.XContainer.CreateWriter%2A></xref:System.Xml.XmlWriter>。  
  
 しかし、XML ツリーを作成する最も一般的な方法は次のとおりです。  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 結果を使用して XML ツリーを作成するもう&1; つの一般的な方法では、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]の次の例に示すように、XML ツリーを設定するクエリ。  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>XML ツリーのシリアル化  
 XML ツリーをシリアル化することができます、 <xref:System.IO.File>、 <xref:System.IO.TextWriter>、または<xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File>  
  
 詳細については、次を参照してください。 [XML ツリーをシリアル化する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)します。  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>軸メソッドによる XML データの取得  
 軸メソッドを使用すると、属性、子要素、子孫要素、および祖先要素を取得できます。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] クエリは、軸メソッドに対して機能し、XML ツリーを操作して処理するための、柔軟で強力な複数の機能を備えています。  
  
 詳細については、次を参照してください。 [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)します。  
  
### <a name="querying-xml-trees"></a>XML ツリーのクエリ  
 記述する[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]XML ツリーからデータを抽出するクエリ。  
  
 詳細については、次を参照してください。 [(Visual Basic) の XML ツリーのクエリを実行する](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)です。  
  
### <a name="modifying-xml-trees"></a>XML ツリーの変更  
 要素を変更するには、そのコンテンツや属性を変更するなど、さまざまな方法があります。 要素を親から削除することもできます。  
  
 詳細については、次を参照してください。 [XML ツリーの変更 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)します。  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML プログラミングの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
