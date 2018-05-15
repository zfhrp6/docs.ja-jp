---
title: Word 文書 (Visual Basic) でのテキストの検索
ms.date: 07/20/2015
ms.assetid: eea9819b-a78a-4552-bf13-8837fc0e7a37
ms.openlocfilehash: d9f9b0066a1f9b1fbe25c52f5bc23721b9e813c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="finding-text-in-word-documents-visual-basic"></a><span data-ttu-id="946f3-102">Word 文書 (Visual Basic) でのテキストの検索</span><span class="sxs-lookup"><span data-stu-id="946f3-102">Finding Text in Word Documents (Visual Basic)</span></span>
<span data-ttu-id="946f3-103">このトピックでは、以前のクエリを拡張して、ドキュメント内で特定の文字列の出現箇所をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="946f3-103">This topic extends the previous queries to do something useful: find all occurrences of a string in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="946f3-104">例</span><span class="sxs-lookup"><span data-stu-id="946f3-104">Example</span></span>  
 <span data-ttu-id="946f3-105">この例では、WordprocessingML ドキュメントを処理して、ドキュメント内で特定のテキストの出現箇所をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="946f3-105">This example processes a WordprocessingML document, to find all the occurences of a specific piece of text in the document.</span></span> <span data-ttu-id="946f3-106">ここではそのために、"Hello" という文字列を検索するクエリを使用します。</span><span class="sxs-lookup"><span data-stu-id="946f3-106">To do this, we use a query that finds the string "Hello".</span></span> <span data-ttu-id="946f3-107">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="946f3-107">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="946f3-108">新しいクエリについては、以下のコード内にあるコメントで説明が示されています。</span><span class="sxs-lookup"><span data-stu-id="946f3-108">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="946f3-109">この例のソース ドキュメントを作成する方法の詳細については、次を参照してください。[ソース Office Open XML ドキュメント (Visual Basic) を作成する](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)です。</span><span class="sxs-lookup"><span data-stu-id="946f3-109">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="946f3-110">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="946f3-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="946f3-111">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="946f3-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because VB does not support short circuit evaluation  
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
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = ParagraphText(para.ParagraphNode) _  
            }  
  
        ' Following is the new query that retrieves all paragraphs  
        ' that have specific text in them.  
        Dim helloParagraphs = _  
            From para In paraWithText _  
            Where para.Text.Contains("Hello") _  
            Select New With _  
            { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.Text _  
            }  
  
        For Each p In helloParagraphs  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="946f3-112">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="946f3-112">This example produces the following output:</span></span>  
  
```  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >Hello World<  
```  
  
 <span data-ttu-id="946f3-113">この検索に変更を加えて、特定のスタイルの行を検索することもできます。</span><span class="sxs-lookup"><span data-stu-id="946f3-113">You can, of course, modify the search so that it searches for lines with a specific style.</span></span> <span data-ttu-id="946f3-114">次のクエリは、Code スタイルの空白行をすべて検索します。</span><span class="sxs-lookup"><span data-stu-id="946f3-114">The following query finds all blank lines that have the Code style:</span></span>  
  
```vb  
Imports System.IO.Packaging  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because VB does not support short circuit evaluation  
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
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = ParagraphText(para.ParagraphNode) _  
            }  
  
        ' Retrieve all paragraphs that have no text and are styled Code.  
        Dim blankCodeParagraphs = _  
            From para In paraWithText _  
            Where String.IsNullOrEmpty(para.Text) And para.StyleName.Equals("Code") _  
            Select New With _  
            { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.Text _  
            }  
  
        For Each p In blankCodeParagraphs  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="946f3-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="946f3-115">This example produces the following output:</span></span>  
  
```  
StyleName:Code ><  
```  
  
 <span data-ttu-id="946f3-116">この例はさまざまな形で強化できます。</span><span class="sxs-lookup"><span data-stu-id="946f3-116">Of course, this example could be enhanced in a number of ways.</span></span> <span data-ttu-id="946f3-117">たとえば、正規表現を使用してテキストを検索したり、特定のディレクトリにあるすべての Word ファイルを反復処理したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="946f3-117">For example, we could use regular expressions to search for text, we could iterate through all the Word files in a particular directory, and so on.</span></span>  
  
 <span data-ttu-id="946f3-118">この例は、1 つのクエリとして記述された場合とほぼ同程度のパフォーマンスを発揮します。</span><span class="sxs-lookup"><span data-stu-id="946f3-118">Note that this example performs approximately as well as if it were written as a single query.</span></span> <span data-ttu-id="946f3-119">各クエリはレイジー遅延方式で実装されているため、反復処理されるまで結果は生成されません。</span><span class="sxs-lookup"><span data-stu-id="946f3-119">Because each query is implemented in a lazy, deferred fashion, each query does not yield its results until the query is iterated.</span></span> <span data-ttu-id="946f3-120">実行とレイジー評価の詳細については、次を参照してください。[遅延実行とレイジー評価を LINQ to XML (Visual Basic) で](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="946f3-120">For more information about execution and lazy evaluation, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="946f3-121">次の手順</span><span class="sxs-lookup"><span data-stu-id="946f3-121">Next Steps</span></span>  
 <span data-ttu-id="946f3-122">次のセクションでは、WordprocessingML ドキュメントについて詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="946f3-122">The next section provides more information about WordprocessingML documents:</span></span>  
  
-   [<span data-ttu-id="946f3-123">Office の詳細は Open XML WordprocessingML ドキュメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946f3-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)  
  
## <a name="see-also"></a><span data-ttu-id="946f3-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="946f3-124">See Also</span></span>  
 [<span data-ttu-id="946f3-125">チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作</span><span class="sxs-lookup"><span data-stu-id="946f3-125">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)  
 [<span data-ttu-id="946f3-126">純粋関数によるリファクタリング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946f3-126">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
 [<span data-ttu-id="946f3-127">遅延実行とレイジー評価で LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="946f3-127">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
