---
title: XML ドキュメント リテラル (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5c84fecbb035c229cc3576bc556db6ecb6f3934
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="85fbb-102">XML ドキュメント リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85fbb-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="85fbb-103">リテラルを表す、<xref:System.Xml.Linq.XDocument>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="85fbb-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85fbb-104">構文</span><span class="sxs-lookup"><span data-stu-id="85fbb-104">Syntax</span></span>  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="85fbb-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="85fbb-105">Parts</span></span>  
  
|<span data-ttu-id="85fbb-106">用語</span><span class="sxs-lookup"><span data-stu-id="85fbb-106">Term</span></span>|<span data-ttu-id="85fbb-107">定義</span><span class="sxs-lookup"><span data-stu-id="85fbb-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="85fbb-108">任意。</span><span class="sxs-lookup"><span data-stu-id="85fbb-108">Optional.</span></span> <span data-ttu-id="85fbb-109">リテラルのテキスト エンコード ドキュメントの宣言を使用します。</span><span class="sxs-lookup"><span data-stu-id="85fbb-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="85fbb-110">任意。</span><span class="sxs-lookup"><span data-stu-id="85fbb-110">Optional.</span></span> <span data-ttu-id="85fbb-111">リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="85fbb-111">Literal text.</span></span> <span data-ttu-id="85fbb-112">"Yes"にする必要がありますまたは"no"です。</span><span class="sxs-lookup"><span data-stu-id="85fbb-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="85fbb-113">任意。</span><span class="sxs-lookup"><span data-stu-id="85fbb-113">Optional.</span></span> <span data-ttu-id="85fbb-114">XML 処理命令や XML コメントの一覧です。</span><span class="sxs-lookup"><span data-stu-id="85fbb-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="85fbb-115">次の形式になります。</span><span class="sxs-lookup"><span data-stu-id="85fbb-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="85fbb-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="85fbb-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="85fbb-117">各`piComment`次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="85fbb-117">Each `piComment` can be one of the following:</span></span><br /><br /> <span data-ttu-id="85fbb-118">-   [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)です。</span><span class="sxs-lookup"><span data-stu-id="85fbb-118">-   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="85fbb-119">-   [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)です。</span><span class="sxs-lookup"><span data-stu-id="85fbb-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="85fbb-120">必須。</span><span class="sxs-lookup"><span data-stu-id="85fbb-120">Required.</span></span> <span data-ttu-id="85fbb-121">ドキュメントのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="85fbb-121">Root element of the document.</span></span> <span data-ttu-id="85fbb-122">形式では、次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="85fbb-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="85fbb-123">[XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)です。</span><span class="sxs-lookup"><span data-stu-id="85fbb-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="85fbb-124">形式の式を埋め込む`<%=` `elementExp` `%>`です。</span><span class="sxs-lookup"><span data-stu-id="85fbb-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="85fbb-125">`elementExp`次のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="85fbb-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="85fbb-126"><xref:System.Xml.Linq.XElement> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="85fbb-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="85fbb-127">いずれかを含むコレクション<xref:System.Xml.Linq.XElement>オブジェクトと任意の数の<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="85fbb-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="85fbb-128">詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)です。</span><span class="sxs-lookup"><span data-stu-id="85fbb-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="85fbb-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="85fbb-129">Return Value</span></span>  
 <span data-ttu-id="85fbb-130"><xref:System.Xml.Linq.XDocument> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="85fbb-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85fbb-131">コメント</span><span class="sxs-lookup"><span data-stu-id="85fbb-131">Remarks</span></span>  
 <span data-ttu-id="85fbb-132">XML ドキュメント リテラルは、リテラルの先頭に XML 宣言によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="85fbb-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="85fbb-133">各 XML ドキュメント リテラルには、XML のルート要素の 1 つだけ必要がありますが、任意の数 XML 処理命令や XML コメントの持つことができます。</span><span class="sxs-lookup"><span data-stu-id="85fbb-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="85fbb-134">XML ドキュメント リテラルは、XML 要素ではできません。</span><span class="sxs-lookup"><span data-stu-id="85fbb-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85fbb-135">XML リテラルは、行継続文字を使用せず複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="85fbb-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="85fbb-136">これにより、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="85fbb-136">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="85fbb-137">Visual Basic コンパイラでは、リテラルの XML ドキュメントを変換への呼び出しに、<xref:System.Xml.Linq.XDocument.%23ctor%2A>と<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="85fbb-137">The Visual Basic compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85fbb-138">例</span><span class="sxs-lookup"><span data-stu-id="85fbb-138">Example</span></span>  
 <span data-ttu-id="85fbb-139">次の例では、XML 宣言、処理命令、コメント、および別の要素を格納する要素のある XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="85fbb-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="85fbb-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="85fbb-140">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [<span data-ttu-id="85fbb-141">XML 処理命令リテラル</span><span class="sxs-lookup"><span data-stu-id="85fbb-141">XML Processing Instruction Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [<span data-ttu-id="85fbb-142">XML コメント リテラル</span><span class="sxs-lookup"><span data-stu-id="85fbb-142">XML Comment Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [<span data-ttu-id="85fbb-143">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="85fbb-143">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="85fbb-144">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="85fbb-144">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="85fbb-145">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="85fbb-145">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="85fbb-146">XML での埋め込み式</span><span class="sxs-lookup"><span data-stu-id="85fbb-146">Embedded Expressions in XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
