---
title: "XML での埋め込み式 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1cdba0a39a932f143ac98c2514240e1696a8fe0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="embedded-expressions-in-xml-visual-basic"></a><span data-ttu-id="ca0a4-102">XML での埋め込み式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca0a4-102">Embedded Expressions in XML (Visual Basic)</span></span>
<span data-ttu-id="ca0a4-103">埋め込み式を使用すると、実行時に評価される式が含まれる XML リテラルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-103">Embedded expressions enable you to create XML literals that contain expressions that are evaluated at run time.</span></span> <span data-ttu-id="ca0a4-104">埋め込み式の構文は、 `<%=` `expression` `%>`で使用される構文と同じであるが[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-104">The syntax for an embedded expression is `<%=` `expression` `%>`, which is the same as the syntax used in [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="ca0a4-105">たとえば、作成 XML 要素リテラル、リテラル テキストの内容を含む埋め込み式を組み合わせることです。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-105">For example, you can create an XML element literal, combining embedded expressions with literal text content.</span></span>  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 <span data-ttu-id="ca0a4-106">場合`isbnNumber`12345 整数が含まれると`modifiedDate`日付を含む 3/5/2006、ときにこのコードの実行の値`book`は。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-106">If `isbnNumber` contains the integer 12345 and `modifiedDate` contains the date 3/5/2006, when this code executes, the value of `book` is:</span></span>  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a><span data-ttu-id="ca0a4-107">埋め込み式の位置と検証</span><span class="sxs-lookup"><span data-stu-id="ca0a4-107">Embedded Expression Location and Validation</span></span>  
 <span data-ttu-id="ca0a4-108">埋め込み式は、XML リテラル式内で特定の場所にしか表示されないことができます。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-108">Embedded expressions can appear only at certain locations within XML literal expressions.</span></span> <span data-ttu-id="ca0a4-109">式の型を式の場所のコントロールを返すことができます、どのように`Nothing`処理されます。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-109">The expression location controls which types the expression can return and how `Nothing` is handled.</span></span> <span data-ttu-id="ca0a4-110">次の表は、許可されている場所と埋め込み式の型について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-110">The following table describes the allowed locations and types of embedded expressions.</span></span>  
  
|<span data-ttu-id="ca0a4-111">リテラル内の場所</span><span class="sxs-lookup"><span data-stu-id="ca0a4-111">Location in literal</span></span>|<span data-ttu-id="ca0a4-112">式の型</span><span class="sxs-lookup"><span data-stu-id="ca0a4-112">Type of expression</span></span>|<span data-ttu-id="ca0a4-113">処理`Nothing`</span><span class="sxs-lookup"><span data-stu-id="ca0a4-113">Handling of `Nothing`</span></span>|  
|---|---|---|  
|<span data-ttu-id="ca0a4-114">XML 要素名</span><span class="sxs-lookup"><span data-stu-id="ca0a4-114">XML element name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="ca0a4-115">エラー</span><span class="sxs-lookup"><span data-stu-id="ca0a4-115">Error</span></span>|  
|<span data-ttu-id="ca0a4-116">XML 要素のコンテンツ</span><span class="sxs-lookup"><span data-stu-id="ca0a4-116">XML element content</span></span>|<span data-ttu-id="ca0a4-117">`Object`またはの配列`Object`</span><span class="sxs-lookup"><span data-stu-id="ca0a4-117">`Object` or array of `Object`</span></span>|<span data-ttu-id="ca0a4-118">無視</span><span class="sxs-lookup"><span data-stu-id="ca0a4-118">Ignored</span></span>|  
|<span data-ttu-id="ca0a4-119">XML 要素の属性名</span><span class="sxs-lookup"><span data-stu-id="ca0a4-119">XML element attribute name</span></span>|<xref:System.Xml.Linq.XName>|<span data-ttu-id="ca0a4-120">エラー、属性値もしない限り、`Nothing`</span><span class="sxs-lookup"><span data-stu-id="ca0a4-120">Error, unless the attribute value is also `Nothing`</span></span>|  
|<span data-ttu-id="ca0a4-121">XML 要素の属性値</span><span class="sxs-lookup"><span data-stu-id="ca0a4-121">XML element attribute value</span></span>|`Object`|<span data-ttu-id="ca0a4-122">属性宣言は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-122">Attribute declaration ignored</span></span>|  
|<span data-ttu-id="ca0a4-123">XML 要素の属性</span><span class="sxs-lookup"><span data-stu-id="ca0a4-123">XML element attribute</span></span>|<span data-ttu-id="ca0a4-124"><xref:System.Xml.Linq.XAttribute>またはのコレクション<xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="ca0a4-124"><xref:System.Xml.Linq.XAttribute> or a collection of <xref:System.Xml.Linq.XAttribute></span></span>|<span data-ttu-id="ca0a4-125">無視</span><span class="sxs-lookup"><span data-stu-id="ca0a4-125">Ignored</span></span>|  
|<span data-ttu-id="ca0a4-126">XML ドキュメントのルート要素</span><span class="sxs-lookup"><span data-stu-id="ca0a4-126">XML document root element</span></span>|<span data-ttu-id="ca0a4-127"><xref:System.Xml.Linq.XElement>1 つのコレクションまたは<xref:System.Xml.Linq.XElement>オブジェクトと任意の数の<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト</span><span class="sxs-lookup"><span data-stu-id="ca0a4-127"><xref:System.Xml.Linq.XElement> or a collection of one <xref:System.Xml.Linq.XElement> object and an arbitrary number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects</span></span>|<span data-ttu-id="ca0a4-128">無視</span><span class="sxs-lookup"><span data-stu-id="ca0a4-128">Ignored</span></span>|  
  
-   <span data-ttu-id="ca0a4-129">XML 要素の名前の埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="ca0a4-129">Example of an embedded expression in an XML element name:</span></span>  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   <span data-ttu-id="ca0a4-130">XML 要素のコンテンツの埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="ca0a4-130">Example of an embedded expression in the content of an XML element:</span></span>  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   <span data-ttu-id="ca0a4-131">XML 要素属性の名前の埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="ca0a4-131">Example of an embedded expression in an XML element attribute name:</span></span>  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   <span data-ttu-id="ca0a4-132">XML 要素の属性値内の埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="ca0a4-132">Example of an embedded expression in an XML element attribute value:</span></span>  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   <span data-ttu-id="ca0a4-133">XML 要素の属性の埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="ca0a4-133">Example of an embedded expression in an XML element attribute:</span></span>  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   <span data-ttu-id="ca0a4-134">XML ドキュメントのルート要素の埋め込み式の例:</span><span class="sxs-lookup"><span data-stu-id="ca0a4-134">Example of an embedded expression in an XML document root element:</span></span>  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 <span data-ttu-id="ca0a4-135">有効にした場合`Option Strict`コンパイラは各埋め込み式の型が必要な型に拡大変換ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-135">If you enable `Option Strict`, the compiler checks that the type of each embedded expression widens to the required type.</span></span> <span data-ttu-id="ca0a4-136">唯一の例外では、コードの実行時に検証される XML ドキュメントのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-136">The only exception is for the root element of an XML document, which is verified when the code runs.</span></span> <span data-ttu-id="ca0a4-137">せずにコンパイルする場合`Option Strict`、型の式を埋め込むことができます`Object`およびそれらの種類の実行時に確認します。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-137">If you compile without `Option Strict`, you can embed expressions of type `Object` and their type is verified at run time.</span></span>  
  
 <span data-ttu-id="ca0a4-138">コンテンツが、省略可能な場所で埋め込み式を含む`Nothing`は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-138">In locations where content is optional, embedded expressions that contain `Nothing` are ignored.</span></span> <span data-ttu-id="ca0a4-139">つまり、その要素のコンテンツの属性値を確認する必要はありませんし、配列要素ではありません`Nothing`XML リテラルを使用する前にします。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-139">This means you do not have to check that element content, attribute values, and array elements are not `Nothing` before you use an XML literal.</span></span> <span data-ttu-id="ca0a4-140">必要な要素と属性の名などの値にすることはできません`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-140">Required values, such as element and attribute names, cannot be `Nothing`.</span></span>  
  
 <span data-ttu-id="ca0a4-141">詳細については、リテラルの特定の型の埋め込み式を使用して、次を参照してください。 [XML ドキュメント リテラル](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)、 [XML 要素リテラル](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-141">For more information about using an embedded expression in a particular type of literal, see [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span>  
  
## <a name="scoping-rules"></a><span data-ttu-id="ca0a4-142">スコープの規則</span><span class="sxs-lookup"><span data-stu-id="ca0a4-142">Scoping Rules</span></span>  
 <span data-ttu-id="ca0a4-143">コンパイラは、各 XML リテラルを適切なリテラルの型のコンス トラクターの呼び出しに変換します。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-143">The compiler converts each XML literal into a constructor call for the appropriate literal type.</span></span> <span data-ttu-id="ca0a4-144">XML リテラルでの埋め込み式とリテラルの内容は、コンス トラクターに引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-144">The literal content and embedded expressions in an XML literal are passed as arguments to the constructor.</span></span> <span data-ttu-id="ca0a4-145">つまり、すべて[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]XML リテラルに利用できるプログラミング要素も、埋め込み式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-145">This means that all [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming elements available to an XML literal are also available to its embedded expressions.</span></span>  
  
 <span data-ttu-id="ca0a4-146">XML リテラル内でプレフィックスが宣言された XML 名前空間にアクセスすることができます、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-146">Within an XML literal, you can access the XML namespace prefixes declared with the `Imports` statement.</span></span> <span data-ttu-id="ca0a4-147">新しい XML 名前空間プレフィックスを宣言または要素を使用して、既存 XML 名前空間プレフィックスをシャドウすることができます、`xmlns`属性。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-147">You can declare a new XML namespace prefix, or shadow an existing XML namespace prefix, in an element by using the `xmlns` attribute.</span></span> <span data-ttu-id="ca0a4-148">新しい名前空間は、組み込み式内の XML リテラルではなく、その要素の子ノードに使用可能なです。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-148">The new namespace is available to the child nodes of that element, but not to XML literals in embedded expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca0a4-149">使用して XML 名前空間プレフィックスを宣言する場合、`xmlns`名前空間の属性、属性値が文字列定数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-149">When you declare an XML namespace prefix by using the `xmlns` namespace attribute, the attribute value must be a constant string.</span></span> <span data-ttu-id="ca0a4-150">この点を使用して、`xmlns`属性は、使用するように、 `Imports` XML 名前空間を宣言するステートメント。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-150">In this regard, using the `xmlns` attribute is like using the `Imports` statement to declare an XML namespace.</span></span> <span data-ttu-id="ca0a4-151">埋め込み式を使用して、XML 名前空間の値を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="ca0a4-151">You cannot use an embedded expression to specify the XML namespace value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca0a4-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca0a4-152">See Also</span></span>  
 [<span data-ttu-id="ca0a4-153">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="ca0a4-153">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="ca0a4-154">XML ドキュメント リテラル</span><span class="sxs-lookup"><span data-stu-id="ca0a4-154">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="ca0a4-155">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="ca0a4-155">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="ca0a4-156">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="ca0a4-156">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="ca0a4-157">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="ca0a4-157">Imports Statement (.NET Namespace and Type)</span></span>](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="ca0a4-158">XML リテラルの概要</span><span class="sxs-lookup"><span data-stu-id="ca0a4-158">XML Literals Overview</span></span>](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
