---
title: "段落とそのスタイル (Visual Basic) を取得します。"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9ed2238-d38e-4ad4-b88b-db7859df9bde
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95c85b4731a9ada0a6af1a9d825bef9b873e89ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="retrieving-the-paragraphs-and-their-styles-visual-basic"></a><span data-ttu-id="51da2-102">段落とそのスタイル (Visual Basic) を取得します。</span><span class="sxs-lookup"><span data-stu-id="51da2-102">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>
<span data-ttu-id="51da2-103">この例では、WordprocessingML ドキュメントから段落ノードを取得するクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="51da2-103">In this example, we write a query that retrieves the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="51da2-104">それぞれの段落のスタイルも特定します。</span><span class="sxs-lookup"><span data-stu-id="51da2-104">It also identifies the style of each paragraph.</span></span>  
  
 <span data-ttu-id="51da2-105">このクエリは前の例では、クエリに基づいて[既定の段落スタイル (Visual Basic) を検索する](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)スタイルの一覧から既定のスタイルを取得します。</span><span class="sxs-lookup"><span data-stu-id="51da2-105">This query builds on the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md), which retrieves the default style from the list of styles.</span></span> <span data-ttu-id="51da2-106">スタイルが明示的に設定されていない段落のスタイルをクエリで特定するには、この情報が必要です。</span><span class="sxs-lookup"><span data-stu-id="51da2-106">This information is required so that the query can identify the style of paragraphs that do not have a style explicitly set.</span></span> <span data-ttu-id="51da2-107">段落のスタイルは、`w:pPr` 要素を通して設定されます。この要素が含まれていない段落は、既定のスタイルを使用して書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="51da2-107">Paragraph styles are set through the `w:pPr` element; if a paragraph does not contain this element, it is formatted with the default style.</span></span>  
  
 <span data-ttu-id="51da2-108">このトピックでは、クエリを構成するいくつかの要素の意味を説明し、完全な作業例の一部分であるクエリを紹介します。</span><span class="sxs-lookup"><span data-stu-id="51da2-108">This topic explains the significance of some pieces of the query, then shows the query as part of a complete, working example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51da2-109">例</span><span class="sxs-lookup"><span data-stu-id="51da2-109">Example</span></span>  
 <span data-ttu-id="51da2-110">ドキュメント内のすべての段落とそのスタイルを取得するクエリのソースは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="51da2-110">The source of the query to retrieve all the paragraphs in a document and their styles is as follows:</span></span>  
  
```vb  
xDoc.Root.<w:body>...<w:p>  
```  
  
 <span data-ttu-id="51da2-111">この式は、クエリのソースの前の例に似ています[の既定の段落スタイル (Visual Basic) を検索する](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md)です。</span><span class="sxs-lookup"><span data-stu-id="51da2-111">This expression is similar to the source of the query in the previous example, [Finding the Default Paragraph Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/finding-the-default-paragraph-style.md).</span></span> <span data-ttu-id="51da2-112">主な違いは、<xref:System.Xml.Linq.XContainer.Descendants%2A> 軸の代わりに <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を使用している点です。</span><span class="sxs-lookup"><span data-stu-id="51da2-112">The main difference is that it uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis instead of the <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span> <span data-ttu-id="51da2-113">クエリで <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用しているのは、セクションが含まれているドキュメントの場合、段落が本文要素の直接の子とならず、階層内で 2 つ下のレベルに位置するためです。</span><span class="sxs-lookup"><span data-stu-id="51da2-113">The query uses the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis because in documents that have sections, the paragraphs will not be the direct children of the body element; rather, the paragraphs will be two levels down in the hierarchy.</span></span> <span data-ttu-id="51da2-114">コードで <xref:System.Xml.Linq.XContainer.Descendants%2A> 軸を使用すると、ドキュメントでセクションが使用されているかどうかにかかわらず機能するようになります。</span><span class="sxs-lookup"><span data-stu-id="51da2-114">By using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis, the code will work of whether or not the document uses sections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51da2-115">例</span><span class="sxs-lookup"><span data-stu-id="51da2-115">Example</span></span>  
 <span data-ttu-id="51da2-116">クエリで `Let` 句を使用して、スタイル ノードが含まれる要素を特定します。</span><span class="sxs-lookup"><span data-stu-id="51da2-116">The query uses a `Let` clause to determine the element that contains the style node.</span></span> <span data-ttu-id="51da2-117">要素がない場合は、`styleNode` が `Nothing` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="51da2-117">If there is no element, then `styleNode` is set to `Nothing`:</span></span>  
  
```vb  
Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault()  
```  
  
 <span data-ttu-id="51da2-118">`Let` 句は、まず <xref:System.Xml.Linq.XContainer.Elements%2A> 軸を使用して `pPr` という名前の要素すべてを検索し、次に <xref:System.Xml.Linq.Extensions.Elements%2A> 拡張メソッドを使用して `pStyle` という名前の子要素すべてを検索し、最後に <xref:System.Linq.Enumerable.FirstOrDefault%2A> 標準クエリ演算子を使用してコレクションをシングルトンに変換します。</span><span class="sxs-lookup"><span data-stu-id="51da2-118">The `Let` clause first uses the <xref:System.Xml.Linq.XContainer.Elements%2A> axis to find all elements named `pPr`, then uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method to find all child elements named `pStyle`, and finally uses the <xref:System.Linq.Enumerable.FirstOrDefault%2A> standard query operator to convert the collection to a singleton.</span></span> <span data-ttu-id="51da2-119">コレクションが空の場合は、`styleNode` が `Nothing` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="51da2-119">If the collection is empty, `styleNode` is set to `Nothing`.</span></span> <span data-ttu-id="51da2-120">これは、`pStyle` 子孫ノードを検索するのに便利な表現形式です。</span><span class="sxs-lookup"><span data-stu-id="51da2-120">This is a useful idiom to look for the `pStyle` descendant node.</span></span> <span data-ttu-id="51da2-121">`pPr` 子ノードが存在しない場合、コードが例外をスローして失敗することはなく、`styleNode` が `Nothing` に設定されます。これは、この `Let` 句で予期された動作です。</span><span class="sxs-lookup"><span data-stu-id="51da2-121">Note that if the `pPr` child node does not exist, the code does nor fail by throwing an exception; instead, `styleNode` is set to `Nothing`, which is the desired behavior of this `Let` clause.</span></span>  
  
 <span data-ttu-id="51da2-122">このクエリは、匿名型のコレクションを射影します。このコレクションには、`StyleName` および `ParagraphNode` の 2 つのメンバーがあります。</span><span class="sxs-lookup"><span data-stu-id="51da2-122">The query projects a collection of an anonymous type with two members, `StyleName` and `ParagraphNode`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51da2-123">例</span><span class="sxs-lookup"><span data-stu-id="51da2-123">Example</span></span>  
 <span data-ttu-id="51da2-124">この例では、WordprocessingML ドキュメントを処理して、WordprocessingML ドキュメントから段落ノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="51da2-124">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="51da2-125">それぞれの段落のスタイルも特定します。</span><span class="sxs-lookup"><span data-stu-id="51da2-125">It also identifies the style of each paragraph.</span></span> <span data-ttu-id="51da2-126">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="51da2-126">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="51da2-127">新しいクエリについては、以下のコード内にあるコメントで説明が示されています。</span><span class="sxs-lookup"><span data-stu-id="51da2-127">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="51da2-128">この例では、ソース ドキュメントを作成するための手順を参照して[ソース Office Open XML ドキュメント (Visual Basic) を作成する](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)です。</span><span class="sxs-lookup"><span data-stu-id="51da2-128">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="51da2-129">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="51da2-129">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="51da2-130">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="51da2-130">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Following is the new query that finds all paragraphs in the  
        ' document and their styles.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault() _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        For Each p In paragraphs  
            Console.WriteLine("StyleName:{0}", p.StyleName)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="51da2-131">この例には、次で説明されているドキュメントに適用されたときに出力が生成されます。[ソース Office Open XML ドキュメント (Visual Basic) を作成する](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)です。</span><span class="sxs-lookup"><span data-stu-id="51da2-131">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Code  
StyleName:Normal  
StyleName:Normal  
StyleName:Normal  
StyleName:Code  
```  
  
## <a name="next-steps"></a><span data-ttu-id="51da2-132">次の手順</span><span class="sxs-lookup"><span data-stu-id="51da2-132">Next Steps</span></span>  
 <span data-ttu-id="51da2-133">次のトピックで[(Visual Basic)、段落のテキストを取得して](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)段落のテキストを取得するクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="51da2-133">In the next topic, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), you'll create a query to retrieve the text of paragraphs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51da2-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="51da2-134">See Also</span></span>  
 [<span data-ttu-id="51da2-135">チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作</span><span class="sxs-lookup"><span data-stu-id="51da2-135">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
