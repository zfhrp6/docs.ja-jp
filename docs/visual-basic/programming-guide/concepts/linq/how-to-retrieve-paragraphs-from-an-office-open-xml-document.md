---
title: "方法: Office Open XML ドキュメント (Visual Basic の場合) から段落を取得 |Microsoft ドキュメント"
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
ms.assetid: 66053f21-9217-473c-a6f3-a0897be07756
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3a62f64f2c923f8f8c8f85f7f9e5e6b7dbcef3d1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="how-to-retrieve-paragraphs-from-an-office-open-xml-document-visual-basic"></a><span data-ttu-id="f877c-102">方法: Office Open XML ドキュメント (Visual Basic の場合) から段落を取得</span><span class="sxs-lookup"><span data-stu-id="f877c-102">How to: Retrieve Paragraphs from an Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="f877c-103">このトピックでは、Office Open XML ドキュメントを開き、そのドキュメント内のすべての段落のコレクションを取得する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="f877c-103">This topic presents an example that opens an Office Open XML document, and retrieves a collection of all of the paragraphs in the document.</span></span>  
  
 <span data-ttu-id="f877c-104">Office Open XML の詳細については、次を参照してください。 [www.openxmldeveloper.org](http://go.microsoft.com/fwlink/?LinkID=95573)します。</span><span class="sxs-lookup"><span data-stu-id="f877c-104">For more information on Office Open XML, see [www.openxmldeveloper.org](http://go.microsoft.com/fwlink/?LinkID=95573).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f877c-105">例</span><span class="sxs-lookup"><span data-stu-id="f877c-105">Example</span></span>  
 <span data-ttu-id="f877c-106">この例では、Office Open XML パッケージを開き、Open XML パッケージ内のリレーションシップを使用してドキュメントとスタイル パーツを検索します。</span><span class="sxs-lookup"><span data-stu-id="f877c-106">This example opens an Office Open XML package, uses the relationships within the Open XML package to find the document and the style parts.</span></span> <span data-ttu-id="f877c-107">段落を含む匿名型のコレクションを射影、ドキュメントを照会し、<xref:System.Xml.Linq.XElement>ノード、各段落のスタイル名、および各段落のテキスト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="f877c-107">It then queries the document, projecting a collection of an anonymous type that contains the paragraph <xref:System.Xml.Linq.XElement> node, the style name of each paragraph, and the text of each paragraph.</span></span>  
  
 <span data-ttu-id="f877c-108">この例では、例の中でも提供される `StringConcatenate` という名前の拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f877c-108">The example uses an extension method named `StringConcatenate`, which is also supplied in the example.</span></span>  
  
 <span data-ttu-id="f877c-109">この例の動作を説明する詳細なチュートリアルについては[純粋関数型変換の XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="f877c-109">For a detailed tutorial that explains how this example works, see [Pure Functional Transformations of XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).</span></span>  
  
 <span data-ttu-id="f877c-110">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="f877c-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="f877c-111">内の型を使用して、<xref:System.IO.Packaging?displayProperty=fullName>名前空間</xref:System.IO.Packaging?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="f877c-111">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
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
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, ByVal defaultStyle As String) _  
                As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage _  
              .GetRelationshipsByType(documentRelationshipType) _  
              .FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = _  
                  PackUriHelper _  
                  .ResolvePartUri(New Uri("/", UriKind.Relative), docPackageRelationship.TargetUri)  
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
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f877c-112">実行する」に記載するサンプルの Open XML ドキュメントと[ソース Office Open XML ドキュメント (Visual Basic) を作成する](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)、この例は、次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="f877c-112">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="see-also"></a><span data-ttu-id="f877c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f877c-113">See Also</span></span>  
 [<span data-ttu-id="f877c-114">詳細クエリ手法 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f877c-114">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
