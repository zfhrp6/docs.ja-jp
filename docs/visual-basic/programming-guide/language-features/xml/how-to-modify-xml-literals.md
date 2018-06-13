---
title: '方法 : XML リテラルを変更する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], Value
- XML literals [Visual Basic]
- XML literals [Visual Basic], modifying
ms.assetid: 4e864522-a37a-43a2-8236-af80277c5482
ms.openlocfilehash: 17da86d6d10fb1602c16fc2a8c4d6f9f8acf8ff7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656046"
---
# <a name="how-to-modify-xml-literals-visual-basic"></a>方法 : XML リテラルを変更する (Visual Basic)
Visual Basic では、XML リテラルを変更する便利な手段を提供します。 追加したり、要素と属性を削除し、新しい XML 要素を持つ既存の要素を置換することもできます。 このトピックでは、既存の XML リテラルを変更する方法の例をいくつかを示します。  
  
### <a name="to-modify-the-value-of-an-xml-literal"></a>XML リテラルの値を変更するには  
  
1.  XML リテラルの値を変更するには、XML リテラルおよび設定への参照を取得、`Value`プロパティを目的の値にします。  
  
     次のコード例は、すべての値を更新、\<価格 > XML ドキュメント内の要素。  
  
     [!code-vb[VbXmlSamples2#4](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_1.vb)]  
  
     次のサンプルのソース XML に示し、このコード例から XML を変更します。  
  
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
    >  `Value`プロパティは、コレクション内の最初の XML 要素を参照します。 コレクションに同じ名前を持つ 2 つ以上の要素がある場合は、設定、`Value`プロパティは、コレクション内の最初の要素だけに影響します。  
  
### <a name="to-add-an-attribute-to-an-xml-literal"></a>XML リテラルに属性を追加するには  
  
1.  XML リテラルに属性を追加するには、リテラルの XML への参照をまず取得します。 新しい XML 属性軸プロパティを追加することで、属性を追加できます。 追加することも、新しい<xref:System.Xml.Linq.XAttribute>オブジェクトを使用して、リテラルの XML に、<xref:System.Xml.Linq.XContainer.Add%2A>メソッドです。 次の例では、両方のオプションを示します。  
  
     [!code-vb[VbXmlSamples2#5](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_2.vb)]  
  
     次のサンプルのソース XML に示し、このコード例から XML を変更します。  
  
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
  
     XML 属性軸プロパティの詳細については、次を参照してください。 [XML 属性軸プロパティ](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)です。  
  
### <a name="to-add-an-element-to-an-xml-literal"></a>XML リテラルに要素を追加するには  
  
1.  XML リテラルに要素を追加するには、リテラルの XML への参照をまず取得します。 できますし、追加する新しい<xref:System.Xml.Linq.XElement>オブジェクトを使用して要素の最後のサブ要素として、<xref:System.Xml.Linq.XContainer.Add%2A>メソッドです。 新しいを追加することができます<xref:System.Xml.Linq.XElement>オブジェクトを使用して最初のサブ要素として、<xref:System.Xml.Linq.XContainer.AddFirst%2A>メソッドです。  
  
     その他のサブ要素に対して特定の場所に新しい要素を追加するには、隣接するサブ要素への参照をまず取得します。 できますし、追加する新しい<xref:System.Xml.Linq.XElement>オブジェクトを使用して隣接するサブ要素の前に、<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>メソッドです。 追加することも、新しい<xref:System.Xml.Linq.XElement>オブジェクトを使用して隣接するサブ要素の後に、<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>メソッドです。  
  
     次の例では、これらの方法の例を示します。  
  
     [!code-vb[VbXmlSamples2#6](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_3.vb)]  
  
     次のサンプルのソース XML に示し、このコード例から XML を変更します。  
  
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
  
1.  XML リテラルから要素または属性を削除するには、要素または属性および呼び出しへの参照を取得、`Remove`メソッドを次の例で示すようにします。  
  
     [!code-vb[VbXmlSamples2#7](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_4.vb)]  
  
     次のサンプルのソース XML に示し、このコード例から XML を変更します。  
  
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
  
     XML リテラルからすべての要素または属性を削除にリテラルの XML への参照を取得し、<xref:System.Xml.Linq.XElement.RemoveAll%2A>メソッドです。  
  
### <a name="to-modify-an-xml-literal"></a>XML リテラルを変更するには  
  
1.  XML 要素の名前を変更するには、まず要素への参照を取得します。 できますし、新規に作成する<xref:System.Xml.Linq.XElement>を持つ新しい名前を指定し、新しい渡すオブジェクト<xref:System.Xml.Linq.XElement>オブジェクトを<xref:System.Xml.Linq.XNode.ReplaceWith%2A>、既存のメソッド<xref:System.Xml.Linq.XElement>オブジェクト。  
  
     置き換えようとしている要素に保存する必要があるサブ要素がある場合は、新しい値に設定<xref:System.Xml.Linq.XElement>オブジェクトを<xref:System.Xml.Linq.XContainer.Nodes%2A>既存の要素のプロパティです。 これにより、既存の要素の内部 XML を新しい要素の値が設定されます。 それ以外の場合、新しい要素の値を設定することができます、`Value`既存の要素のプロパティです。  
  
     次のコード例では、すべてに置き換わります\<説明 > を持つ要素が\<抽象 > 要素。 内容、\<説明 > 要素が新しい内でも維持される\<抽象 > 要素を使用して、<xref:System.Xml.Linq.XContainer.Nodes%2A>のプロパティ、\<説明 ><xref:System.Xml.Linq.XElement>オブジェクト。  
  
     [!code-vb[VbXmlSamples2#8](../../../../visual-basic/programming-guide/language-features/xml/codesnippet/VisualBasic/how-to-modify-xml-literals_5.vb)]  
  
     次のサンプルのソース XML に示し、このコード例から XML を変更します。  
  
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
 [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [方法 : ファイル、文字列、またはストリームからの XML の読み込み](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
