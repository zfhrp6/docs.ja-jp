---
title: "XML 要素リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralElement
dev_langs:
- VB
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: 32
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
ms.openlocfilehash: d5cf769a1e3f668652d1eb4551058deba38a8acf
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xml-element-literal-visual-basic"></a><span data-ttu-id="1ffb0-102">XML 要素リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ffb0-102">XML Element Literal (Visual Basic)</span></span>
<span data-ttu-id="1ffb0-103">表すリテラル、<xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-103">A literal that represents an <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffb0-104">構文</span><span class="sxs-lookup"><span data-stu-id="1ffb0-104">Syntax</span></span>  
  
```  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a><span data-ttu-id="1ffb0-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="1ffb0-105">Parts</span></span>  
  
-   `<`  
  
     <span data-ttu-id="1ffb0-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-106">Required.</span></span> <span data-ttu-id="1ffb0-107">要素の開始タグを開きます。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-107">Opens the starting element tag.</span></span>  
  
-   `name`  
  
     <span data-ttu-id="1ffb0-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-108">Required.</span></span> <span data-ttu-id="1ffb0-109">要素名</span><span class="sxs-lookup"><span data-stu-id="1ffb0-109">Name of the element.</span></span> <span data-ttu-id="1ffb0-110">形式は、次のいずれかを示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-110">The format is one of the following:</span></span>  
  
    -   <span data-ttu-id="1ffb0-111">リテラル テキストの形式の要素名を [`ePrefix``:`]`eName`、場所。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-111">Literal text for the element name, of the form [`ePrefix``:`]`eName`, where:</span></span>  
  
        |<span data-ttu-id="1ffb0-112">パーツ</span><span class="sxs-lookup"><span data-stu-id="1ffb0-112">Part</span></span>|<span data-ttu-id="1ffb0-113">説明</span><span class="sxs-lookup"><span data-stu-id="1ffb0-113">Description</span></span>|  
        |---|---|  
        |`ePrefix`|<span data-ttu-id="1ffb0-114">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-114">Optional.</span></span> <span data-ttu-id="1ffb0-115">要素の XML 名前空間プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-115">XML namespace prefix for the element.</span></span> <span data-ttu-id="1ffb0-116">グローバル XML 名前空間で定義されている必要があります、`Imports`ステートメント、ファイルまたはプロジェクト レベルまたはこの要素または親要素で定義されているローカル XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-116">Must be a global XML namespace that is defined with an `Imports` statement in the file or at the project level, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`eName`|<span data-ttu-id="1ffb0-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-117">Required.</span></span> <span data-ttu-id="1ffb0-118">要素名</span><span class="sxs-lookup"><span data-stu-id="1ffb0-118">Name of the element.</span></span> <span data-ttu-id="1ffb0-119">形式は、次のいずれかを示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-119">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="1ffb0-120">リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-120">-   Literal text.</span></span> <span data-ttu-id="1ffb0-121">参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-121">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="1ffb0-122">形式の式を埋め込み`<%=`e`NameExp` `%>`します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-122">-   Embedded expression of the form `<%=` e`NameExp` `%>`.</span></span> <span data-ttu-id="1ffb0-123">型`eNameExp`する必要があります`String`または<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>に暗黙的に変換できる型</span><span class="sxs-lookup"><span data-stu-id="1ffb0-123">The type of `eNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
  
    -   <span data-ttu-id="1ffb0-124">形式の式を埋め込む`<%=` `nameExp` `%>`します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-124">Embedded expression of the form `<%=` `nameExp` `%>`.</span></span> <span data-ttu-id="1ffb0-125">型`nameExp`する必要があります`String`または<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>に暗黙的に変換の種類</span><span class="sxs-lookup"><span data-stu-id="1ffb0-125">The type of `nameExp` must be `String` or a type implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span> <span data-ttu-id="1ffb0-126">要素の終了タグで、組み込み式を設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-126">An embedded expression is not allowed in a closing tag of an element.</span></span>  
  
-   `attributeList`  
  
     <span data-ttu-id="1ffb0-127">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-127">Optional.</span></span> <span data-ttu-id="1ffb0-128">属性の一覧は、リテラルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-128">List of attributes declared in the literal.</span></span>  
  
     `attribute [ attribute ... ]`  
  
     <span data-ttu-id="1ffb0-129">各`attribute`が次の構文のいずれか。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-129">Each `attribute` has one of the following syntaxes:</span></span>  
  
    -   <span data-ttu-id="1ffb0-130">属性を割り当てる、フォームの [`aPrefix``:`]`aName``=``aValue`、場所。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-130">Attribute assignment, of the form [`aPrefix``:`]`aName``=``aValue`, where:</span></span>  
  
        |<span data-ttu-id="1ffb0-131">パーツ</span><span class="sxs-lookup"><span data-stu-id="1ffb0-131">Part</span></span>|<span data-ttu-id="1ffb0-132">説明</span><span class="sxs-lookup"><span data-stu-id="1ffb0-132">Description</span></span>|  
        |---|---|  
        |`aPrefix`|<span data-ttu-id="1ffb0-133">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-133">Optional.</span></span> <span data-ttu-id="1ffb0-134">属性の XML 名前空間プレフィックス。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-134">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="1ffb0-135">グローバル XML 名前空間で定義されている必要があります、`Imports`ステートメント、またはこの要素または親要素で定義されているローカル XML 名前空間。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-135">Must be a global XML namespace that is defined with an `Imports` statement, or a local XML namespace that is defined in this element or a parent element.</span></span>|  
        |`aName`|<span data-ttu-id="1ffb0-136">必須です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-136">Required.</span></span> <span data-ttu-id="1ffb0-137">属性の名前。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-137">Name of the attribute.</span></span> <span data-ttu-id="1ffb0-138">形式は、次のいずれかを示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-138">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="1ffb0-139">リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-139">-   Literal text.</span></span> <span data-ttu-id="1ffb0-140">参照してください[宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-140">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span><br /><span data-ttu-id="1ffb0-141">形式の式を埋め込み`<%=` `aNameExp` `%>`します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-141">-   Embedded expression of the form `<%=` `aNameExp` `%>`.</span></span> <span data-ttu-id="1ffb0-142">型`aNameExp`する必要があります`String`または<xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName>に暗黙的に変換できる型</span><span class="sxs-lookup"><span data-stu-id="1ffb0-142">The type of `aNameExp` must be `String` or a type that is implicitly convertible to <xref:System.Xml.Linq.XName>.</span></span>|  
        |`aValue`|<span data-ttu-id="1ffb0-143">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-143">Optional.</span></span> <span data-ttu-id="1ffb0-144">属性の値です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-144">Value of the attribute.</span></span> <span data-ttu-id="1ffb0-145">形式は、次のいずれかを示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-145">The format is one of the following:</span></span><br /><br /> <span data-ttu-id="1ffb0-146">の引用符で囲むリテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-146">-   Literal text, enclosed in quotation marks.</span></span><br /><span data-ttu-id="1ffb0-147">形式の式を埋め込み`<%=` `aValueExp` `%>`します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-147">-   Embedded expression of the form `<%=` `aValueExp` `%>`.</span></span> <span data-ttu-id="1ffb0-148">任意の型を許可します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-148">Any type is allowed.</span></span>|  
  
    -   <span data-ttu-id="1ffb0-149">形式の式を埋め込む`<%=` `aExp` `%>`します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-149">Embedded expression of the form `<%=` `aExp` `%>`.</span></span>  
  
-   `/>`  
  
     <span data-ttu-id="1ffb0-150">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-150">Optional.</span></span> <span data-ttu-id="1ffb0-151">要素がコンテンツのない、空の要素であることを示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-151">Indicates that the element is an empty element, without content.</span></span>  
  
-   `>`  
  
     <span data-ttu-id="1ffb0-152">必須です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-152">Required.</span></span> <span data-ttu-id="1ffb0-153">以降、または空要素タグを終了します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-153">Ends the beginning or empty element tag.</span></span>  
  
-   `elementContents`  
  
     <span data-ttu-id="1ffb0-154">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-154">Optional.</span></span> <span data-ttu-id="1ffb0-155">要素の内容。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-155">Content of the element.</span></span>  
  
     `content [ content ... ]`  
  
     <span data-ttu-id="1ffb0-156">各`content`次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-156">Each `content` can be one of the following:</span></span>  
  
    -   <span data-ttu-id="1ffb0-157">リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-157">Literal text.</span></span> <span data-ttu-id="1ffb0-158">内のすべての空白`elementContents`リテラル テキストがある場合に有効になります。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-158">All the white space in `elementContents` becomes significant if there is any literal text.</span></span>  
  
    -   <span data-ttu-id="1ffb0-159">形式の式を埋め込む`<%=` `contentExp` `%>`します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-159">Embedded expression of the form `<%=` `contentExp` `%>`.</span></span>  
  
    -   <span data-ttu-id="1ffb0-160">XML 要素リテラルです。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-160">XML element literal.</span></span>  
  
    -   <span data-ttu-id="1ffb0-161">XML コメント リテラルです。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-161">XML comment literal.</span></span> <span data-ttu-id="1ffb0-162">参照してください[XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-162">See [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>  
  
    -   <span data-ttu-id="1ffb0-163">XML 処理命令リテラルです。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-163">XML processing instruction literal.</span></span> <span data-ttu-id="1ffb0-164">参照してください[XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-164">See [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span>  
  
    -   <span data-ttu-id="1ffb0-165">XML CDATA リテラルです。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-165">XML CDATA literal.</span></span> <span data-ttu-id="1ffb0-166">参照してください[XML CDATA リテラル](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-166">See [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).</span></span>  
  
-   <span data-ttu-id="1ffb0-167">`</`[`name`]`>`</span><span class="sxs-lookup"><span data-stu-id="1ffb0-167">`</`[`name`]`>`</span></span>  
  
     <span data-ttu-id="1ffb0-168">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-168">Optional.</span></span> <span data-ttu-id="1ffb0-169">要素の終了タグを表します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-169">Represents the closing tag for the element.</span></span> <span data-ttu-id="1ffb0-170">省略可能な`name`の埋め込み式の結果になる場合、パラメーターは許可されません。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-170">The optional `name` parameter is not allowed when it is the result of an embedded expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ffb0-171">戻り値</span><span class="sxs-lookup"><span data-stu-id="1ffb0-171">Return Value</span></span>  
 <span data-ttu-id="1ffb0-172"><xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-172">An <xref:System.Xml.Linq.XElement> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ffb0-173">コメント</span><span class="sxs-lookup"><span data-stu-id="1ffb0-173">Remarks</span></span>  
 <span data-ttu-id="1ffb0-174">作成する XML 要素リテラルの構文を使用する<xref:System.Xml.Linq.XElement>、コード内のオブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-174">You can use the XML element literal syntax to create <xref:System.Xml.Linq.XElement> objects in your code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ffb0-175">XML リテラルは、行継続文字を使用せず複数の行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-175">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="1ffb0-176">この機能を使用すると、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-176">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="1ffb0-177">形式の式を埋め込む`<%=` `exp` `%>`を使用すると、XML 要素リテラルに動的な情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-177">Embedded expressions of the form `<%=` `exp` `%>` enable you to add dynamic information to an XML element literal.</span></span> <span data-ttu-id="1ffb0-178">詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-178">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="1ffb0-179">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラへの呼び出しにリテラルの XML 要素に変換して、<xref:System.Xml.Linq.XElement.%23ctor%2A>コンス トラクターと、必要な場合、<xref:System.Xml.Linq.XAttribute.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XAttribute.%23ctor%2A> </xref:System.Xml.Linq.XElement.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-179">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML element literal into calls to the <xref:System.Xml.Linq.XElement.%23ctor%2A> constructor and, if it is required, the <xref:System.Xml.Linq.XAttribute.%23ctor%2A> constructor.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="1ffb0-180">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="1ffb0-180">XML Namespaces</span></span>  
 <span data-ttu-id="1ffb0-181">XML 名前空間プレフィックスは、コードに何度も同じ名前空間の要素を含む XML リテラルを作成する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-181">XML namespace prefixes are useful when you have to create XML literals with elements from the same namespace many times in code.</span></span> <span data-ttu-id="1ffb0-182">使用して定義するグローバルの XML 名前空間プレフィックスを使用する、`Imports`ステートメント、またはローカルのプレフィックスは、使用して定義する、 `xmlns:``xmlPrefix`="`xmlNamespace`"属性構文です。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-182">You can use global XML namespace prefixes, which you define by using the `Imports` statement, or local prefixes, which you define by using the `xmlns:``xmlPrefix`="`xmlNamespace`" attribute syntax.</span></span> <span data-ttu-id="1ffb0-183">詳細については、次を参照してください。 [Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-183">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
 <span data-ttu-id="1ffb0-184">XML 名前空間のスコープの規則に従ってローカル プレフィックスはグローバル プレフィックスに優先します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-184">In accordance with the scoping rules for XML namespaces, local prefixes take precedence over global prefixes.</span></span> <span data-ttu-id="1ffb0-185">ただし、XML リテラルには、XML 名前空間が定義されている場合はその名前空間は、組み込み式に出現する式を使用できません。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-185">However, if an XML literal defines an XML namespace, that namespace is not available to expressions that appear in an embedded expression.</span></span> <span data-ttu-id="1ffb0-186">埋め込み式は、グローバルの XML 名前空間のみにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-186">The embedded expression can access only the global XML namespace.</span></span>  
  
 <span data-ttu-id="1ffb0-187">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラが各グローバル生成されたコード内のローカルの名前空間の定義を&1; つに、XML リテラルで使用される XML 名前空間に変換します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-187">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts each global XML namespace that is used by an XML literal into a one local namespace definition in the generated code.</span></span> <span data-ttu-id="1ffb0-188">使用されていないグローバルの XML 名前空間は、生成されたコードには表示されません。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-188">Global XML namespaces that are not used do not appear in the generated code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ffb0-189">例</span><span class="sxs-lookup"><span data-stu-id="1ffb0-189">Example</span></span>  
 <span data-ttu-id="1ffb0-190">次の例では、2 つの入れ子になった空要素を持つ単純な XML 要素を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-190">The following example shows how to create a simple XML element that has two nested empty elements.</span></span>  
  
 <span data-ttu-id="1ffb0-191">[!code-vb[VbXMLSamples&#20;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ffb0-191">[!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]</span></span>  
  
 <span data-ttu-id="1ffb0-192">この例では、次のテキストを表示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-192">The example displays the following text.</span></span> <span data-ttu-id="1ffb0-193">リテラルは、空の要素の構造を維持することを確認します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-193">Notice that the literal preserves the structure of the empty elements.</span></span>  
  
```  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a><span data-ttu-id="1ffb0-194">例</span><span class="sxs-lookup"><span data-stu-id="1ffb0-194">Example</span></span>  
 <span data-ttu-id="1ffb0-195">次の例では、組み込み式を使用して、要素の名前を指定し、属性を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-195">The following example shows how to use embedded expressions to name an element and create attributes.</span></span>  
  
 <span data-ttu-id="1ffb0-196">[!code-vb[VbXMLSamples #&21;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ffb0-196">[!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]</span></span>  
  
 <span data-ttu-id="1ffb0-197">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-197">This code displays the following text:</span></span>  
  
```  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a><span data-ttu-id="1ffb0-198">例</span><span class="sxs-lookup"><span data-stu-id="1ffb0-198">Example</span></span>  
 <span data-ttu-id="1ffb0-199">次の例では、`ns` を名前空間プレフィックスとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-199">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="1ffb0-200">XML リテラルを作成する名前空間のプレフィックスを使用し、要素の最終的なフォームを表示します。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-200">It then uses the prefix of the namespace to create an XML literal and displays the element's final form.</span></span>  
  
 <span data-ttu-id="1ffb0-201">[!code-vb[VbXMLSamples #&22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1ffb0-201">[!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]</span></span>  
  
 <span data-ttu-id="1ffb0-202">このコードを実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-202">This code displays the following text:</span></span>  
  
```  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 <span data-ttu-id="1ffb0-203">コンパイラが XML 名前空間のプレフィックス定義にグローバルの XML 名前空間のプレフィックスを変換することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-203">Notice that the compiler converted the prefix of the global XML namespace into a prefix definition for the XML namespace.</span></span> <span data-ttu-id="1ffb0-204">\<Ns:middle > 要素の XML 名前空間プレフィックスを再定義、 \<ns:inner1 > 要素。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-204">The \<ns:middle> element redefines the XML namespace prefix for the \<ns:inner1> element.</span></span> <span data-ttu-id="1ffb0-205">ただし、 \<ns:inner2 > 要素によって定義された名前空間を使用して、`Imports`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1ffb0-205">However, the \<ns:inner2> element uses the namespace defined by the `Imports` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ffb0-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ffb0-206">See Also</span></span>  
 <span data-ttu-id="1ffb0-207"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="1ffb0-207"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="1ffb0-208"> [宣言する XML 要素と属性の名前](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="1ffb0-208"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md) </span></span>  
<span data-ttu-id="1ffb0-209"> [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span><span class="sxs-lookup"><span data-stu-id="1ffb0-209"> [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span></span>  
<span data-ttu-id="1ffb0-210"> [XML CDATA リテラル](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md) </span><span class="sxs-lookup"><span data-stu-id="1ffb0-210"> [XML CDATA Literal](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md) </span></span>  
<span data-ttu-id="1ffb0-211"> [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="1ffb0-211"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="1ffb0-212"> [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1ffb0-212"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="1ffb0-213"> [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="1ffb0-213"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="1ffb0-214"> [Imports ステートメント (XML 名前空間)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)</span><span class="sxs-lookup"><span data-stu-id="1ffb0-214"> [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)</span></span>
