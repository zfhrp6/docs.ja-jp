---
title: "既定の段落スタイル (Visual Basic) の検索 |Microsoft ドキュメント"
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
ms.assetid: 9d094a4a-ec8c-41b0-b7ab-a3deb2a01d45
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 22d97c95a1dec52c0290555daeedce51c5a567e3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="finding-the-default-paragraph-style-visual-basic"></a><span data-ttu-id="4ef8c-102">既定の段落スタイル (Visual Basic) の検索</span><span class="sxs-lookup"><span data-stu-id="4ef8c-102">Finding the Default Paragraph Style (Visual Basic)</span></span>
<span data-ttu-id="4ef8c-103">WordprocessingML ドキュメントのチュートリアルでの情報の操作の最初のタスクでは、ドキュメント内の段落の既定のスタイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-103">The first task in the Manipulating Information in a WordprocessingML Document tutorial is to find the default style of paragraphs in the document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ef8c-104">例</span><span class="sxs-lookup"><span data-stu-id="4ef8c-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="4ef8c-105">説明</span><span class="sxs-lookup"><span data-stu-id="4ef8c-105">Description</span></span>  
 <span data-ttu-id="4ef8c-106">次の例では、Office Open XML WordprocessingML ドキュメントを開き、パッケージのドキュメント パーツとスタイル パーツを検索した後、既定のスタイル名を検索するクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-106">The following example opens an Office Open XML WordprocessingML document, finds the document and style parts of the package, and then executes a query that finds the default style name.</span></span> <span data-ttu-id="4ef8c-107">Office Open XML ドキュメントのパッケージと構成のパーツについては、次を参照してください。[詳細の Office Open XML WordprocessingML ドキュメント (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)します。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-107">For information about Office Open XML document packages, and the parts they consist of, see [Details of Office Open XML WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md).</span></span>  
  
 <span data-ttu-id="4ef8c-108">このクエリは、値が "paragraph" である `w:style` という名前の属性と、値が "1" である `w:type` という名前の属性を持つ `w:default` という名前のノードを検索します。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-108">The query finds a node named `w:style` that has an attribute named `w:type` with a value of "paragraph", and also has an attribute named `w:default` with a value of "1".</span></span> <span data-ttu-id="4ef8c-109">クエリを使用してこれらの属性を持つ XML ノードを&1; つがありますので、<xref:System.Linq.Enumerable.First%2A?displayProperty=fullName>コレクションをシングルトンに変換する演算子</xref:System.Linq.Enumerable.First%2A?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-109">Because there will be only one XML node with these attributes, the query uses the <xref:System.Linq.Enumerable.First%2A?displayProperty=fullName> operator to convert a collection to a singleton.</span></span> <span data-ttu-id="4ef8c-110">次に、`w:styleId` という名前の属性の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-110">It then gets the value of the attribute with the name `w:styleId`.</span></span>  
  
 <span data-ttu-id="4ef8c-111">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="4ef8c-112">内の型を使用して、<xref:System.IO.Packaging?displayProperty=fullName>名前空間</xref:System.IO.Packaging?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-112">It uses types in the <xref:System.IO.Packaging?displayProperty=fullName> namespace.</span></span>  
  
### <a name="code"></a><span data-ttu-id="4ef8c-113">コード</span><span class="sxs-lookup"><span data-stu-id="4ef8c-113">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="4ef8c-114">コメント</span><span class="sxs-lookup"><span data-stu-id="4ef8c-114">Comments</span></span>  
 <span data-ttu-id="4ef8c-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-115">This example produces the following output:</span></span>  
  
```  
The default style is: Normal  
```  
  
## <a name="next-steps"></a><span data-ttu-id="4ef8c-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="4ef8c-116">Next Steps</span></span>  
 <span data-ttu-id="4ef8c-117">次の例では、ドキュメントとそのスタイル内のすべての段落を検索する同様のクエリを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ef8c-117">In the next example, you'll create a similar query that finds all the paragraphs in a document and their styles:</span></span>  
  
-   [<span data-ttu-id="4ef8c-118">段落とそのスタイル (Visual Basic) の取得</span><span class="sxs-lookup"><span data-stu-id="4ef8c-118">Retrieving the Paragraphs and Their Styles (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)  
  
## <a name="see-also"></a><span data-ttu-id="4ef8c-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ef8c-119">See Also</span></span>  
 [<span data-ttu-id="4ef8c-120">チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作</span><span class="sxs-lookup"><span data-stu-id="4ef8c-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
