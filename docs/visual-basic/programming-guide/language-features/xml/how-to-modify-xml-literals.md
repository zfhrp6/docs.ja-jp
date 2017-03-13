---
title: "How to: Modify XML Literals (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "XML axis [Visual Basic], Value"
  - "XML literals [Visual Basic]"
  - "XML literals [Visual Basic], modifying"
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Modify XML Literals (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、XML リテラルを変更するための便利な方法が用意されています。  要素と属性を追加または削除したり、既存の要素を新しい XML 要素に置き換えたりできます。  このトピックでは、既存の XML リテラルを変更する方法の例を示して説明します。  
  
### XML リテラルの値を変更するには  
  
1.  XML リテラルの値を変更するには、XML リテラルへの参照を取得し、`Value` プロパティに目的の値を設定します。  
  
     次のコード例では、XML ドキュメント内のすべての \<Price\> 要素の値を更新します。  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     上のコード例を使用する前の元の XML と変更後の XML を次に示します。  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>47.20</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>48.25</Price>  
      </Book>  
    </Catalog>  
    ```  
  
    > [!NOTE]
    >  `Value` プロパティは、コレクション内の最初の XML 要素を参照します。  コレクション内に同名の要素が複数ある場合、`Value` プロパティの設定は、コレクションの最初の要素だけに作用します。  
  
### XML リテラルに属性を追加するには  
  
1.  XML リテラルに属性を追加するには、先に XML リテラルへの参照を取得します。  次に、新しい XML 属性軸プロパティを追加することで、属性を追加できます。  XML リテラルへの新しい <xref:System.Xml.Linq.XAttribute> オブジェクトの追加は、<xref:System.Xml.Linq.XContainer.Add%2A> メソッドを使用することでも実行できます。  この 2 つの方法の使用例を次に示します。  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     上のコード例を使用する前の元の XML と変更後の XML を次に示します。  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
    ```  
  
     XML 属性軸プロパティの詳細については、「[XML Attribute Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)」を参照してください。  
  
### XML リテラルに要素を追加するには  
  
1.  XML リテラルに要素を追加するには、先に XML リテラルへの参照を取得します。  次に、<xref:System.Xml.Linq.XContainer.Add%2A> メソッドを使用して、新しい <xref:System.Xml.Linq.XElement> オブジェクトを要素のサブ要素として追加できます。  新しい <xref:System.Xml.Linq.XElement> オブジェクトは、<xref:System.Xml.Linq.XContainer.AddFirst%2A> メソッドを使用すると、最初のサブ要素として追加できます。  
  
     新しい要素を、他のサブ要素を基準とする特定の位置に追加するには、隣接するサブ要素への参照を先に取得します。  次に、<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A> メソッドを使用して、隣接するサブ要素の前に新しい <xref:System.Xml.Linq.XElement> オブジェクトを追加できます。  新しい <xref:System.Xml.Linq.XElement> オブジェクトは、<xref:System.Xml.Linq.XNode.AddAfterSelf%2A> メソッドを使用して、隣接するサブ要素の後ろに追加することもできます。  
  
     これらの方法の使用例を次に示します。  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     上のコード例を使用する前の元の XML と変更後の XML を次に示します。  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" >  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331">  
        <Publisher>Microsoft Press</Publisher>  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <PublishDate>2005-2-14</PublishDate>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
    ```  
  
### XML リテラルから要素または属性を削除するには  
  
1.  XML リテラルから要素または属性を削除するには、要素または属性への参照を取得し、`Remove` メソッドを呼び出します。次に例を示します。  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     上のコード例を使用する前の元の XML と変更後の XML を次に示します。  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" genre="Computer" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" genre="Computer" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book>  
      <Book id="bk999"></Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101" editorEmail="someone@example.com">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
      </Book>  
      <Book id="bk000"></Book>  
      <Book id="bk331" editorEmail="someone@example.com">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
      </Book> </Catalog>  
    ```  
  
     XML リテラルからすべての要素または属性を削除するには、XML リテラルへの参照を取得し、<xref:System.Xml.Linq.XElement.RemoveAll%2A> メソッドを呼び出します。  
  
### XML リテラルを変更するには  
  
1.  XML 要素の名前を変更するには、先に要素への参照を取得します。  次に、新しい名前の <xref:System.Xml.Linq.XElement> オブジェクトを作成し、その新しい <xref:System.Xml.Linq.XElement> オブジェクトを、既存の <xref:System.Xml.Linq.XElement> オブジェクトの <xref:System.Xml.Linq.XNode.ReplaceWith%2A> メソッドに渡します。  
  
     置換する要素に、保持する必要があるサブ要素がある場合は、新しい <xref:System.Xml.Linq.XElement> オブジェクトの値に、既存の要素の <xref:System.Xml.Linq.XContainer.Nodes%2A> プロパティを設定します。  これにより、新しい要素の値に、既存の要素の内部 XML が設定されます。  または、新しい要素の値に、既存の要素の `Value` プロパティを設定できます。  
  
     次のコード例では、すべての \<Description\> 要素を \<Abstract\> 要素に置換します。  \<Description\> 要素の内容は、\<Description\> <xref:System.Xml.Linq.XElement> オブジェクトの <xref:System.Xml.Linq.XContainer.Nodes%2A> プロパティによって、新しい \<Abstract\> 要素の中に保持されます。  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     上のコード例を使用する前の元の XML と変更後の XML を次に示します。  
  
    ```  
    Source XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <Price>44.95</Price>  
        <Description>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Description>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <Price>45.95</Price>  
        <Description>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Description>  
      </Book>  
    </Catalog>  
  
    Modified XML:  
    <?xml version="1.0"?>  
    <Catalog>  
      <Book id="bk101">  
        <Author>Garghentini, Davide</Author>  
        <Title>XML Developer's Guide</Title>  
        <MSRP>44.95</MSRP>     <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>     <Abstract>  
          Get the expert insights, practical code samples, and best  
          practices you need to advance your expertise with   
          <technology>Visual Basic .NET</technology>.   
          Learn how to create faster, more reliable applications  
          based on professional, pragmatic guidance by today's top  
          <audience>developers</audience>.  
        </Abstract>  
      </Book>  
    </Catalog>  
    ```  
  
## 参照  
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)