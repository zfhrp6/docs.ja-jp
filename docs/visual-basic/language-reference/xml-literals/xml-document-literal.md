---
title: "XML ドキュメント リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
dev_langs:
- VB
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
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
ms.openlocfilehash: 5e173c8bc89f61925c3e6127fb3cac61379aeffa
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xml-document-literal-visual-basic"></a><span data-ttu-id="db1ad-102">XML ドキュメント リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db1ad-102">XML Document Literal (Visual Basic)</span></span>
<span data-ttu-id="db1ad-103">リテラルを表す、<xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="db1ad-103">A literal representing an <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db1ad-104">構文</span><span class="sxs-lookup"><span data-stu-id="db1ad-104">Syntax</span></span>  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a><span data-ttu-id="db1ad-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="db1ad-105">Parts</span></span>  
  
|<span data-ttu-id="db1ad-106">用語</span><span class="sxs-lookup"><span data-stu-id="db1ad-106">Term</span></span>|<span data-ttu-id="db1ad-107">定義</span><span class="sxs-lookup"><span data-stu-id="db1ad-107">Definition</span></span>|  
|---|---|  
|`encoding`|<span data-ttu-id="db1ad-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="db1ad-108">Optional.</span></span> <span data-ttu-id="db1ad-109">リテラル テキストをエンコード ドキュメントの宣言を使用します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-109">Literal text declaring which encoding the document uses.</span></span>|  
|`standalone`|<span data-ttu-id="db1ad-110">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="db1ad-110">Optional.</span></span> <span data-ttu-id="db1ad-111">リテラル テキスト。</span><span class="sxs-lookup"><span data-stu-id="db1ad-111">Literal text.</span></span> <span data-ttu-id="db1ad-112">"Yes"にする必要がありますまたは"no"です。</span><span class="sxs-lookup"><span data-stu-id="db1ad-112">Must be "yes" or "no".</span></span>|  
|`piCommentList`|<span data-ttu-id="db1ad-113">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="db1ad-113">Optional.</span></span> <span data-ttu-id="db1ad-114">XML 処理命令と XML コメントの一覧です。</span><span class="sxs-lookup"><span data-stu-id="db1ad-114">List of XML processing instructions and XML comments.</span></span> <span data-ttu-id="db1ad-115">次の形式を取ります。</span><span class="sxs-lookup"><span data-stu-id="db1ad-115">Takes the following format:</span></span><br /><br /> <span data-ttu-id="db1ad-116">`piComment [` `piComment` `... ]`</span><span class="sxs-lookup"><span data-stu-id="db1ad-116">`piComment [` `piComment` `... ]`</span></span><br /><br /> <span data-ttu-id="db1ad-117">各`piComment`次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="db1ad-117">Each `piComment`can be one of the following:</span></span><br /><br /><span data-ttu-id="db1ad-118"> -   [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-118"> -   [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).</span></span><br /><span data-ttu-id="db1ad-119">-   [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-119">-   [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).</span></span>|  
|`rootElement`|<span data-ttu-id="db1ad-120">必須です。</span><span class="sxs-lookup"><span data-stu-id="db1ad-120">Required.</span></span> <span data-ttu-id="db1ad-121">ドキュメントのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="db1ad-121">Root element of the document.</span></span> <span data-ttu-id="db1ad-122">形式は、次のいずれかを示します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-122">The format is one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="db1ad-123">[XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-123">[XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</span></span></li><li><span data-ttu-id="db1ad-124">形式の式を埋め込む`<%=` `elementExp` `%>`します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-124">Embedded expression of the form `<%=` `elementExp` `%>`.</span></span> <span data-ttu-id="db1ad-125">`elementExp`次のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-125">The `elementExp` returns one of the following:</span></span><br /><br /> <ul><li><span data-ttu-id="db1ad-126"><xref:System.Xml.Linq.XElement>オブジェクト</xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="db1ad-126">An <xref:System.Xml.Linq.XElement> object.</span></span></li><li><span data-ttu-id="db1ad-127">1 つ含まれているコレクション<xref:System.Xml.Linq.XElement>オブジェクトと任意の数の<xref:System.Xml.Linq.XProcessingInstruction>と<xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="db1ad-127">A collection that contains one <xref:System.Xml.Linq.XElement> object and any number of <xref:System.Xml.Linq.XProcessingInstruction> and <xref:System.Xml.Linq.XComment> objects.</span></span></li></ul></li></ul><br /> <span data-ttu-id="db1ad-128">詳細については、次を参照してください。 [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-128">For more information, see [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="db1ad-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="db1ad-129">Return Value</span></span>  
 <span data-ttu-id="db1ad-130"><xref:System.Xml.Linq.XDocument>オブジェクト</xref:System.Xml.Linq.XDocument>。</span><span class="sxs-lookup"><span data-stu-id="db1ad-130">An <xref:System.Xml.Linq.XDocument> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db1ad-131">コメント</span><span class="sxs-lookup"><span data-stu-id="db1ad-131">Remarks</span></span>  
 <span data-ttu-id="db1ad-132">XML ドキュメント リテラルは、リテラルの先頭に XML 宣言によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="db1ad-132">An XML document literal is identified by the XML declaration at the start of the literal.</span></span> <span data-ttu-id="db1ad-133">各 XML ドキュメント リテラルにはただ&1; つの XML ルート要素を設定する必要がありますが、任意の数の XML 処理命令と XML のコメントがあることができます。</span><span class="sxs-lookup"><span data-stu-id="db1ad-133">Although each XML document literal must have exactly one root XML element, it can have any number of XML processing instructions and XML comments.</span></span>  
  
 <span data-ttu-id="db1ad-134">XML ドキュメント リテラルは、XML 要素にはできません。</span><span class="sxs-lookup"><span data-stu-id="db1ad-134">An XML document literal cannot appear in an XML element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="db1ad-135">XML リテラルは、行継続文字を使用せず複数の行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="db1ad-135">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="db1ad-136">これにより、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。</span><span class="sxs-lookup"><span data-stu-id="db1ad-136">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="db1ad-137">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、リテラル XML ドキュメントを変換への呼び出しに、<xref:System.Xml.Linq.XDocument.%23ctor%2A>と<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XDeclaration.%23ctor%2A> </xref:System.Xml.Linq.XDocument.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="db1ad-137">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML document literal into calls to the <xref:System.Xml.Linq.XDocument.%23ctor%2A> and <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> constructors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db1ad-138">例</span><span class="sxs-lookup"><span data-stu-id="db1ad-138">Example</span></span>  
 <span data-ttu-id="db1ad-139">次の例では、XML 宣言、処理命令、コメント、および別の要素を含む要素には、XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="db1ad-139">The following example creates an XML document that has an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
 <span data-ttu-id="db1ad-140">[!code-vb[VbXMLSamples #&30;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="db1ad-140">[!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db1ad-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="db1ad-141">See Also</span></span>  
 <span data-ttu-id="db1ad-142"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="db1ad-142"><xref:System.Xml.Linq.XElement></span></span>   
 <span data-ttu-id="db1ad-143"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="db1ad-143"><xref:System.Xml.Linq.XProcessingInstruction></span></span>   
 <span data-ttu-id="db1ad-144"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="db1ad-144"><xref:System.Xml.Linq.XComment></span></span>   
 <span data-ttu-id="db1ad-145"><xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="db1ad-145"><xref:System.Xml.Linq.XDocument></span></span>   
<span data-ttu-id="db1ad-146"> [XML 処理命令リテラル](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md) </span><span class="sxs-lookup"><span data-stu-id="db1ad-146"> [XML Processing Instruction Literal](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md) </span></span>  
<span data-ttu-id="db1ad-147"> [XML コメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span><span class="sxs-lookup"><span data-stu-id="db1ad-147"> [XML Comment Literal](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md) </span></span>  
<span data-ttu-id="db1ad-148"> [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="db1ad-148"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="db1ad-149"> [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="db1ad-149"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="db1ad-150"> [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="db1ad-150"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="db1ad-151"> [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)</span><span class="sxs-lookup"><span data-stu-id="db1ad-151"> [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)</span></span>
