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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 12b5bfd059d219a5cb0087e763688d01a75b0533
ms.contentlocale: ja-jp
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-transform-xml-by-using-linq-visual-basic"></a><span data-ttu-id="a86b0-102">方法 : LINQ を使用して XML を変換する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a86b0-102">How to: Transform XML by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="a86b0-103">[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md)容易に&1; つのソースから XML を読み取るし、新しい XML 形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="a86b0-103">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) make it easy to read XML from one source and transform it to a new XML format.</span></span> <span data-ttu-id="a86b0-104">変換、コンテンツを取得する LINQ クエリを活用したり、既存のドキュメントの内容を新しい XML 形式に変更できます。</span><span class="sxs-lookup"><span data-stu-id="a86b0-104">You can take advantage of LINQ queries to retrieve the content to transform, or change content in an existing document to a new XML format.</span></span>  
  
 <span data-ttu-id="a86b0-105">このトピックの例では、XML ソース ドキュメントからブラウザーで表示される HTML へのコンテンツを変換します。</span><span class="sxs-lookup"><span data-stu-id="a86b0-105">The example in this topic transforms content from an XML source document to HTML to be viewed in a browser.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-transform-an-xml-document"></a><span data-ttu-id="a86b0-106">XML ドキュメントを変換するには</span><span class="sxs-lookup"><span data-stu-id="a86b0-106">To transform an XML document</span></span>  
  
1.  <span data-ttu-id="a86b0-107">Visual Studio で新しい Visual Basic プロジェクトを作成、**コンソール アプリケーション**プロジェクト テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="a86b0-107">In Visual Studio, create a new Visual Basic project in the **Console Application** project template.</span></span>  
  
2.  <span data-ttu-id="a86b0-108">Visual Basic コードを変更するプロジェクトで作成した Module1.vb ファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="a86b0-108">Double-click the Module1.vb file created in the project to modify the Visual Basic code.</span></span> <span data-ttu-id="a86b0-109">次のコードを追加、`Sub Main`の`Module1`モジュールです。</span><span class="sxs-lookup"><span data-stu-id="a86b0-109">Add the following code to the `Sub Main` of the `Module1` module.</span></span> <span data-ttu-id="a86b0-110">このコードでは、ソース XML ドキュメントとして、<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="a86b0-110">This code creates the source XML document as an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
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
  
     <span data-ttu-id="a86b0-111">[方法: ファイル、文字列またはストリームから XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)です。</span><span class="sxs-lookup"><span data-stu-id="a86b0-111">[How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md).</span></span>  
  
3.  <span data-ttu-id="a86b0-112">ソース XML ドキュメントを作成するコードの後に、すべて取得する次のコードを追加、\<帳 > オブジェクトの要素を HTML ドキュメントに変換するとします。</span><span class="sxs-lookup"><span data-stu-id="a86b0-112">After the code to create the source XML document, add the following code to retrieve all the \<Book> elements from the object and transform them into an HTML document.</span></span> <span data-ttu-id="a86b0-113">一連の\<帳 > のコレクションを返す LINQ クエリを使用して要素を作成<xref:System.Xml.Linq.XElement>変換後の HTML を含むオブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="a86b0-113">The list of \<Book> elements is created by using a LINQ query that returns a collection of <xref:System.Xml.Linq.XElement> objects that contain the transformed HTML.</span></span> <span data-ttu-id="a86b0-114">埋め込み式を使用して、新しい XML 形式で、ソース ドキュメントからの値を挿入することができます。</span><span class="sxs-lookup"><span data-stu-id="a86b0-114">You can use embedded expressions to put the values from the source document in the new XML format.</span></span>  
  
     <span data-ttu-id="a86b0-115">使用して結果の HTML ドキュメントがファイルに書き込まれる、<xref:System.Xml.Linq.XElement.Save%2A>メソッド</xref:System.Xml.Linq.XElement.Save%2A>。</span><span class="sxs-lookup"><span data-stu-id="a86b0-115">The resulting HTML document is written to a file by using the <xref:System.Xml.Linq.XElement.Save%2A> method.</span></span>  
  
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
  
4.  <span data-ttu-id="a86b0-116">後に`Sub Main`の`Module1`、新しいメソッドを追加 (`Sub`) に変換する、\<説明 > ノードを指定した HTML 形式にします。</span><span class="sxs-lookup"><span data-stu-id="a86b0-116">After `Sub Main` of `Module1`, add a new method (`Sub`) to transform a \<Description> node into the specified HTML format.</span></span> <span data-ttu-id="a86b0-117">このメソッドは、前の手順でコードによって呼び出されの形式を保持するために使用される、\<説明 > 要素。</span><span class="sxs-lookup"><span data-stu-id="a86b0-117">This method is called by the code in the previous step and is used to preserve the format of the \<Description> elements.</span></span>  
  
     <span data-ttu-id="a86b0-118">このメソッドは、のサブ要素を置き換えます、\<説明 > HTML を持つ要素。</span><span class="sxs-lookup"><span data-stu-id="a86b0-118">This method replaces sub-elements of the \<Description> element with HTML.</span></span> <span data-ttu-id="a86b0-119">`ReplaceWith`メソッドは、サブ要素の位置を保持するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a86b0-119">The `ReplaceWith` method is used to preserve the location of the sub-elements.</span></span> <span data-ttu-id="a86b0-120">変換済みのコンテンツ、\<説明 > HTML パラグラフで要素が含まれています (\<p >) 要素です。</span><span class="sxs-lookup"><span data-stu-id="a86b0-120">The transformed content of the \<Description> element is included in an HTML paragraph (\<p>) element.</span></span> <span data-ttu-id="a86b0-121"><xref:System.Xml.Linq.XContainer.Nodes%2A>の変換済みのコンテンツを取得するプロパティが使用される、\<説明 > 要素</xref:System.Xml.Linq.XContainer.Nodes%2A>。</span><span class="sxs-lookup"><span data-stu-id="a86b0-121">The <xref:System.Xml.Linq.XContainer.Nodes%2A> property is used to retrieve the transformed content of the \<Description> element.</span></span> <span data-ttu-id="a86b0-122">これにより、変換済みのコンテンツにサブ要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a86b0-122">This ensures that sub-elements are included in the transformed content.</span></span>  
  
     <span data-ttu-id="a86b0-123">後は、次のコードを追加`Sub Main`の`Module1`です。</span><span class="sxs-lookup"><span data-stu-id="a86b0-123">Add the following code after `Sub Main` of `Module1`.</span></span>  
  
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
  
5.  <span data-ttu-id="a86b0-124">変更内容を保存します。</span><span class="sxs-lookup"><span data-stu-id="a86b0-124">Save your changes.</span></span>  
  
6.  <span data-ttu-id="a86b0-125">F5 キーを押して、コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="a86b0-125">Press F5 to run the code.</span></span> <span data-ttu-id="a86b0-126">保存されたドキュメントは以下のようにします。</span><span class="sxs-lookup"><span data-stu-id="a86b0-126">The resulting saved document will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a86b0-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="a86b0-127">See Also</span></span>  
 <span data-ttu-id="a86b0-128">[XML リテラル](../../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="a86b0-128">[XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="a86b0-129"> [Visual Basic で XML を操作します。](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a86b0-129"> [Manipulating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md) </span></span>  
<span data-ttu-id="a86b0-130"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="a86b0-130"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="a86b0-131"> [方法: ファイル、文字列またはストリームから XML を読み込む](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span><span class="sxs-lookup"><span data-stu-id="a86b0-131"> [How to: Load XML from a File, String, or Stream](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md) </span></span>  
<span data-ttu-id="a86b0-132"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="a86b0-132"> [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="a86b0-133"> [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="a86b0-133"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>

