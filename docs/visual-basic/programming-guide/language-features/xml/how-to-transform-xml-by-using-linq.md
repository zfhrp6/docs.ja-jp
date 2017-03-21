---
title: "方法: LINQ (Visual Basic) を使用して XML を変換 |Microsoft ドキュメント"
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
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: 14
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 9f97466727064ea275c051b5916b0fb297e9e23a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>方法 : LINQ を使用して XML を変換する (Visual Basic)
[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)容易に&1; つのソースから XML を読み取るし、新しい XML 形式に変換します。 変換、コンテンツを取得する LINQ クエリを活用したり、既存のドキュメントの内容を新しい XML 形式に変更できます。  
  
 このトピックの例では、XML ソース ドキュメントからブラウザーで表示される HTML へのコンテンツを変換します。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-transform-an-xml-document"></a>XML ドキュメントを変換するには  
  
1.  Visual Studio で新しい Visual Basic プロジェクトを作成、**コンソール アプリケーション**プロジェクト テンプレートです。  
  
2.  Visual Basic コードを変更するプロジェクトで作成した Module1.vb ファイルをダブルクリックします。 次のコードを追加、`Sub Main`の`Module1`モジュールです。 このコードでは、ソース XML ドキュメントとして、<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument>。  
  
    ```vb  
    Dim catalog =   
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
              Get the expert insights, practical code samples,   
              and best practices you need   
              to advance your expertise with <technology>Visual   
              Basic .NET</technology>.   
              Learn how to create faster, more reliable applications  
              based on professional,   
              pragmatic guidance by today's top <audience>developers</audience>.  
            </Description>  
          </Book>  
        </Catalog>  
    ```  
  
     [方法: ファイル、文字列またはストリームから XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)です。  
  
3.  ソース XML ドキュメントを作成するコードの後に、すべて取得する次のコードを追加、\<帳 > オブジェクトの要素を HTML ドキュメントに変換するとします。 一連の\<帳 > のコレクションを返す LINQ クエリを使用して要素を作成<xref:System.Xml.Linq.XElement>変換後の HTML を含むオブジェクト</xref:System.Xml.Linq.XElement>。 埋め込み式を使用して、新しい XML 形式で、ソース ドキュメントからの値を挿入することができます。  
  
     使用して結果の HTML ドキュメントがファイルに書き込まれる、<xref:System.Xml.Linq.XElement.Save%2A>メソッド</xref:System.Xml.Linq.XElement.Save%2A>。  
  
    ```vb  
    Dim htmlOutput =   
      <html>  
        <body>  
          <%= From book In catalog.<Catalog>.<Book>   
              Select <div>  
                       <h1><%= book.<Title>.Value %></h1>  
                       <h3><%= "By " & book.<Author>.Value %></h3>  
                        <h3><%= "Price = " & book.<Price>.Value %></h3>  
                        <h2>Description</h2>  
                        <%= TransformDescription(book.<Description>(0)) %>  
                        <hr/>  
                      </div> %>  
        </body>  
      </html>  
  
    htmlOutput.Save("BookDescription.html")  
    ```  
  
4.  後に`Sub Main`の`Module1`、新しいメソッドを追加 (`Sub`) に変換する、\<説明 > ノードを指定した HTML 形式にします。 このメソッドは、前の手順でコードによって呼び出されの形式を保持するために使用される、\<説明 > 要素。  
  
     このメソッドは、のサブ要素を置き換えます、\<説明 > HTML を持つ要素。 `ReplaceWith`メソッドは、サブ要素の位置を保持するために使用します。 変換済みのコンテンツ、\<説明 > HTML パラグラフで要素が含まれています (\<p >) 要素です。 <xref:System.Xml.Linq.XContainer.Nodes%2A>の変換済みのコンテンツを取得するプロパティが使用される、\<説明 > 要素</xref:System.Xml.Linq.XContainer.Nodes%2A>。 これにより、変換済みのコンテンツにサブ要素が含まれています。  
  
     後は、次のコードを追加`Sub Main`の`Module1`です。  
  
    ```vb  
    Public Function TransformDescription(ByVal desc As XElement) As XElement  
  
      ' Replace <technology> elements with <b>.  
      Dim content = (From element In desc...<technology>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<b><%= content(i).Value %></b>)  
        Next  
      End If  
  
      ' Replace <audience> elements with <i>.  
      content = (From element In desc...<audience>).ToList()  
  
      If content.Count > 0 Then  
        For i = 0 To content.Count - 1  
          content(i).ReplaceWith(<i><%= content(i).Value %></i>)  
        Next  
      End If  
  
      ' Return the updated contents of the <Description> element.  
      Return <p><%= desc.Nodes %></p>  
    End Function  
    ```  
  
5.  変更内容を保存します。  
  
6.  F5 キーを押して、コードを実行します。 保存されたドキュメントは以下のようにします。  
  
    ```  
    <?xml version="1.0"?>  
    <html>  
      <body>  
        <div>  
          <h1>XML Developer's Guide</h1>  
          <h3>By Garghentini, Davide</h3>  
          <h3>Price = 44.95</h3>  
          <h2>Description</h2>  
          <p>  
            An in-depth look at creating applications  
            with <b>XML</b>. For   
            <i>beginners</i> or   
            <i>advanced</i> developers.  
          </p>  
          <hr />  
        </div>  
        <div>  
          <h1>Developing Applications with Visual Basic .NET</h1>  
          <h3>By Spencer, Phil</h3>  
          <h3>Price = 45.95</h3>  
          <h2>Description</h2>  
          <p>  
            Get the expert insights, practical code   
            samples, and best practices you need   
            to advance your expertise with <b>Visual   
            Basic .NET</b>. Learn how to create faster,  
            more reliable applications based on  
            professional, pragmatic guidance by today's   
            top <i>developers</i>.  
          </p>  
          <hr />  
        </div>  
      </body>  
    </html>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [方法: ファイル、文字列またはストリームから XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)

