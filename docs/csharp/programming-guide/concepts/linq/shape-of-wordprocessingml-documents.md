---
title: "WordprocessingML ドキュメントの構造 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee03c9cd64c3c3b251049be0826c7b29abe80bfa
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2018
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="a15e0-102">WordprocessingML ドキュメントの構造 (C#)</span><span class="sxs-lookup"><span data-stu-id="a15e0-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="a15e0-103">このトピックでは、WordprocessingML ドキュメントの XML 構造について説明します。</span><span class="sxs-lookup"><span data-stu-id="a15e0-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="a15e0-104">Microsoft Office 形式</span><span class="sxs-lookup"><span data-stu-id="a15e0-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="a15e0-105">2007 Microsoft Office システムのネイティブ ファイル形式は Office Open XML (一般的な呼称は Open XML) です。</span><span class="sxs-lookup"><span data-stu-id="a15e0-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="a15e0-106">Open XML は Ecma 標準の XML ベースの形式であり、現在は ISO-IEC 標準としての検討が進められている段階です。</span><span class="sxs-lookup"><span data-stu-id="a15e0-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="a15e0-107">Open XML 内のワード プロセッシング ファイルのマークアップ言語は WordprocessingML と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="a15e0-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="a15e0-108">このチュートリアルの例では、WordprocessingML ソース ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="a15e0-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="a15e0-109">Microsoft Office 2003 を使用しており、Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats をインストールしている場合は、Office Open XML 形式でドキュメントを保存できます。</span><span class="sxs-lookup"><span data-stu-id="a15e0-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="a15e0-110">WordprocessingML ドキュメントの構造</span><span class="sxs-lookup"><span data-stu-id="a15e0-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="a15e0-111">最初に理解する必要があるのは WordprocessingML ドキュメントの構造です。</span><span class="sxs-lookup"><span data-stu-id="a15e0-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="a15e0-112">WordprocessingML ドキュメントには、ドキュメントの段落を含む本文要素 (名前は `w:body`) が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="a15e0-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="a15e0-113">各段落には、1 つ以上のテキスト ラン (名前は `w:r`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a15e0-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="a15e0-114">各テキスト ランには、1 つ以上のテキスト片 (名前は `w:t`) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a15e0-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="a15e0-115">非常に単純な WordprocessingML ドキュメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a15e0-115">The following is a very simple WordprocessingML document:</span></span>  
  
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
  
 <span data-ttu-id="a15e0-116">このドキュメントには、2 つの段落が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a15e0-116">This document contains two paragraphs.</span></span> <span data-ttu-id="a15e0-117">各段落には 1 つのテキスト ランが含まれており、各テキスト ランには 1 つのテキスト片が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a15e0-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="a15e0-118">WordprocessingML ドキュメントの内容を XML 形式で表示する最も簡単な方法は、Microsoft Word を使用して WordprocessingML ドキュメントを作成および保存し、次のプログラムを実行してコンソールに XML を出力することです。</span><span class="sxs-lookup"><span data-stu-id="a15e0-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="a15e0-119">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a15e0-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="a15e0-120">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="a15e0-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="a15e0-121">外部リソース</span><span class="sxs-lookup"><span data-stu-id="a15e0-121">External Resources</span></span>  
 [<span data-ttu-id="a15e0-122">Office (2007) Open XML ファイル形式の概要</span><span class="sxs-lookup"><span data-stu-id="a15e0-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://msdn.microsoft.com/library/ms406049.aspx)  
 <span data-ttu-id="a15e0-123">[WordprocessingML の概要](https://msdn.microsoft.com/library/aa212812(office.11).aspx)</span><span class="sxs-lookup"><span data-stu-id="a15e0-123">[Overview of WordprocessingML](https://msdn.microsoft.com/library/aa212812(office.11).aspx)</span></span>  
 [<span data-ttu-id="a15e0-124">WordProcessingML ファイルの構造</span><span class="sxs-lookup"><span data-stu-id="a15e0-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)  
 [<span data-ttu-id="a15e0-125">WordprocessingML の概要</span><span class="sxs-lookup"><span data-stu-id="a15e0-125">Introduction to WordprocessingML</span></span>](http://ericwhite.com/blog/introduction-to-wordprocessingml-series/)  
 [<span data-ttu-id="a15e0-126">Office 2003: XML リファレンス スキーマのダウンロード ページ</span><span class="sxs-lookup"><span data-stu-id="a15e0-126">Office 2003: XML Reference Schemas Download page</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=101)  
  
## <a name="see-also"></a><span data-ttu-id="a15e0-127">参照</span><span class="sxs-lookup"><span data-stu-id="a15e0-127">See Also</span></span>  
 [<span data-ttu-id="a15e0-128">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="a15e0-128">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
