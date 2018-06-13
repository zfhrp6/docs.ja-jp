---
title: '方法 : XML リテラルを作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e5f8429b3ff02678bf8bf3e9e32bef6eb1a56831
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652871"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="1e5a4-102">方法 : XML リテラルを作成する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e5a4-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="1e5a4-103">XML リテラルを使用して、XML ドキュメント、フラグメント、または要素をコード内で直接作成できます。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="1e5a4-104">このトピックの例では、次の 3 つの子要素を持つ XML 要素を作成する方法と、XML ドキュメントを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="1e5a4-105">使用することも、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]を作成するための Api[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="1e5a4-106">詳細については、「<xref:System.Xml.Linq.XElement>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="1e5a4-107">XML 要素を作成するには</span><span class="sxs-lookup"><span data-stu-id="1e5a4-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="1e5a4-108">XML インラインを作成するには、実際の XML 構文と同じでは、XML リテラル構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="1e5a4-109">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-109">Run the code.</span></span> <span data-ttu-id="1e5a4-110">このコードの出力です。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="1e5a4-111">XML ドキュメントを作成するには</span><span class="sxs-lookup"><span data-stu-id="1e5a4-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="1e5a4-112">XML ドキュメントを 1 列を作成します。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-112">Create the XML document inline.</span></span> <span data-ttu-id="1e5a4-113">次のコードでは、リテラルの構文、XML 宣言、処理命令、コメント、および別の要素を格納する要素のある XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="1e5a4-114">コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-114">Run the code.</span></span> <span data-ttu-id="1e5a4-115">このコードの出力です。</span><span class="sxs-lookup"><span data-stu-id="1e5a4-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="1e5a4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e5a4-116">See Also</span></span>  
 [<span data-ttu-id="1e5a4-117">XML</span><span class="sxs-lookup"><span data-stu-id="1e5a4-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="1e5a4-118">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="1e5a4-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="1e5a4-119">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="1e5a4-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="1e5a4-120">XML ドキュメント リテラル</span><span class="sxs-lookup"><span data-stu-id="1e5a4-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
