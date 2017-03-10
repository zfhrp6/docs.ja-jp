---
title: "How to: Transform XML by Using LINQ (Visual Basic) | Microsoft Docs"
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
  - "XML [Visual Basic], transforming"
  - "LINQ to XML [Visual Basic], transforming XML"
ms.assetid: 815687f4-0bc2-4c0b-adc6-d78744aa356f
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Transform XML by Using LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)を使用すると、ソースからの XML の読み込みと新しい XML 形式への変換を容易に実行できます。  LINQ クエリを利用して変換の内容を取得したり、既存のドキュメントの内容を新しい XML 形式に変換したりできます。  
  
 このトピックの例では、XML ソース ドキュメントの内容を、ブラウザーに表示される HTML に変換します。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### XML ドキュメントを変換するには  
  
1.  Visual Studio で、新しい Visual Basic プロジェクトを **\[コンソール アプリケーション\]** プロジェクト テンプレートで作成します。  
  
2.  Visual Basic コードを変更するために、プロジェクト内に作成された Module1.vb ファイルをダブルクリックします。  `Module1` モジュールの `Sub Main` に次のコードを追加します。  このコードは、ソース XML ドキュメントを <xref:System.Xml.Linq.XDocument> オブジェクトとして作成します。  
  
    ```vb#  
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
  
     [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).  
  
3.  ソース XML ドキュメントを作成するコードの後ろに、オブジェクトからすべての \<Book\> 要素を取得して HTML ドキュメントに変換する次のコードを追加します。  変換後の HTML を含む <xref:System.Xml.Linq.XElement> オブジェクトのコレクションを返す LINQ クエリを使用して、\<Book\> 要素の一覧を作成します。  埋め込み式を使用して、ソース ドキュメントの値を新しい XML 形式にできます。  
  
     <xref:System.Xml.Linq.XElement.Save%2A> メソッドを使用して、結果の HTML ドキュメントをファイルに書き込みます。  
  
    ```vb#  
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
  
4.  `Module1` の `Sub Main` の後ろに、\<Description\> ノードを指定の HTML 形式に変換する新しいメソッド \(`Sub`\) を追加します。  このメソッドは、前の手順のコードによって呼び出され、\<Description\> 要素の書式を保持するために使用されます。  
  
     このメソッドは、\<Description\> 要素のサブ要素を HTML に置き換えます。  `ReplaceWith` メソッドは、サブ要素の位置を保持するために使用されます。  \<Description\> 要素の変換後の内容は、HTML 段落 \(\<p\>\) 要素に含まれます。  <xref:System.Xml.Linq.XContainer.Nodes%2A> プロパティを使用して、\<Description\> 要素の変換後の内容が取得されます。  これにより、変換後の内容にサブ要素が含まれることが保証されます。  
  
     `Module1` の `Sub Main` の後ろに、次のコードを追加します。  
  
    ```vb#  
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
  
6.  F5 キーを押してコードを実行します。  保存されたドキュメントは、次のようになります。  
  
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
  
## 参照  
 [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md)   
 [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)   
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)   
 [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)