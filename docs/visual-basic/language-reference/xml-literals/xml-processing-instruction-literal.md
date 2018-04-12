---
title: XML 処理命令リテラル (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralProcessingInstruction
helpviewer_keywords:
- XML literals [Visual Basic], processing instruction
- XML processing instruction literal [Visual Basic]
- processing instruction literal [Visual Basic]
ms.assetid: cef4f7f8-0011-4f64-8602-795077ad4f15
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ce0f2d0dff80072beefdb4f84643ea28e2cf165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xml-processing-instruction-literal-visual-basic"></a><span data-ttu-id="46d25-102">XML 処理命令リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46d25-102">XML Processing Instruction Literal (Visual Basic)</span></span>
<span data-ttu-id="46d25-103">リテラルを表す、<xref:System.Xml.Linq.XProcessingInstruction>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="46d25-103">A literal representing an <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d25-104">構文</span><span class="sxs-lookup"><span data-stu-id="46d25-104">Syntax</span></span>  
  
```xml  
<?piName [ = piData ] ?>  
```  
  
## <a name="parts"></a><span data-ttu-id="46d25-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="46d25-105">Parts</span></span>  
 `<?`  
 <span data-ttu-id="46d25-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="46d25-106">Required.</span></span> <span data-ttu-id="46d25-107">XML 処理命令リテラルの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="46d25-107">Denotes the start of the XML processing instruction literal.</span></span>  
  
 `piName`  
 <span data-ttu-id="46d25-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="46d25-108">Required.</span></span> <span data-ttu-id="46d25-109">アプリケーションを示す処理命令のターゲットを名前します。</span><span class="sxs-lookup"><span data-stu-id="46d25-109">Name indicating which application the processing instruction targets.</span></span> <span data-ttu-id="46d25-110">"Xml"または"XML"で始まることはできません。</span><span class="sxs-lookup"><span data-stu-id="46d25-110">Cannot begin with "xml" or "XML".</span></span>  
  
 `piData`  
 <span data-ttu-id="46d25-111">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="46d25-111">Optional.</span></span> <span data-ttu-id="46d25-112">アプリケーションの対象とする方法を示す文字列`piName`XML ドキュメントを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46d25-112">String indicating how the application targeted by `piName` should process the XML document.</span></span>  
  
 `?>`  
 <span data-ttu-id="46d25-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="46d25-113">Required.</span></span> <span data-ttu-id="46d25-114">処理命令の終了を示します。</span><span class="sxs-lookup"><span data-stu-id="46d25-114">Denotes the end of the processing instruction.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46d25-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="46d25-115">Return Value</span></span>  
 <span data-ttu-id="46d25-116"><xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="46d25-116">An <xref:System.Xml.Linq.XProcessingInstruction> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46d25-117">コメント</span><span class="sxs-lookup"><span data-stu-id="46d25-117">Remarks</span></span>  
 <span data-ttu-id="46d25-118">XML 処理命令リテラルは、アプリケーションが XML ドキュメントを処理する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="46d25-118">XML processing instruction literals indicate how applications should process an XML document.</span></span> <span data-ttu-id="46d25-119">アプリケーションには、XML ドキュメントが読み込まれると、アプリケーションは、XML 処理命令、ドキュメントを処理する方法を決定を確認できます。</span><span class="sxs-lookup"><span data-stu-id="46d25-119">When an application loads an XML document, the application can check the XML processing instructions to determine how to process the document.</span></span> <span data-ttu-id="46d25-120">アプリケーションの意味を解釈する`piName`と`piData`です。</span><span class="sxs-lookup"><span data-stu-id="46d25-120">The application interprets the meaning of `piName` and `piData`.</span></span>  
  
 <span data-ttu-id="46d25-121">XML ドキュメント リテラルは、XML 処理命令に似ていますが構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="46d25-121">The XML document literal uses syntax that is similar to that of the XML processing instruction.</span></span> <span data-ttu-id="46d25-122">詳細については、次を参照してください。 [XML ドキュメント リテラル](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)です。</span><span class="sxs-lookup"><span data-stu-id="46d25-122">For more information, see [XML Document Literal](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46d25-123">`piName`要素は、XML 1.0 仕様は、これらの id を予約するため、文字列"xml"または"XML"で始めることはできません。</span><span class="sxs-lookup"><span data-stu-id="46d25-123">The `piName` element cannot begin with the strings "xml" or "XML", because the XML 1.0 specification reserves those identifiers.</span></span>  
  
 <span data-ttu-id="46d25-124">変数に XML 処理命令リテラルを代入または XML ドキュメント リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="46d25-124">You can assign an XML processing instruction literal to a variable or include it in an XML document literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46d25-125">XML リテラルは、行継続文字をことがなく複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="46d25-125">An XML literal can span multiple lines without needing line continuation characters.</span></span> <span data-ttu-id="46d25-126">これにより、XML ドキュメントの内容をコピーして貼り付けに直接、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プログラムです。</span><span class="sxs-lookup"><span data-stu-id="46d25-126">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.</span></span>  
  
 <span data-ttu-id="46d25-127">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラへの呼び出しにリテラルの XML 処理命令を変換する、<xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="46d25-127">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts the XML processing instruction literal to a call to the <xref:System.Xml.Linq.XProcessingInstruction.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46d25-128">例</span><span class="sxs-lookup"><span data-stu-id="46d25-128">Example</span></span>  
 <span data-ttu-id="46d25-129">次の例では、XML ドキュメントのスタイル シートを識別する処理命令を作成します。</span><span class="sxs-lookup"><span data-stu-id="46d25-129">The following example creates a processing instruction identifying a style-sheet for an XML document.</span></span>  
  
 [!code-vb[VbXMLSamples#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-processing-instruction-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="46d25-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="46d25-130">See Also</span></span>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 [<span data-ttu-id="46d25-131">XML ドキュメント リテラル</span><span class="sxs-lookup"><span data-stu-id="46d25-131">XML Document Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [<span data-ttu-id="46d25-132">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="46d25-132">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="46d25-133">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="46d25-133">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
