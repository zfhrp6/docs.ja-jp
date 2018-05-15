---
title: WordprocessingML ドキュメント (Visual Basic) の構造
ms.date: 07/20/2015
ms.assetid: 2dfb446b-5a07-4c00-9ab3-a74ba734ff3a
ms.openlocfilehash: 40d1013d5b5c131cc0b83c1b62bff2555ab179a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="shape-of-wordprocessingml-documents-visual-basic"></a><span data-ttu-id="69017-102">WordprocessingML ドキュメント (Visual Basic) の構造</span><span class="sxs-lookup"><span data-stu-id="69017-102">Shape of WordprocessingML Documents (Visual Basic)</span></span>
<span data-ttu-id="69017-103">このトピックでは、WordprocessingML ドキュメントの XML 構造について説明します。</span><span class="sxs-lookup"><span data-stu-id="69017-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="69017-104">Microsoft Office 形式</span><span class="sxs-lookup"><span data-stu-id="69017-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="69017-105">2007 Microsoft Office システムのネイティブ ファイル形式は Office Open XML (一般的な呼称は Open XML) です。</span><span class="sxs-lookup"><span data-stu-id="69017-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="69017-106">Open XML は Ecma 標準の XML ベースの形式であり、現在は ISO-IEC 標準としての検討が進められている段階です。</span><span class="sxs-lookup"><span data-stu-id="69017-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="69017-107">Open XML 内のワード プロセッシング ファイルのマークアップ言語は WordprocessingML と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="69017-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="69017-108">このチュートリアルの例では、WordprocessingML ソース ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="69017-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="69017-109">Microsoft Office 2003 を使用しており、Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats をインストールしている場合は、Office Open XML 形式でドキュメントを保存できます。</span><span class="sxs-lookup"><span data-stu-id="69017-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="69017-110">WordprocessingML ドキュメントの構造</span><span class="sxs-lookup"><span data-stu-id="69017-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="69017-111">最初に理解する必要があるのは WordprocessingML ドキュメントの構造です。</span><span class="sxs-lookup"><span data-stu-id="69017-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="69017-112">WordprocessingML ドキュメントには、ドキュメントの段落を含む本文要素 (名前は `w:body`) が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="69017-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="69017-113">各段落には、1 つ以上のテキスト ラン (名前は `w:r`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="69017-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="69017-114">各テキスト ランには、1 つ以上のテキスト片 (名前は `w:t`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="69017-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="69017-115">非常に単純な WordprocessingML ドキュメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="69017-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="69017-116">このドキュメントには、2 つの段落が含まれています。</span><span class="sxs-lookup"><span data-stu-id="69017-116">This document contains two paragraphs.</span></span> <span data-ttu-id="69017-117">各段落には 1 つのテキスト ランが含まれており、各テキスト ランには 1 つのテキスト片が含まれています。</span><span class="sxs-lookup"><span data-stu-id="69017-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="69017-118">WordprocessingML ドキュメントの内容を XML 形式で表示する最も簡単な方法は、Microsoft Word を使用して WordprocessingML ドキュメントを作成および保存し、次のプログラムを実行してコンソールに XML を出力することです。</span><span class="sxs-lookup"><span data-stu-id="69017-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="69017-119">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="69017-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="69017-120">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="69017-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    Sub Main()  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
  
        Using wdPackage As Package = _  
          Package.Open("SampleDoc.docx", _  
                       FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri( _  
                            New Uri("/", UriKind.Relative), _  
                            docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                ' Get the officeDocument part from the package.  
                ' Load the XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = _  
                    XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
                Console.WriteLine(xDoc.Root)  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
## <a name="external-resources"></a><span data-ttu-id="69017-121">外部リソース</span><span class="sxs-lookup"><span data-stu-id="69017-121">External Resources</span></span>  
 [<span data-ttu-id="69017-122">Office (2007) Open XML ファイル形式の概要</span><span class="sxs-lookup"><span data-stu-id="69017-122">Introducing the Office (2007) Open XML File Formats</span></span>](http://go.microsoft.com/fwlink/?LinkId=98093)  
  
 [<span data-ttu-id="69017-123">WordprocessingML の概要</span><span class="sxs-lookup"><span data-stu-id="69017-123">Overview of WordprocessingML</span></span>](http://go.microsoft.com/fwlink/?LinkId=98094)  
  
 [<span data-ttu-id="69017-124">Office 2003: XML リファレンス スキーマのダウンロード ページ</span><span class="sxs-lookup"><span data-stu-id="69017-124">Office 2003: XML Reference Schemas Download page</span></span>](http://go.microsoft.com/fwlink/?LinkId=98095)  
  
## <a name="see-also"></a><span data-ttu-id="69017-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="69017-125">See Also</span></span>  
 [<span data-ttu-id="69017-126">チュートリアル: WordprocessingML ドキュメント (Visual Basic) 内のコンテンツの操作</span><span class="sxs-lookup"><span data-stu-id="69017-126">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
