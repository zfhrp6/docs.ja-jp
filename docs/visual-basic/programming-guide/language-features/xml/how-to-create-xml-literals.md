---
title: '方法 : XML リテラルを作成する (Visual Basic)'
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
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce1bf763529b436158c2d74811c4938182166f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="15dcc-102">方法 : XML リテラルを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15dcc-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="15dcc-103">XML リテラルを使用して、XML ドキュメント、フラグメント、または要素をコード内で直接作成できます。</span><span class="sxs-lookup"><span data-stu-id="15dcc-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="15dcc-104">このトピックの例では、次の 3 つの子要素を持つ XML 要素を作成する方法と、XML ドキュメントを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="15dcc-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="15dcc-105">使用することも、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]を作成するための Api[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="15dcc-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="15dcc-106">詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15dcc-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="15dcc-107">XML 要素を作成するには</span><span class="sxs-lookup"><span data-stu-id="15dcc-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="15dcc-108">XML インラインを作成するには、実際の XML 構文と同じでは、XML リテラル構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="15dcc-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="15dcc-109">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="15dcc-109">Run the code.</span></span> <span data-ttu-id="15dcc-110">このコードの出力です。</span><span class="sxs-lookup"><span data-stu-id="15dcc-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="15dcc-111">XML ドキュメントを作成するには</span><span class="sxs-lookup"><span data-stu-id="15dcc-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="15dcc-112">XML ドキュメントを 1 列を作成します。</span><span class="sxs-lookup"><span data-stu-id="15dcc-112">Create the XML document inline.</span></span> <span data-ttu-id="15dcc-113">次のコードでは、リテラルの構文、XML 宣言、処理命令、コメント、および別の要素を格納する要素のある XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="15dcc-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="15dcc-114">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="15dcc-114">Run the code.</span></span> <span data-ttu-id="15dcc-115">このコードの出力です。</span><span class="sxs-lookup"><span data-stu-id="15dcc-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="15dcc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="15dcc-116">See Also</span></span>  
 [<span data-ttu-id="15dcc-117">XML</span><span class="sxs-lookup"><span data-stu-id="15dcc-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="15dcc-118">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="15dcc-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="15dcc-119">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="15dcc-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="15dcc-120">XML ドキュメント リテラル</span><span class="sxs-lookup"><span data-stu-id="15dcc-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
