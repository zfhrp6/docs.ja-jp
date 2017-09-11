---
title: "XML (Visual Basic) の関数型変換 |Microsoft ドキュメント"
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
ms.assetid: fdbe5b91-f457-4b4e-a11b-def4bdd77bab
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8c41d464d5b214520ca5e36877fb59d45c851786
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017


---
# <a name="functional-transformation-of-xml-visual-basic"></a><span data-ttu-id="15d32-102">XML (Visual Basic) の関数型変換</span><span class="sxs-lookup"><span data-stu-id="15d32-102">Functional Transformation of XML (Visual Basic)</span></span>
<span data-ttu-id="15d32-103">このトピックでは、XML ドキュメントを変更するための純粋関数型変換の方法について説明し、手続き型の方法と比較します。</span><span class="sxs-lookup"><span data-stu-id="15d32-103">This topic discusses the pure functional transformation approach to modifying XML documents, and contrasts it with a procedural approach.</span></span>  
  
## <a name="modifying-an-xml-document"></a><span data-ttu-id="15d32-104">XML ドキュメントの変更</span><span class="sxs-lookup"><span data-stu-id="15d32-104">Modifying an XML Document</span></span>  
 <span data-ttu-id="15d32-105">XML プログラマにとって最も一般的なタスクの&1; つが、XML の形式の変換です。</span><span class="sxs-lookup"><span data-stu-id="15d32-105">One of the most common tasks for an XML programmer is transforming XML from one shape to another.</span></span> <span data-ttu-id="15d32-106">XML ドキュメントの形式とはドキュメントの構造のことで、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="15d32-106">The shape of an XML document is the structure of the document, which includes the following:</span></span>  
  
-   <span data-ttu-id="15d32-107">ドキュメントによって表される階層。</span><span class="sxs-lookup"><span data-stu-id="15d32-107">The hierarchy expressed by the document.</span></span>  
  
-   <span data-ttu-id="15d32-108">要素名および属性名。</span><span class="sxs-lookup"><span data-stu-id="15d32-108">The element and attribute names.</span></span>  
  
-   <span data-ttu-id="15d32-109">要素と属性のデータ型。</span><span class="sxs-lookup"><span data-stu-id="15d32-109">The data types of the elements and attributes.</span></span>  
  
 <span data-ttu-id="15d32-110">一般に、XML の形式を変換するために最も効果的なのは、純粋関数型変換の方法です。</span><span class="sxs-lookup"><span data-stu-id="15d32-110">In general, the most effective approach to transforming XML from one shape to another is that of pure functional transformation.</span></span> <span data-ttu-id="15d32-111">この方法におけるプログラマの主なタスクは、XML ドキュメント全体 (または&1; つ以上の厳密に定義されたノード) に適用する変換を作成することです。</span><span class="sxs-lookup"><span data-stu-id="15d32-111">In this approach, the primary programmer task is to create a transformation which is applied to the entire XML document (or to one or more strictly defined nodes).</span></span> <span data-ttu-id="15d32-112">関数型変換は、(プログラマがこの方法をいったん理解すれば) コードの記述が最も簡単で、最も保守しやすいコードが得られ、多くの場合、その他の方法よりもコンパクトです。</span><span class="sxs-lookup"><span data-stu-id="15d32-112">Functional transformation is arguably the easiest to code (after a programmer is familiar with the approach), yields the most maintainable code, and is often more compact than alternative approaches.</span></span>  
  
### <a name="xml-functional-transformational-technologies"></a><span data-ttu-id="15d32-113">XML の関数型変換のテクノロジ</span><span class="sxs-lookup"><span data-stu-id="15d32-113">XML Functional Transformational Technologies</span></span>  
 <span data-ttu-id="15d32-114">Microsoft では、XML ドキュメントで使用する関数型変換のテクノロジを&2; つ用意しています。それらは、XSLT と LINQ to XML です。</span><span class="sxs-lookup"><span data-stu-id="15d32-114">Microsoft offers two functional transformation technologies for use on XML documents: XSLT and LINQ to XML.</span></span> <span data-ttu-id="15d32-115">XSLT には、<xref:System.Xml.Xsl>マネージ名前空間と MSXML のネイティブ COM 実装</xref:System.Xml.Xsl>。</span><span class="sxs-lookup"><span data-stu-id="15d32-115">XSLT is supported in the <xref:System.Xml.Xsl> managed namespace and in the native COM implementation of MSXML.</span></span> <span data-ttu-id="15d32-116">XSLT は XML ドキュメントを操作するための堅牢なテクノロジですが、XSLT 言語とそれに対応する API に関する専門知識を必要とします。</span><span class="sxs-lookup"><span data-stu-id="15d32-116">Although XSLT is a robust technology for manipulating XML documents, it requires expertise in a specialized domain, namely the XSLT language and its supporting APIs.</span></span>  
  
 <span data-ttu-id="15d32-117">LINQ to XML には、純粋関数型変換のコードを C# または Visual Basic のコード内にさまざまな表現で効果的に記述できるツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="15d32-117">LINQ to XML provides the tools necessary to code pure functional transformations in an expressive and powerful way, within C# or Visual Basic code.</span></span> <span data-ttu-id="15d32-118">たとえば、LINQ to XML のドキュメントに記載されている多くの例で、純粋関数型の方法が使用されています。</span><span class="sxs-lookup"><span data-stu-id="15d32-118">For example, many of the examples in the LINQ to XML documentation use a pure functional approach.</span></span> <span data-ttu-id="15d32-119">また、[チュートリアル: WordprocessingML ドキュメント (Visual Basic の場合) 内のコンテンツを操作する](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)チュートリアルでは、使用して LINQ to XML 関数型の方法で Microsoft Word ドキュメント内の情報を操作します。</span><span class="sxs-lookup"><span data-stu-id="15d32-119">Also, in the [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial, we use LINQ to XML in a functional approach to manipulate information in a Microsoft Word document.</span></span>  
  
 <span data-ttu-id="15d32-120">詳細な比較では LINQ to XML の他の Microsoft XML テクノロジと、次を参照してください。 [LINQ to XML およびです。他の XML テクノロジ](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)します。</span><span class="sxs-lookup"><span data-stu-id="15d32-120">For a more complete comparison of LINQ to XML with other Microsoft XML technologies, see [LINQ to XML vs. Other XML Technologies](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md).</span></span>  
  
 <span data-ttu-id="15d32-121">ソース ドキュメントの構造が標準的でない場合、ドキュメント中心の変換には XSLT を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="15d32-121">XSLT is the recommended tool for  document-centric transformations when the source document has an irregular structure.</span></span> <span data-ttu-id="15d32-122">ただし、LINQ to XML でもドキュメント中心の変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="15d32-122">However, LINQ to XML can also perform document-centric transforms.</span></span> <span data-ttu-id="15d32-123">詳細については、次を参照してください。[方法: LINQ to XML ツリーを XSLT スタイル (Visual Basic) に変換する注釈が使用](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md)します。</span><span class="sxs-lookup"><span data-stu-id="15d32-123">For more information, see [How to: Use Annotations to Transform LINQ to XML Trees in an XSLT Style (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-use-annotation-trees-to-transform-linq-to-xml-trees-in-an-xslt-style.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15d32-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="15d32-124">See Also</span></span>  
 <span data-ttu-id="15d32-125">[純粋関数型変換 (Visual Basic) の概要](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="15d32-125">[Introduction to Pure Functional Transformations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
<span data-ttu-id="15d32-126"> [LINQ to XML と他の XML テクノロジ](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md) </span><span class="sxs-lookup"><span data-stu-id="15d32-126"> [LINQ to XML vs. Other XML Technologies](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md) </span></span>  
<span data-ttu-id="15d32-127"> [LINQ to XML とその他の XML テクノロジ](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)</span><span class="sxs-lookup"><span data-stu-id="15d32-127"> [LINQ to XML vs. Other XML Technologies](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)</span></span>
