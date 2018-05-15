---
title: Office Open XML ドキュメント パーツ (Visual Basic) を出力する例
ms.date: 07/20/2015
ms.assetid: a951925b-c985-48ed-b215-2a68b58f1ae5
ms.openlocfilehash: 2e4b03d89a5b1eabb5751d807ef78442a960389d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="example-that-outputs-office-open-xml-document-parts-visual-basic"></a><span data-ttu-id="b07a8-102">Office Open XML ドキュメント パーツ (Visual Basic) を出力する例</span><span class="sxs-lookup"><span data-stu-id="b07a8-102">Example that Outputs Office Open XML Document Parts (Visual Basic)</span></span>
<span data-ttu-id="b07a8-103">このトピックでは、Office Open XML ドキュメントを開き、ドキュメント内のパーツにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b07a8-103">This topic shows how to open an Office Open XML document and access parts within it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b07a8-104">例</span><span class="sxs-lookup"><span data-stu-id="b07a8-104">Example</span></span>  
 <span data-ttu-id="b07a8-105">次の例では、Office Open XML ドキュメントを開き、ドキュメント パーツとスタイル パーツをコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="b07a8-105">The following example opens an Office Open XML document, and prints the document part and the style part to the console.</span></span>  
  
 <span data-ttu-id="b07a8-106">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="b07a8-106">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="b07a8-107">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="b07a8-107">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Const fileName As String = "SampleDoc.docx"  
  
Const documentRelationshipType As String = _  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
Const stylesRelationshipType As String = _  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
Const wordmlNamespace As String = _  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
Dim w As XNamespace = wordmlNamespace  
  
Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
    Dim docPackageRelationship As PackageRelationship = _  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
    If docPackageRelationship IsNot Nothing Then  
        Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
          docPackageRelationship.TargetUri)  
        Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
        ' Load the document XML in the part into an XDocument instance.  
        Dim xdoc As XDocument = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
        Console.WriteLine("TargetUri:{0}", docPackageRelationship.TargetUri)  
        Console.WriteLine("==================================================================")  
        Console.WriteLine(xdoc.Root)  
        Console.WriteLine()  
  
        ' Find the styles part. There will only be one.  
        Dim styleRelation As PackageRelationship = _  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
        If styleRelation IsNot Nothing Then  
            Dim styleUri As Uri = _  
              PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
            Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
            ' Load the style XML in the part into an XDocument instance.  
            Dim styleDoc As XDocument = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
  
            Console.WriteLine("TargetUri:{0}", styleRelation.TargetUri)  
            Console.WriteLine("==================================================================")  
            Console.WriteLine(styleDoc.Root)  
            Console.WriteLine()  
        End If  
    End If  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="b07a8-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="b07a8-108">See Also</span></span>  
 [<span data-ttu-id="b07a8-109">Office の詳細は Open XML WordprocessingML ドキュメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b07a8-109">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
