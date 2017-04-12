---
title: "方法: XML リテラル (Visual Basic) の変更 |Microsoft ドキュメント"
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
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0ff2eba693862154d9c402748fb6797d10c4a1f8
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-modify-xml-literals-visual-basic"></a>方法 : XML リテラルを変更する (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルを変更する便利な手段を提供します。 リストにログインを追加したり、要素や属性を削除し、新しい XML 要素を持つ既存の要素を置換することもできます。 このトピックでは、既存の XML リテラルを変更する方法の例をいくつかを示します。  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a>XML リテラルの値を変更するには  
  
1.  XML リテラルの値を変更するには、XML リテラルと設定への参照を取得、`Value`プロパティを目的の値にします。  
  
     次のコード例は、すべての値を更新、\<価格 > XML ドキュメント内の要素。  
  
     [!code-vb[VbXmlSamples2&4;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     次の XML のサンプルのソースを示していて、このコード例から XML を変更します。  
  
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
    >  `Value`プロパティは、コレクション内の最初の XML 要素を参照します。 複数のコレクションで同じ名前を持つ要素がある場合は、設定、`Value`プロパティは、コレクション内の最初の要素だけに影響します。  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a>XML リテラルに属性を追加するには  
  
1.  XML リテラルに属性を追加するには、XML リテラルへの参照を最初に取得します。 新しい XML 属性軸プロパティを追加することで、属性を追加できます。 追加することも、新しい<xref:System.Xml.Linq.XAttribute>オブジェクトを XML リテラルを使用して、<xref:System.Xml.Linq.XContainer.Add%2A>メソッド</xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XAttribute>。 次の例では、両方のオプションを示します。  
  
     [!code-vb[VbXmlSamples&#2;5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     次の XML のサンプルのソースを示していて、このコード例から XML を変更します。  
  
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
  
     XML 属性軸プロパティの詳細については、次を参照してください。 [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)します。  
  
### <a name="to-add-an-element-to-an-xml-literal"></a>XML リテラルに要素を追加するには  
  
1.  XML リテラルに要素を追加するには、XML リテラルへの参照を最初に取得します。 新しく追加できます<xref:System.Xml.Linq.XElement>オブジェクトを使用して要素の最後のサブ要素として、<xref:System.Xml.Linq.XContainer.Add%2A>メソッド</xref:System.Xml.Linq.XContainer.Add%2A></xref:System.Xml.Linq.XElement>。 新しいを追加する<xref:System.Xml.Linq.XElement>オブジェクトを使用して最初のサブ要素として、<xref:System.Xml.Linq.XContainer.AddFirst%2A>メソッド</xref:System.Xml.Linq.XContainer.AddFirst%2A></xref:System.Xml.Linq.XElement>。  
  
     その他のサブ要素を基準とした特定の場所に新しい要素を追加するには、隣接するサブ要素への参照を最初に取得します。 新しいできますし、追加<xref:System.Xml.Linq.XElement>オブジェクトを使用して、隣接するサブ要素の前に、<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>メソッド</xref:System.Xml.Linq.XNode.AddBeforeSelf%2A></xref:System.Xml.Linq.XElement>。 追加することも、新しい<xref:System.Xml.Linq.XElement>オブジェクトを使用して、隣接するサブ要素の後に、<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>メソッド</xref:System.Xml.Linq.XNode.AddAfterSelf%2A></xref:System.Xml.Linq.XElement>。  
  
     次の例では、これらの各手法の例を示します。  
  
     [!code-vb[VbXmlSamples2&6;](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     次の XML のサンプルのソースを示していて、このコード例から XML を変更します。  
  
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
  
### <a name="to-remove-an-element-or-attribute-from-an-xml-literal"></a>XML リテラルから要素または属性を削除するには  
  
1.  XML リテラルから要素または属性を削除するには、要素または属性および呼び出しへの参照を取得、`Remove`メソッドを次の例に示すようにします。  
  
     [!code-vb[VbXmlSamples&#2;7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     次の XML のサンプルのソースを示していて、このコード例から XML を変更します。  
  
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
      </Book></Catalog>  
    ```  
  
     XML リテラルからすべての要素または属性を削除するには、XML リテラルへの参照を取得およびを呼び出す、<xref:System.Xml.Linq.XElement.RemoveAll%2A>メソッド</xref:System.Xml.Linq.XElement.RemoveAll%2A>。  
  
### <a name="to-modify-an-xml-literal"></a>XML リテラルを変更するには  
  
1.  XML 要素の名前を変更するには、まず要素への参照を取得します。 できますし、新規に作成する<xref:System.Xml.Linq.XElement>オブジェクトを持つ新しい名前を指定し、新しい渡す<xref:System.Xml.Linq.XElement>オブジェクトを<xref:System.Xml.Linq.XNode.ReplaceWith%2A>、既存のメソッド<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XNode.ReplaceWith%2A></xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XElement>。  
  
     ものに交換する要素に保存する必要があるサブ要素がある場合は、新しい値を設定<xref:System.Xml.Linq.XElement>オブジェクトを<xref:System.Xml.Linq.XContainer.Nodes%2A>は既存の要素のプロパティ</xref:System.Xml.Linq.XContainer.Nodes%2A></xref:System.Xml.Linq.XElement>。 これにより、既存の要素の内部 XML を新しい要素の値が設定されます。 それ以外の場合に新しい要素の値を設定することができます、`Value`は既存の要素のプロパティです。  
  
     次のコード例では、すべて置き換えられます\<説明 > を持つ要素が\<抽象 > 要素。 内容、\<説明 > 要素は、新しい保持\<抽象 > 要素を使用して、<xref:System.Xml.Linq.XContainer.Nodes%2A>のプロパティ、\<説明 ><xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XContainer.Nodes%2A>。  
  
     [!code-vb[VbXmlSamples&#2;8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     次の XML のサンプルのソースを示していて、このコード例から XML を変更します。  
  
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
        <MSRP>44.95</MSRP>    <Abstract>  
          An in-depth look at creating applications  
          with <technology>XML</technology>. For   
          <audience>beginners</audience> or   
          <audience>advanced</audience> developers.  
        </Abstract>  
      </Book>  
      <Book id="bk331">  
        <Author>Spencer, Phil</Author>  
        <Title>Developing Applications with Visual Basic .NET</Title>  
        <MSRP>45.95</MSRP>    <Abstract>  
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
  
## <a name="see-also"></a>関連項目  
 [Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [方法: ファイル、文字列またはストリームから XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
