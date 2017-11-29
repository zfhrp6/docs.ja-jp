---
title: "方法 : LINQ を使用して XML を変換する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], transforming
- LINQ to XML [Visual Basic], transforming XML
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf7c44598558b2c631ff3ef4c2ae0986a49ca2bd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a>方法 : LINQ を使用して XML を変換する (Visual Basic)
[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)簡単に 1 つのソースから XML を読み取るし、新しい XML 形式に変換します。 変換するには、コンテンツを取得する LINQ クエリを利用したり、既存のドキュメントにコンテンツを新しい XML 形式に変更することができます。  
  
 このトピックの例では、XML ソース ドキュメントからブラウザーで表示される HTML へのコンテンツを変換します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a>XML ドキュメントを変換するには  
  
1.  Visual Studio で、新しい Visual Basic プロジェクトを作成、**コンソール アプリケーション**プロジェクト テンプレート。  
  
2.  Visual Basic コードを変更するプロジェクトで作成した Module1.vb ファイルをダブルクリックします。 次のコードを追加、`Sub Main`の`Module1`モジュール。 このコードでは、ソース XML ドキュメントとして、<xref:System.Xml.Linq.XDocument>オブジェクト。  
  
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
  
     [方法: ファイル、文字列、またはストリームから XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)します。  
  
3.  XML ソース ドキュメントを作成するコードを後にすべてを取得する次のコードを追加、 \<Book > オブジェクトの要素を HTML ドキュメントに変換するとします。 一覧\<Book > 要素のコレクションを返す LINQ クエリを使用して作成<xref:System.Xml.Linq.XElement>変換後の HTML を格納するオブジェクト。 埋め込み式を使用すると、新しい XML 形式でソース ドキュメントからの値を入力します。  
  
     使用して、結果の HTML ドキュメントがファイルに書き込まれます、<xref:System.Xml.Linq.XElement.Save%2A>メソッドです。  
  
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
  
4.  後に`Sub Main`の`Module1`、新しいメソッドを追加 (`Sub`) に変換する、\<説明 > ノードを指定した HTML 形式にします。 このメソッドは、前の手順のコードによって呼び出されますの形式を保持するために使用される、\<説明 > 要素。  
  
     このメソッドは、のサブ要素を置き換えます、\<説明 > を HTML 要素です。 `ReplaceWith`サブ要素の位置を保持するためにメソッドを使用します。 変換後の内容、\<説明 > HTML 段落で要素が含まれています (\<p >) 要素です。 <xref:System.Xml.Linq.XContainer.Nodes%2A>の変換後の内容を取得するプロパティが使用される、\<説明 > 要素。 これにより、変換済みのコンテンツにサブ要素が含まれています。  
  
     次のコードの後に追加`Sub Main`の`Module1`します。  
  
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
  
6.  F5 キーを押してコードを実行します。 保存されたドキュメントは次のようにします。  
  
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
 [Visual Basic での XML の操作](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [方法 : ファイル、文字列、またはストリームからの XML の読み込み](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
