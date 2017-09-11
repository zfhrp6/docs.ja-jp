---
title: "方法: XML リテラル (Visual Basic) に式を埋め込む |Microsoft ドキュメント"
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
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
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
ms.openlocfilehash: e4f086b06575cb8300bd65d450cda6b9893bb692
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="a170c-102">方法: XML リテラルに式を埋め込む (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a170c-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="a170c-103">組み込み式を XML ドキュメント、フラグメント、または実行時に作成されたコンテンツを格納する要素を作成するには、XML リテラルを組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="a170c-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="a170c-104">次の例では、組み込み式を使用して、実行時に要素の内容、属性、および要素名を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a170c-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="a170c-105">埋め込み式の構文は`<%=` `exp` `%>`、これは、同じ構文を[!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]を使用します。</span><span class="sxs-lookup"><span data-stu-id="a170c-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] uses.</span></span> <span data-ttu-id="a170c-106">詳細については、次を参照してください。 [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="a170c-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="a170c-107">使用することも、[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]を作成する Api[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a170c-107">You can also use the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs to create [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects.</span></span> <span data-ttu-id="a170c-108">詳細については、 <xref:System.Xml.Linq.XElement>。</xref:System.Xml.Linq.XElement>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a170c-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="a170c-109">手順</span><span class="sxs-lookup"><span data-stu-id="a170c-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="a170c-110">要素の内容としてテキストを挿入するには</span><span class="sxs-lookup"><span data-stu-id="a170c-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="a170c-111">次の例に含まれているテキストを挿入する方法を示しています、`contactName`変数名の開始と終了の要素の間です。</span><span class="sxs-lookup"><span data-stu-id="a170c-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     <span data-ttu-id="a170c-112">[!code-vb[VbXMLSamples&#39;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a170c-112">[!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="a170c-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a170c-113">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="a170c-114">属性値としてテキストを挿入するには</span><span class="sxs-lookup"><span data-stu-id="a170c-114">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="a170c-115">次の例に含まれているテキストを挿入する方法を示しています、`phoneType`変数の値として、`type`属性です。</span><span class="sxs-lookup"><span data-stu-id="a170c-115">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     <span data-ttu-id="a170c-116">[!code-vb[VbXMLSamples #&40;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a170c-116">[!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="a170c-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a170c-117">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="a170c-118">要素名のテキストを挿入するには</span><span class="sxs-lookup"><span data-stu-id="a170c-118">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="a170c-119">次の例に含まれているテキストを挿入する方法を示しています、`elementName`変数としての要素の名前。</span><span class="sxs-lookup"><span data-stu-id="a170c-119">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="a170c-120">をこの方法を使用して要素を作成するときに、それらを閉じる必要があります、 \</> タグ。</span><span class="sxs-lookup"><span data-stu-id="a170c-120">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     <span data-ttu-id="a170c-121">[!code-vb[VbXMLSamples #&41;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a170c-121">[!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]</span></span>  
  
     <span data-ttu-id="a170c-122">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a170c-122">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a170c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a170c-123">See Also</span></span>  
 <span data-ttu-id="a170c-124">[方法: XML リテラルを作成します。](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md) </span><span class="sxs-lookup"><span data-stu-id="a170c-124">[How to: Create XML Literals](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md) </span></span>  
<span data-ttu-id="a170c-125"> [XML での埋め込み式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a170c-125"> [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="a170c-126"> [Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="a170c-126"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="a170c-127"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="a170c-127"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
