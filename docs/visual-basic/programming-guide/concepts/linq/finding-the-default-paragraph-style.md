---
title: 既定の段落スタイル (Visual Basic) を検索します。
ms.date: 07/20/2015
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
ms.openlocfilehash: 77e6e6db321b5f8ef338706e5f938daa02d115eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="78eaa-102">既定の段落スタイル (Visual Basic) を検索します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="78eaa-103">「WordprocessingML ドキュメント内の情報の操作」チュートリアルでの最初のタスクは、ドキュメント内にある段落の既定のスタイルを検索することです。</span><span class="sxs-lookup"><span data-stu-id="78eaa-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78eaa-104">例</span><span class="sxs-lookup"><span data-stu-id="78eaa-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="78eaa-105">説明</span><span class="sxs-lookup"><span data-stu-id="78eaa-105">Description</span></span>  
 <span data-ttu-id="78eaa-106">次の例では、Office Open XML WordprocessingML ドキュメントを開き、パッケージのドキュメント パーツとスタイル パーツを検索した後、既定のスタイル名を検索するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="78eaa-107">Office Open XML ドキュメントのパッケージとので構成されている部分については、次を参照してください。[詳細 Office Open XML WordprocessingML ドキュメントの (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)です。</span><span class="sxs-lookup"><span data-stu-id="78eaa-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="78eaa-108">このクエリは、値が "paragraph" である `w:style` という名前の属性と、値が "1" である `w:type` という名前の属性を持つ `w:default` という名前のノードを検索します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="78eaa-109">これらの属性を持つ XML ノードは 1 つしかないため、このクエリは、<xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> 演算子を使用してコレクションをシングルトンに変換します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=nameWithType> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="78eaa-110">次に、`w:styleId` という名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="78eaa-111">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="78eaa-112">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="78eaa-113">コード</span><span class="sxs-lookup"><span data-stu-id="78eaa-113">Code</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
  
    Sub Main()  
  
        Const fileName As String = "SampleDoc.docx"  
  
        Const documentRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Const stylesRelationshipType As String = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If docPackageRelationship IsNot Nothing Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                ' Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If styleRelation IsNot Nothing Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        ' The following query finds all the paragraphs that have the default style.  
        Dim defParas As IEnumerable(Of XElement) = _  
            From style In styleDoc.Root.<w:style> _  
            Where style.@w:type.Equals("paragraph") And _  
                   style.@w:default.Equals("1") _  
            Select style  
        ' Then find the style of the first.  
        Dim defaultStyle As String = defParas.First().@w:styleId  
  
        Console.WriteLine("The default style is: " & defaultStyle)  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="78eaa-114">コメント</span><span class="sxs-lookup"><span data-stu-id="78eaa-114">Comments</span></span>  
 <span data-ttu-id="78eaa-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="78eaa-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="78eaa-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="78eaa-116">Next Steps</span></span>  
 <span data-ttu-id="78eaa-117">次の例では、ドキュメント内のすべての段落およびそのスタイルを検索する同様のクエリを記述します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="78eaa-118">段落とそのスタイル (Visual Basic) を取得します。</span><span class="sxs-lookup"><span data-stu-id="78eaa-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="78eaa-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="78eaa-119">See Also</span></span>  
 [<span data-ttu-id="78eaa-120">チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作</span><span class="sxs-lookup"><span data-stu-id="78eaa-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
