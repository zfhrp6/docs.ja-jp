---
title: "XML CDATA リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
dev_langs:
- VB
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
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
ms.openlocfilehash: 6bf12a5dd5b24b0a915cb15f41cb8947c33e94b0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="cfd0f-102">XML CDATA リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfd0f-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="cfd0f-103">リテラルを表す、<xref:System.Xml.Linq.XCData>オブジェクト</xref:System.Xml.Linq.XCData>。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd0f-104">構文</span><span class="sxs-lookup"><span data-stu-id="cfd0f-104">Syntax</span></span>  
  
```  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="cfd0f-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="cfd0f-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="cfd0f-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-106">Required.</span></span> <span data-ttu-id="cfd0f-107">XML CDATA セクションの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="cfd0f-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-108">Required.</span></span> <span data-ttu-id="cfd0f-109">XML CDATA セクションに表示されるテキストの内容。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="cfd0f-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-110">Required.</span></span> <span data-ttu-id="cfd0f-111">セクションの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfd0f-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="cfd0f-112">Return Value</span></span>  
 <span data-ttu-id="cfd0f-113"><xref:System.Xml.Linq.XCData>オブジェクト</xref:System.Xml.Linq.XCData>。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfd0f-114">コメント</span><span class="sxs-lookup"><span data-stu-id="cfd0f-114">Remarks</span></span>  
 <span data-ttu-id="cfd0f-115">XML CDATA セクションには、未加工のテキストが含まれているは解析されずに、それを含んでいる xml が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="cfd0f-116">XML CDATA セクションには、任意のテキストを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="cfd0f-117">これには、予約済み XML 文字が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-117">This includes reserved XML characters.</span></span> <span data-ttu-id="cfd0f-118">XML CDATA セクションは、シーケンスで終わる"] >"です。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="cfd0f-119">これは、次の点を意味します。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="cfd0f-120">組み込み式の区切り記号が有効な XML CDATA コンテンツであるので、リテラル XML CDATA で埋め込み式を使用できません。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="cfd0f-121">XML CDATA セクションは入れ子にできないため`content`値を含めることはできません"] >"です。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="cfd0f-122">リテラル XML CDATA を変数を割り当てたり、XML 要素リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfd0f-123">XML リテラルでは、複数行にまたがることができますが、行継続文字を使用しません。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="cfd0f-124">これにより、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-124">This enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="cfd0f-125">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、XML CDATA リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XCData.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XCData.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-125">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfd0f-126">例</span><span class="sxs-lookup"><span data-stu-id="cfd0f-126">Example</span></span>  
 <span data-ttu-id="cfd0f-127">次の例では、CDATA セクションのテキストを含む"リテラルに含めることができる\<XML > タグ"です。</span><span class="sxs-lookup"><span data-stu-id="cfd0f-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 <span data-ttu-id="cfd0f-128">[!code-vb[VbXMLSamples 第&23;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cfd0f-128">[!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd0f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfd0f-129">See Also</span></span>  
 <span data-ttu-id="cfd0f-130"><xref:System.Xml.Linq.XCData></xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="cfd0f-130"><xref:System.Xml.Linq.XCData></span></span>   
<span data-ttu-id="cfd0f-131"> [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="cfd0f-131"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="cfd0f-132"> [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="cfd0f-132"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="cfd0f-133"> [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="cfd0f-133"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
