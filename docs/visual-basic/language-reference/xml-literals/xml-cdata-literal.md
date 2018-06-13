---
title: XML CDATA リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 999531d8146748fe491255663f0d2d17d056bcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603835"
---
# <a name="xml-cdata-literal-visual-basic"></a><span data-ttu-id="c307c-102">XML CDATA リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c307c-102">XML CDATA Literal (Visual Basic)</span></span>
<span data-ttu-id="c307c-103">リテラルを表す、<xref:System.Xml.Linq.XCData>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c307c-103">A literal representing an <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c307c-104">構文</span><span class="sxs-lookup"><span data-stu-id="c307c-104">Syntax</span></span>  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a><span data-ttu-id="c307c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c307c-105">Parts</span></span>  
 `<![CDATA[`  
 <span data-ttu-id="c307c-106">必須。</span><span class="sxs-lookup"><span data-stu-id="c307c-106">Required.</span></span> <span data-ttu-id="c307c-107">XML CDATA セクションの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="c307c-107">Denotes the start of the XML CDATA section.</span></span>  
  
 `content`  
 <span data-ttu-id="c307c-108">必須。</span><span class="sxs-lookup"><span data-stu-id="c307c-108">Required.</span></span> <span data-ttu-id="c307c-109">XML CDATA セクションに表示されるテキストの内容。</span><span class="sxs-lookup"><span data-stu-id="c307c-109">Text content to appear in the XML CDATA section.</span></span>  
  
 `]]>`  
 <span data-ttu-id="c307c-110">必須。</span><span class="sxs-lookup"><span data-stu-id="c307c-110">Required.</span></span> <span data-ttu-id="c307c-111">セクションの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="c307c-111">Denotes the end of the section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c307c-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="c307c-112">Return Value</span></span>  
 <span data-ttu-id="c307c-113"><xref:System.Xml.Linq.XCData> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c307c-113">An <xref:System.Xml.Linq.XCData> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c307c-114">コメント</span><span class="sxs-lookup"><span data-stu-id="c307c-114">Remarks</span></span>  
 <span data-ttu-id="c307c-115">XML CDATA セクションを含む未加工のテキストが含まれている場合は、それを含む XML を解析できません。</span><span class="sxs-lookup"><span data-stu-id="c307c-115">XML CDATA sections contain raw text that should be included, but not parsed, with the XML that contains it.</span></span> <span data-ttu-id="c307c-116">XML CDATA セクションには、任意のテキストを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c307c-116">A XML CDATA section can contain any text.</span></span> <span data-ttu-id="c307c-117">これには、予約済み XML 文字が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c307c-117">This includes reserved XML characters.</span></span> <span data-ttu-id="c307c-118">XML CDATA セクションは、シーケンスで終わる"] >"です。</span><span class="sxs-lookup"><span data-stu-id="c307c-118">The XML CDATA section ends with the sequence "]]>".</span></span> <span data-ttu-id="c307c-119">これは、次の点を意味します。</span><span class="sxs-lookup"><span data-stu-id="c307c-119">This implies the following points:</span></span>  
  
-   <span data-ttu-id="c307c-120">埋め込み式の区切り記号が有効な XML の CDATA コンテンツであるので、XML CDATA リテラルの埋め込み式を使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="c307c-120">You cannot use an embedded expression in an XML CDATA literal because the embedded expression delimiters are valid XML CDATA content.</span></span>  
  
-   <span data-ttu-id="c307c-121">XML CDATA セクションでは入れ子にできないため`content`値を含めることはできません"] >"です。</span><span class="sxs-lookup"><span data-stu-id="c307c-121">XML CDATA sections cannot be nested, because `content` cannot contain the value "]]>".</span></span>  
  
 <span data-ttu-id="c307c-122">リテラル XML CDATA を変数を割り当てたり、XML 要素リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="c307c-122">You can assign an XML CDATA literal to a variable, or include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c307c-123">XML リテラルでは、複数行にまたがることができますが、行継続文字を使用しません。</span><span class="sxs-lookup"><span data-stu-id="c307c-123">An XML literal can span multiple lines but does not use line continuation characters.</span></span> <span data-ttu-id="c307c-124">これにより、XML ドキュメントからコンテンツをコピーして、Visual Basic プログラムに直接貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="c307c-124">This enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="c307c-125">Visual Basic コンパイラでは、XML CDATA リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XCData.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="c307c-125">The Visual Basic compiler converts the XML CDATA literal to a call to the <xref:System.Xml.Linq.XCData.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c307c-126">例</span><span class="sxs-lookup"><span data-stu-id="c307c-126">Example</span></span>  
 <span data-ttu-id="c307c-127">次の例では、テキストを含む CDATA セクション"リテラルに含めることができる\<XML > タグ"です。</span><span class="sxs-lookup"><span data-stu-id="c307c-127">The following example creates a CDATA section that contains the text "Can contain literal \<XML> tags".</span></span>  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c307c-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="c307c-128">See Also</span></span>  
 <xref:System.Xml.Linq.XCData>  
 [<span data-ttu-id="c307c-129">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="c307c-129">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="c307c-130">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="c307c-130">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="c307c-131">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="c307c-131">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
