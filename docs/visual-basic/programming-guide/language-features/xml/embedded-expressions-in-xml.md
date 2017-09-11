---
title: "XML (Visual Basic) での埋め込み式 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
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
ms.openlocfilehash: d24a49f2fa6fd66fe6e4c7724bd4298d65fb7a59
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="3e40b-102">XML での埋め込み式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e40b-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="3e40b-103">組み込み式を使用すると、実行時に評価される式が含まれる XML リテラルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3e40b-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="3e40b-104">埋め込み式の構文は`<%=` `expression` `%>`で使用するための構文は同じ[!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]します。</span><span class="sxs-lookup"><span data-stu-id="3e40b-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)].</span></span>  
  
 <span data-ttu-id="3e40b-105">などを作成する XML 要素リテラル、埋め込み式のリテラル テキストの内容とを組み合わせることです。</span><span class="sxs-lookup"><span data-stu-id="3e40b-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 <span data-ttu-id="3e40b-106">[!code-vb[VbXMLSamples #&27;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3e40b-106">[!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]</span></span>  
  
 <span data-ttu-id="3e40b-107">場合`isbnNumber`12345 整数が含まれると`modifiedDate`日付を含む 3/5/2006 を実行すると次のコードの値`book`は。</span><span class="sxs-lookup"><span data-stu-id="3e40b-107">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="3e40b-108">埋め込み式の位置と検証</span><span class="sxs-lookup"><span data-stu-id="3e40b-108">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="3e40b-109">埋め込み式は、XML リテラル式の中で特定の場所にしか表示されないことができます。</span><span class="sxs-lookup"><span data-stu-id="3e40b-109">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="3e40b-110">式の型を式の場所のコントロールを返すことができ、どのように`Nothing`処理されます。</span><span class="sxs-lookup"><span data-stu-id="3e40b-110">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="3e40b-111">次の表は、許可されている場所と組み込み式の種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e40b-111">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="3e40b-112">リテラル内の場所</span><span class="sxs-lookup"><span data-stu-id="3e40b-112">Location in literal</span></span>|<span data-ttu-id="3e40b-113">式の型</span><span class="sxs-lookup"><span data-stu-id="3e40b-113">Type of expression</span></span>|<span data-ttu-id="3e40b-114">処理`Nothing`</span><span class="sxs-lookup"><span data-stu-id="3e40b-114">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="3e40b-115">XML 要素名</span><span class="sxs-lookup"><span data-stu-id="3e40b-115">XML element name</span></span>|<span data-ttu-id="3e40b-116"><xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="3e40b-116"><xref:System.Xml.Linq.XName></span></span>|<span data-ttu-id="3e40b-117">Error</span><span class="sxs-lookup"><span data-stu-id="3e40b-117">Error</span></span>|  
|<span data-ttu-id="3e40b-118">XML 要素の内容</span><span class="sxs-lookup"><span data-stu-id="3e40b-118">XML element content</span></span>|<span data-ttu-id="3e40b-119">`Object`またはの配列`Object`</span><span class="sxs-lookup"><span data-stu-id="3e40b-119">`Object` or array of `Object`</span></span>|<span data-ttu-id="3e40b-120">無視</span><span class="sxs-lookup"><span data-stu-id="3e40b-120">Ignored</span></span>|  
|<span data-ttu-id="3e40b-121">XML 要素の属性名</span><span class="sxs-lookup"><span data-stu-id="3e40b-121">XML element attribute name</span></span>|<span data-ttu-id="3e40b-122"><xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="3e40b-122"><xref:System.Xml.Linq.XName></span></span>|<span data-ttu-id="3e40b-123">エラー、属性値もしない限り、`Nothing`</span><span class="sxs-lookup"><span data-stu-id="3e40b-123">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="3e40b-124">XML 要素の属性値</span><span class="sxs-lookup"><span data-stu-id="3e40b-124">XML element attribute value</span></span>|`Object`|<span data-ttu-id="3e40b-125">属性宣言は無視されます。</span><span class="sxs-lookup"><span data-stu-id="3e40b-125">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="3e40b-126">XML 要素の属性</span><span class="sxs-lookup"><span data-stu-id="3e40b-126">XML element attribute</span></span>|<span data-ttu-id="3e40b-127"><xref:System.Xml.Linq.XAttribute>またはのコレクション<xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="3e40b-127"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="3e40b-128">無視</span><span class="sxs-lookup"><span data-stu-id="3e40b-128">Ignored</span></span>|  
|<span data-ttu-id="3e40b-129">XML ドキュメントのルート要素</span><span class="sxs-lookup"><span data-stu-id="3e40b-129">XML document root element</span></span>|<span data-ttu-id="3e40b-130"><xref:System.Xml.Linq.XElement>またはの&1; つの<xref:System.Xml.Linq.XElement>オブジェクトと任意の数<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XProcessingInstruction>の</xref:System.Xml.Linq.XElement>コレクション</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="3e40b-130"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="3e40b-131">無視</span><span class="sxs-lookup"><span data-stu-id="3e40b-131">Ignored</span></span>|  
  
-   <span data-ttu-id="3e40b-132">XML 要素名での埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="3e40b-132">Example of an embedded expression in an XML element name:</span></span>  
  
     <span data-ttu-id="3e40b-133">[!code-vb[VbXMLSamples&#32;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="3e40b-133">[!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]</span></span>  
  
-   <span data-ttu-id="3e40b-134">XML 要素のコンテンツ内の埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="3e40b-134">Example of an embedded expression in the content of an XML element:</span></span>  
  
     <span data-ttu-id="3e40b-135">[!code-vb[VbXMLSamples #&33;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="3e40b-135">[!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]</span></span>  
  
-   <span data-ttu-id="3e40b-136">XML 要素の属性名での埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="3e40b-136">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     <span data-ttu-id="3e40b-137">[!code-vb[VbXMLSamples #&34;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="3e40b-137">[!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]</span></span>  
  
-   <span data-ttu-id="3e40b-138">XML 要素の属性値内の埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="3e40b-138">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     <span data-ttu-id="3e40b-139">[!code-vb[VbXMLSamples&#35;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="3e40b-139">[!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]</span></span>  
  
-   <span data-ttu-id="3e40b-140">XML 要素の属性での埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="3e40b-140">Example of an embedded expression in an XML element attribute:</span></span>  
  
     <span data-ttu-id="3e40b-141">[!code-vb[VbXMLSamples&#36;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="3e40b-141">[!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]</span></span>  
  
-   <span data-ttu-id="3e40b-142">XML ドキュメントのルート要素での埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="3e40b-142">Example of an embedded expression in an XML document root element:</span></span>  
  
     <span data-ttu-id="3e40b-143">[!code-vb[VbXMLSamples #&37;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="3e40b-143">[!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]</span></span>  
  
 <span data-ttu-id="3e40b-144">有効にした場合`Option Strict`コンパイラは各埋め込み式の型が必要な型に拡大変換ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3e40b-144">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="3e40b-145">コードの実行時に検証される XML ドキュメントのルート要素は唯一の例外です。</span><span class="sxs-lookup"><span data-stu-id="3e40b-145">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="3e40b-146">せずにコンパイルする場合`Option Strict`、型の式を埋め込むことができます`Object`でその型が実行時に確認します。</span><span class="sxs-lookup"><span data-stu-id="3e40b-146">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="3e40b-147">コンテンツが、省略可能な場所で埋め込み式を含む`Nothing`は無視されます。</span><span class="sxs-lookup"><span data-stu-id="3e40b-147">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="3e40b-148">つまり、その要素の内容の属性の値を確認する必要はありませんし、配列の要素ではありません`Nothing`XML リテラルを使用する前にします。</span><span class="sxs-lookup"><span data-stu-id="3e40b-148">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="3e40b-149">要素と属性名などの値ができないために必要な`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="3e40b-149">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="3e40b-150">リテラルの特定の種類で、組み込み式を使用する方法の詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)、 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="3e40b-150">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="3e40b-151">スコープの規則</span><span class="sxs-lookup"><span data-stu-id="3e40b-151">Scoping Rules</span></span>  
 <span data-ttu-id="3e40b-152">コンパイラは、各 XML リテラルを適切なリテラルの型のコンス トラクターの呼び出しに変換します。</span><span class="sxs-lookup"><span data-stu-id="3e40b-152">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="3e40b-153">XML リテラルでの埋め込み式とリテラルの内容は、コンス トラクターを引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="3e40b-153">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="3e40b-154">つまり、このすべて[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]XML リテラルで使用できるプログラミングの要素も、埋め込み式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3e40b-154">This means that all [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="3e40b-155">XML リテラル内では、XML 名前空間で宣言されたプレフィックスをアクセスできる、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="3e40b-155">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="3e40b-156">新しい XML 名前空間プレフィックスを宣言するかを使用して要素に、既存 XML 名前空間プレフィックスをシャドウ、`xmlns`属性です。</span><span class="sxs-lookup"><span data-stu-id="3e40b-156">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="3e40b-157">新しい名前空間は、組み込み式内の XML リテラルではなく、その要素の子ノードに使用可能なです。</span><span class="sxs-lookup"><span data-stu-id="3e40b-157">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e40b-158">使用して XML 名前空間プレフィックスを宣言する場合、`xmlns`名前空間の属性、属性値は定数文字列を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3e40b-158">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="3e40b-159">この点を使用して、`xmlns`属性は、使用するように、 `Imports` XML 名前空間を宣言するステートメントです。</span><span class="sxs-lookup"><span data-stu-id="3e40b-159">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="3e40b-160">組み込み式を使用して、XML 名前空間の値を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3e40b-160">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e40b-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e40b-161">See Also</span></span>  
 <span data-ttu-id="3e40b-162">[Visual Basic で XML を作成します。](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="3e40b-162">[Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="3e40b-163"> [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span><span class="sxs-lookup"><span data-stu-id="3e40b-163"> [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span></span>  
<span data-ttu-id="3e40b-164"> [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="3e40b-164"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="3e40b-165"> [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3e40b-165"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="3e40b-166"> [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="3e40b-166"> [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="3e40b-167"> [XML リテラルの概要](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)</span><span class="sxs-lookup"><span data-stu-id="3e40b-167"> [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)</span></span>
