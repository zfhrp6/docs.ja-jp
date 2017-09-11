---
title: "XML 処理命令リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
dev_langs:
- VB
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
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
ms.openlocfilehash: 2ae976530ed3028677a1fef39db92265591df530
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="fd5ad-102">XML 処理命令リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd5ad-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="fd5ad-103">リテラルを表す、<xref:System.Xml.Linq.XProcessingInstruction>オブジェクト</xref:System.Xml.Linq.XProcessingInstruction>。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5ad-104">構文</span><span class="sxs-lookup"><span data-stu-id="fd5ad-104">Syntax</span></span>  
  
```  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="fd5ad-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="fd5ad-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="fd5ad-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-106">Required.</span></span> <span data-ttu-id="fd5ad-107">XML 処理命令リテラルの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="fd5ad-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-108">Required.</span></span> <span data-ttu-id="fd5ad-109">アプリケーションを示す処理命令のターゲットを名前します。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="fd5ad-110">"Xml"または"XML"で始まることはできません。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="fd5ad-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-111">Optional.</span></span> <span data-ttu-id="fd5ad-112">アプリケーションの対象とする方法を示す文字列`piName`XML ドキュメントを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="fd5ad-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-113">Required.</span></span> <span data-ttu-id="fd5ad-114">処理命令の終了を示します。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fd5ad-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="fd5ad-115">Return Value</span></span>  
 <span data-ttu-id="fd5ad-116"><xref:System.Xml.Linq.XProcessingInstruction>オブジェクト</xref:System.Xml.Linq.XProcessingInstruction>。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd5ad-117">コメント</span><span class="sxs-lookup"><span data-stu-id="fd5ad-117">Remarks</span></span>  
 <span data-ttu-id="fd5ad-118">XML 処理命令リテラルは、アプリケーションが、XML ドキュメントを処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="fd5ad-119">アプリケーションに XML ドキュメントが読み込まれると、アプリケーションは、ドキュメントを処理する方法を決定する XML 処理命令をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="fd5ad-120">アプリケーションの意味を解釈する`piName`と`piData`です。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="fd5ad-121">XML ドキュメント リテラルは、XML 処理命令の次のような構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="fd5ad-122">詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)します。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd5ad-123">`piName`のため、XML 1.0 仕様これらの id を確保するため、要素が文字列"xml"または"XML"で始まることはできません。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="fd5ad-124">変数には、XML 処理命令リテラルを代入したり、XML ドキュメント リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd5ad-125">XML リテラルは、行継続文字をしなくても複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="fd5ad-126">これにより、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-126">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="fd5ad-127">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、XML 処理命令リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-127">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd5ad-128">例</span><span class="sxs-lookup"><span data-stu-id="fd5ad-128">Example</span></span>  
 <span data-ttu-id="fd5ad-129">次の例では、XML ドキュメントのスタイル シートを識別する処理命令を作成します。</span><span class="sxs-lookup"><span data-stu-id="fd5ad-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 <span data-ttu-id="fd5ad-130">[!code-vb[VbXMLSamples #&28;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fd5ad-130">[!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5ad-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd5ad-131">See Also</span></span>  
 <span data-ttu-id="fd5ad-132"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="fd5ad-132"><xref:System.Xml.Linq.XProcessingInstruction></span></span>   
<span data-ttu-id="fd5ad-133"> [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span><span class="sxs-lookup"><span data-stu-id="fd5ad-133"> [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md) </span></span>  
<span data-ttu-id="fd5ad-134"> [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="fd5ad-134"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="fd5ad-135"> [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="fd5ad-135"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
