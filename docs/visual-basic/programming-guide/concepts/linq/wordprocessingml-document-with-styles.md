---
title: "Styles2 を含む WordprocessingML ドキュメント |Microsoft ドキュメント"
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
ms.assetid: a9136e4d-c368-4661-8049-7d45c679a236
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d88d5a2494ac07aee98e5f98c47acc797bb1fcbc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="feb50-102">スタイルを含む WordprocessingML ドキュメント</span><span class="sxs-lookup"><span data-stu-id="feb50-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="feb50-103">複雑な WordprocessingML ドキュメントには、スタイルを使用して書式設定された段落が含まれています。</span><span class="sxs-lookup"><span data-stu-id="feb50-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="feb50-104">WordprocessingML ドキュメントを構成する場合に役立つ情報をいくつか説明します。</span><span class="sxs-lookup"><span data-stu-id="feb50-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="feb50-105">WordprocessingML ドキュメントはパッケージに格納されます。</span><span class="sxs-lookup"><span data-stu-id="feb50-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="feb50-106">パッケージには複数のパーツがあります (パーツは、パッケージのコンテキストで使用する場合は明示的な意味を持っています。基本的には、パーツとはパッケージを構成するためにまとめて圧縮されたファイルです)。</span><span class="sxs-lookup"><span data-stu-id="feb50-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="feb50-107">スタイルを使用して書式設定された段落がドキュメントに含まれている場合、スタイルが適用されている段落を含むドキュメント パーツがあります。</span><span class="sxs-lookup"><span data-stu-id="feb50-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="feb50-108">ドキュメントによって参照されるスタイルを含むスタイル パーツもあります。</span><span class="sxs-lookup"><span data-stu-id="feb50-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="feb50-109">パッケージにアクセスする場合、任意のパスを使用してではなく、パーツ間のリレーションシップを通じてアクセスすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="feb50-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="feb50-110">この問題が WordprocessingML ドキュメントのチュートリアルではコンテンツの操作の範囲を超えてが、このチュートリアルに含まれているプログラム例では、適切なアプローチを示します。</span><span class="sxs-lookup"><span data-stu-id="feb50-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="feb50-111">スタイルを使用するドキュメント</span><span class="sxs-lookup"><span data-stu-id="feb50-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="feb50-112">WordML の例、 [WordprocessingML ドキュメントの構造 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md)トピックでは、非常に単純なものです。</span><span class="sxs-lookup"><span data-stu-id="feb50-112">The WordML example presented in the [Shape of WordprocessingML Documents (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="feb50-113">次のドキュメントはより複雑で、スタイルを使用して書式設定された段落を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="feb50-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="feb50-114">Office Open XML ドキュメントを構成する XML では、実行する最も簡単な方法、[その出力 Office Open XML ドキュメント パーツ (Visual Basic) の使用例](../../../../visual-basic/programming-guide/concepts/linq/example-that-outputs-office-open-xml-document-parts.md)します。</span><span class="sxs-lookup"><span data-stu-id="feb50-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="feb50-115">次のドキュメントでは、最初の段落にスタイル `Heading1` が設定されています。</span><span class="sxs-lookup"><span data-stu-id="feb50-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="feb50-116">既定のスタイルが設定されている段落が多数あります。</span><span class="sxs-lookup"><span data-stu-id="feb50-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="feb50-117">スタイル `Code` が設定されている段落も多数あります。</span><span class="sxs-lookup"><span data-stu-id="feb50-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="feb50-118">このドキュメントは比較的複雑であるため、LINQ to XML を使用した解析を行うのに適したドキュメントといえます。</span><span class="sxs-lookup"><span data-stu-id="feb50-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="feb50-119">既定以外のスタイルが設定されている段落では、段落要素に `w:pPr` という名前の子要素があり、この子要素には `w:pStyle` という子要素があります。</span><span class="sxs-lookup"><span data-stu-id="feb50-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="feb50-120">
          `w:val` 要素には、スタイル名を格納する  という属性があります。</span><span class="sxs-lookup"><span data-stu-id="feb50-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="feb50-121">段落に既定のスタイルが設定されている場合は、段落要素に `w:p.Pr` 子要素はありません。</span><span class="sxs-lookup"><span data-stu-id="feb50-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
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
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Heading1" />  
      </w:pPr>  
      <w:r>  
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>The following example prints to the console.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>using System;</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>class Program {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    public static void </w:t>  
      </w:r>  
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">  
        <w:r w:rsidRPr="00876F34">  
          <w:t>Main</w:t>  
        </w:r>  
      </w:smartTag>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>(string[] args) {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    }</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>}</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>This example produces the following output:</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>Hello World</w:t>  
      </w:r>  
    </w:p>  
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">  
      <w:pgSz w:w="12240" w:h="15840" />  
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />  
      <w:cols w:space="720" />  
      <w:docGrid w:linePitch="360" />  
    </w:sectPr>  
  </w:body>  
</w:document>  
```  
  
## <a name="see-also"></a><span data-ttu-id="feb50-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="feb50-122">See Also</span></span>  
 [<span data-ttu-id="feb50-123">Office の詳細については Open XML WordprocessingML ドキュメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="feb50-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
