---
title: XML リテラルでの空白文字 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6d23aa54b150748aac9aa955f4bd86ee88358ea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="white-space-in-xml-literals-visual-basic"></a><span data-ttu-id="dc5bb-102">XML リテラルでの空白文字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc5bb-102">White Space in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="dc5bb-103">作成時に、Visual Basic コンパイラは、XML リテラルの有意の空白文字だけが組み込まれて、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-103">The Visual Basic compiler incorporates only the significant white space characters from an XML literal when it creates a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object.</span></span> <span data-ttu-id="dc5bb-104">意味のない空白文字は組み込まれません。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-104">The insignificant white space characters are not incorporated.</span></span>  
  
## <a name="significant-and-insignificant-white-space"></a><span data-ttu-id="dc5bb-105">有意の空白文字</span><span class="sxs-lookup"><span data-stu-id="dc5bb-105">Significant and Insignificant White Space</span></span>  
 <span data-ttu-id="dc5bb-106">3 つだけの領域で XML リテラルの空白文字が重要です。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-106">White space characters in XML literals are significant in only three areas:</span></span>  
  
-   <span data-ttu-id="dc5bb-107">属性値に含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-107">When they are in an attribute value.</span></span>  
  
-   <span data-ttu-id="dc5bb-108">要素のテキスト コンテンツの一部であるし、テキストには、その他の文字も含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-108">When they are part of an element's text content and the text also contains other characters.</span></span>  
  
-   <span data-ttu-id="dc5bb-109">要素のテキスト コンテンツの埋め込み式に含まれる場合。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-109">When they are in an embedded expression for an element's text content.</span></span>  
  
 <span data-ttu-id="dc5bb-110">それ以外の場合、コンパイラとして意味のない空白文字を処理し、で、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]リテラルのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-110">Otherwise, the compiler treats white space characters as insignificant and does not include then in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] object for the literal.</span></span>  
  
 <span data-ttu-id="dc5bb-111">XML リテラルに意味のない空白を含める、文字列リテラルの空白文字を含む埋め込み式を使用します。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-111">To include insignificant white space in an XML literal, use an embedded expression that contains a string literal with the white space.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc5bb-112">場合、 `xml:space` XML 要素リテラルの属性が表示されます、Visual Basic コンパイラにはで属性が含まれています、<xref:System.Xml.Linq.XElement>オブジェクトが、この属性は、コンパイラが空白文字を処理する方法を変更していないを追加します。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-112">If the `xml:space` attribute appears in an XML element literal, the Visual Basic compiler includes the attribute in the <xref:System.Xml.Linq.XElement> object, but adding this attribute does not change how the compiler treats white space.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="dc5bb-113">使用例</span><span class="sxs-lookup"><span data-stu-id="dc5bb-113">Examples</span></span>  
 <span data-ttu-id="dc5bb-114">次の例には、外部および内部の 2 つの XML 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-114">The following example contains two XML elements, outer and inner.</span></span> <span data-ttu-id="dc5bb-115">両方の要素には、テキスト コンテンツ内の空白が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-115">Both elements contain white space in their text content.</span></span> <span data-ttu-id="dc5bb-116">空白文字と XML 要素のみが含まれているため、外側の要素内の空白は意味はありません。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-116">The white space in the outer element is insignificant because it contains only white space and an XML element.</span></span> <span data-ttu-id="dc5bb-117">空白とテキストが含まれているためには、内部の要素内の空白を使用することは重要です。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-117">The white space in the inner element is significant because it contains white space and text.</span></span>  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 <span data-ttu-id="dc5bb-118">実行すると、このコードは、次のテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="dc5bb-118">When run, this code displays the following text.</span></span>  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dc5bb-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc5bb-119">See Also</span></span>  
 [<span data-ttu-id="dc5bb-120">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="dc5bb-120">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
