---
title: "方法: XML リテラル (Visual Basic) を作成する |Microsoft ドキュメント"
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
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 17
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
ms.openlocfilehash: 3a7b5dc692317067290b48222ba056d765a449f3
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="e9b33-102">方法 : XML リテラルを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9b33-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="e9b33-103">XML リテラルを使用して、XML ドキュメント、フラグメント、または要素をコード内で直接作成できます。</span><span class="sxs-lookup"><span data-stu-id="e9b33-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="e9b33-104">このトピックの例では、次の&3; つの子要素を持つ XML 要素を作成する方法と、XML ドキュメントを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e9b33-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="e9b33-105">使用することも、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]を作成する Api[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e9b33-105">You can also use the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs to create [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects.</span></span> <span data-ttu-id="e9b33-106">詳細については、 <xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9b33-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="e9b33-107">XML 要素を作成するには</span><span class="sxs-lookup"><span data-stu-id="e9b33-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="e9b33-108">XML インラインを作成するには、実際の XML 構文と同じでは、XML リテラル構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="e9b33-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     <span data-ttu-id="e9b33-109">[!code-vb[VbXMLSamples&#5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e9b33-109">[!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="e9b33-110">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9b33-110">Run the code.</span></span> <span data-ttu-id="e9b33-111">このコードの出力です。</span><span class="sxs-lookup"><span data-stu-id="e9b33-111">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="e9b33-112">XML ドキュメントを作成するには</span><span class="sxs-lookup"><span data-stu-id="e9b33-112">To create an XML document</span></span>  
  
-   <span data-ttu-id="e9b33-113">XML ドキュメントを&1; 列を作成します。</span><span class="sxs-lookup"><span data-stu-id="e9b33-113">Create the XML document inline.</span></span> <span data-ttu-id="e9b33-114">次のコードでは、リテラルの構文、XML 宣言、処理命令、コメント、および別の要素を含む要素には、XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="e9b33-114">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     <span data-ttu-id="e9b33-115">[!code-vb[VbXMLSamples #&30;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e9b33-115">[!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="e9b33-116">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="e9b33-116">Run the code.</span></span> <span data-ttu-id="e9b33-117">このコードの出力です。</span><span class="sxs-lookup"><span data-stu-id="e9b33-117">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="e9b33-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9b33-118">See Also</span></span>  
 <span data-ttu-id="e9b33-119">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="e9b33-119">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="e9b33-120"> [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="e9b33-120"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="e9b33-121"> [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="e9b33-121"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="e9b33-122"> [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)</span><span class="sxs-lookup"><span data-stu-id="e9b33-122"> [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)</span></span>
