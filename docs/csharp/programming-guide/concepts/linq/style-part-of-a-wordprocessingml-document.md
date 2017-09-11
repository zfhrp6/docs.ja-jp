---
title: "WordprocessingML ドキュメント1 のスタイル パーツ"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 5458bccf-3898-4661-904b-7d280c9239a9
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2ad635d5e7df887ac079d2a7267a40b762829298
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="style-part-of-a-wordprocessingml-document"></a><span data-ttu-id="bcec4-102">WordprocessingML ドキュメントのスタイル パーツ</span><span class="sxs-lookup"><span data-stu-id="bcec4-102">Style Part of a WordprocessingML Document</span></span>
<span data-ttu-id="bcec4-103">このトピックでは、Office Open XML WordprocessingML ドキュメントのスタイル パーツの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="bcec4-103">This topic shows an example of the style part of the Office Open XML WordprocessingML document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcec4-104">例</span><span class="sxs-lookup"><span data-stu-id="bcec4-104">Example</span></span>  
 <span data-ttu-id="bcec4-105">Office Open XML WordprocessingML ドキュメントのスタイル パーツを構成する XML の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bcec4-105">The following example is the XML that makes up the style part of an Office Open XML WordprocessingML document.</span></span>  
  
 <span data-ttu-id="bcec4-106">既定の段落スタイルには、次の開始タグを持つ要素があります。</span><span class="sxs-lookup"><span data-stu-id="bcec4-106">The default paragraph style has an element with the following opening tag:</span></span>  
  
```  
<w:style w:type="paragraph" w:default="1" w:styleId="Normal">  
```  
  
 <span data-ttu-id="bcec4-107">既定のスタイル識別子を検索するクエリを記述するときは、既定のスタイルを持つパラグラフのスタイルをクエリで識別できるようにするために、この情報を理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcec4-107">You need to know this information when you write the query to find the default style identifier, so that the query can identify the style of paragraphs that have the default style.</span></span>  
  
 <span data-ttu-id="bcec4-108">これらのドキュメントは、Microsoft Word によって生成される通常のドキュメントと比べると非常に単純です。</span><span class="sxs-lookup"><span data-stu-id="bcec4-108">Note that these documents are very simple when compared to typical documents that Microsoft Word generates.</span></span> <span data-ttu-id="bcec4-109">多くの場合、Word では多数の追加情報、追加の書式設定、およびメタデータが保存されます。</span><span class="sxs-lookup"><span data-stu-id="bcec4-109">In many cases, Word saves a great deal of additional information, additional formatting and metadata.</span></span> <span data-ttu-id="bcec4-110">さらに、この例とは異なり、Word では行を読みやすくするための書式設定が行われません。代わりに、XML はインデントなしで保存されます。</span><span class="sxs-lookup"><span data-stu-id="bcec4-110">Furthermore, Word does not format the lines to be easily readable as in this example; instead, the XML is saved without indentation.</span></span> <span data-ttu-id="bcec4-111">ただし、すべての WordprocessingML ドキュメントは、同一の XML 基本構造を共有します。</span><span class="sxs-lookup"><span data-stu-id="bcec4-111">However, all WordprocessingML documents share the same basic XML shape.</span></span> <span data-ttu-id="bcec4-112">このため、このチュートリアルで提供されるクエリは、より複雑なドキュメントを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="bcec4-112">Because of this, the queries presented in this tutorial will work with more complicated documents.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<w:styles  
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  <w:docDefaults>  
    <w:rPrDefault>  
      <w:rPr>  
        <w:rFonts  
            w:ascii="Times New Roman"  
            w:eastAsia="Times New Roman"  
            w:hAnsi="Times New Roman"  
            w:cs="Times New Roman" />  
        <w:sz w:val="22" />  
        <w:szCs w:val="22" />  
        <w:lang w:val="en-US" w:eastAsia="en-US" w:bidi="ar-SA" />  
      </w:rPr>  
    </w:rPrDefault>  
    <w:pPrDefault />  
  </w:docDefaults>  
  <w:style w:type="paragraph" w:default="1" w:styleId="Normal">  
    <w:name w:val="Normal" />  
    <w:qFormat />  
    <w:rPr>  
      <w:sz w:val="24" />  
      <w:szCs w:val="24" />  
    </w:rPr>  
  </w:style>  
  <w:style w:type="paragraph" w:styleId="Heading1">  
    <w:name w:val="heading 1" />  
    <w:basedOn w:val="Normal" />  
    <w:next w:val="Normal" />  
    <w:link w:val="Heading1Char" />  
    <w:uiPriority w:val="99" />  
    <w:qFormat />  
    <w:rsid w:val="006027C7" />  
    <w:pPr>  
      <w:keepNext />  
      <w:spacing w:before="240" w:after="60" />  
      <w:outlineLvl w:val="0" />  
    </w:pPr>  
    <w:rPr>  
      <w:rFonts w:ascii="Arial" w:hAnsi="Arial" w:cs="Arial" />  
      <w:b />  
      <w:bCs />  
      <w:kern w:val="32" />  
      <w:sz w:val="32" />  
      <w:szCs w:val="32" />  
    </w:rPr>  
  </w:style>  
  <w:style w:type="character" w:default="1" w:styleId="DefaultParagraphFont">  
    <w:name w:val="Default Paragraph Font" />  
    <w:uiPriority w:val="99" />  
    <w:semiHidden />  
  </w:style>  
  <w:style w:type="table" w:default="1" w:styleId="TableNormal">  
    <w:name w:val="Normal Table" />  
    <w:uiPriority w:val="99" />  
    <w:semiHidden />  
    <w:unhideWhenUsed />  
    <w:qFormat />  
    <w:tblPr>  
      <w:tblInd w:w="0" w:type="dxa" />  
      <w:tblCellMar>  
        <w:top w:w="0" w:type="dxa" />  
        <w:left w:w="108" w:type="dxa" />  
        <w:bottom w:w="0" w:type="dxa" />  
        <w:right w:w="108" w:type="dxa" />  
      </w:tblCellMar>  
    </w:tblPr>  
  </w:style>  
  <w:style w:type="numbering" w:default="1" w:styleId="NoList">  
    <w:name w:val="No List" />  
    <w:uiPriority w:val="99" />  
    <w:semiHidden />  
    <w:unhideWhenUsed />  
  </w:style>  
  <w:style w:type="character" w:customStyle="1" w:styleId="Heading1Char">  
    <w:name w:val="Heading 1 Char" />  
    <w:basedOn w:val="DefaultParagraphFont" />  
    <w:link w:val="Heading1" />  
    <w:uiPriority w:val="9" />  
    <w:rsid w:val="009765E3" />  
    <w:rPr>  
      <w:rFonts  
          w:asciiTheme="majorHAnsi"  
          w:eastAsiaTheme="majorEastAsia"  
          w:hAnsiTheme="majorHAnsi"  
          w:cstheme="majorBidi" />  
      <w:b />  
      <w:bCs />  
      <w:kern w:val="32" />  
      <w:sz w:val="32" />  
      <w:szCs w:val="32" />  
    </w:rPr>  
  </w:style>  
  <w:style w:type="paragraph" w:customStyle="1" w:styleId="Code">  
    <w:name w:val="Code" />  
    <w:aliases w:val="c" />  
    <w:uiPriority w:val="99" />  
    <w:rsid w:val="006027C7" />  
    <w:pPr>  
      <w:spacing w:after="60" w:line="300" w:lineRule="exact" />  
    </w:pPr>  
    <w:rPr>  
      <w:rFonts w:ascii="Courier New" w:hAnsi="Courier New" />  
      <w:noProof />  
      <w:color w:val="000080" />  
      <w:sz w:val="20" />  
      <w:szCs w:val="20" />  
    </w:rPr>  
  </w:style>  
</w:styles>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcec4-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcec4-113">See Also</span></span>  
 [<span data-ttu-id="bcec4-114">Office Open XML WordprocessingML ドキュメントの詳細 (C#)</span><span class="sxs-lookup"><span data-stu-id="bcec4-114">Details of Office Open XML WordprocessingML Documents (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)

