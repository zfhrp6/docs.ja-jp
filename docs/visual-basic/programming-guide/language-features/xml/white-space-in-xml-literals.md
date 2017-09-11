---
title: "XML リテラル (Visual Basic) での空白文字 |Microsoft ドキュメント"
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
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4fc3d30a9c71cbd732597c5e3f32bd01eb489a80
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="75495-102">XML リテラルでの空白文字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75495-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="75495-103">[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]の作成時にコンパイラに XML リテラルの有意の空白文字だけが組み込まれて、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="75495-103">The [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] object.</span></span> <span data-ttu-id="75495-104">余分な空白文字は組み込まれません。</span><span class="sxs-lookup"><span data-stu-id="75495-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="75495-105">有意の空白文字</span><span class="sxs-lookup"><span data-stu-id="75495-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="75495-106">XML リテラルの空白文字、重要な&3; つのみ分類されます。</span><span class="sxs-lookup"><span data-stu-id="75495-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="75495-107">属性値に含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="75495-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="75495-108">要素のテキスト コンテンツの一部であるし、テキストには、その他の文字も含まれています。</span><span class="sxs-lookup"><span data-stu-id="75495-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="75495-109">要素のテキスト コンテンツに組み込み式に含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="75495-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="75495-110">それ以外の場合、コンパイラとして意味のない空白文字を処理しでは、含まれません、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]リテラルのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="75495-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="75495-111">余分な空白を XML リテラルに含めるには、空白文字をリテラル文字列を含む埋め込み式を使用します。</span><span class="sxs-lookup"><span data-stu-id="75495-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75495-112">場合、`xml:space`リテラルで XML 要素に属性が表示されます、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラには、属性が用意されています、<xref:System.Xml.Linq.XElement>オブジェクトはこの属性は、コンパイラが空白文字を処理する方法を変更していない追加しようとします</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="75495-112">If the `xml:space` attribute appears in an XML element literal, the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="75495-113">例</span><span class="sxs-lookup"><span data-stu-id="75495-113">Examples</span></span>  
 <span data-ttu-id="75495-114">次の例には、外側と内側の&2; つの XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="75495-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="75495-115">両方の要素には、そのテキストの内容に空白が含まれています。</span><span class="sxs-lookup"><span data-stu-id="75495-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="75495-116">空白と XML 要素のみが含まれているため、外側の要素内の空白は意味はありません。</span><span class="sxs-lookup"><span data-stu-id="75495-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="75495-117">空白文字とテキストが含まれているために、内部の要素内の空白は重要です。</span><span class="sxs-lookup"><span data-stu-id="75495-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 <span data-ttu-id="75495-118">[!code-vb[VbXMLSamples #&29;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="75495-118">[!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]</span></span>  
  
 <span data-ttu-id="75495-119">実行すると、このコードは、次のテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="75495-119">When run, this code displays the following text.</span></span>  
  
```  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="75495-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="75495-120">See Also</span></span>  
 [<span data-ttu-id="75495-121">Visual Basic で XML を作成します。</span><span class="sxs-lookup"><span data-stu-id="75495-121">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
