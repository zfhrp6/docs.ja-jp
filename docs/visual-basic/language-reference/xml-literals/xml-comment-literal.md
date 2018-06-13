---
title: XML コメント リテラル (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 60c354215c627683fd6c69d9ca66fc115c26ccda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603939"
---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="1d655-102">XML コメント リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d655-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="1d655-103">リテラルを表す、<xref:System.Xml.Linq.XComment>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1d655-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d655-104">構文</span><span class="sxs-lookup"><span data-stu-id="1d655-104">Syntax</span></span>  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="1d655-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="1d655-105">Parts</span></span>  
  
|<span data-ttu-id="1d655-106">用語</span><span class="sxs-lookup"><span data-stu-id="1d655-106">Term</span></span>|<span data-ttu-id="1d655-107">定義</span><span class="sxs-lookup"><span data-stu-id="1d655-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="1d655-108">必須。</span><span class="sxs-lookup"><span data-stu-id="1d655-108">Required.</span></span> <span data-ttu-id="1d655-109">XML コメントの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="1d655-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="1d655-110">必須。</span><span class="sxs-lookup"><span data-stu-id="1d655-110">Required.</span></span> <span data-ttu-id="1d655-111">XML コメントに表示されるテキストです。</span><span class="sxs-lookup"><span data-stu-id="1d655-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="1d655-112">2 つのハイフン (-) または終了タグの横にあるハイフンで end の系列を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="1d655-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="1d655-113">必須。</span><span class="sxs-lookup"><span data-stu-id="1d655-113">Required.</span></span> <span data-ttu-id="1d655-114">XML コメントの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="1d655-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="1d655-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="1d655-115">Return Value</span></span>  
 <span data-ttu-id="1d655-116"><xref:System.Xml.Linq.XComment> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="1d655-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d655-117">コメント</span><span class="sxs-lookup"><span data-stu-id="1d655-117">Remarks</span></span>  
 <span data-ttu-id="1d655-118">XML コメント リテラルにはドキュメントの内容が含まれていませんドキュメントに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d655-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="1d655-119">XML コメントのセクションでは、シーケンス「:」で終了します。</span><span class="sxs-lookup"><span data-stu-id="1d655-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="1d655-120">これは、次の点を意味します。</span><span class="sxs-lookup"><span data-stu-id="1d655-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="1d655-121">埋め込み式の区切り記号が有効な XML コメントのコンテンツであるので、XML コメント リテラルの埋め込み式を使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="1d655-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="1d655-122">XML コメントのセクションでは入れ子にできないため`content`"-->"の値を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="1d655-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="1d655-123">XML コメント リテラルは、変数に割り当てることができますか、XML 要素リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1d655-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d655-124">XML リテラルは、行継続文字を使用せず複数行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="1d655-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="1d655-125">この機能を使用すると、XML ドキュメントの内容をコピーし、Visual Basic プログラムに直接貼り付けることができます。</span><span class="sxs-lookup"><span data-stu-id="1d655-125">This feature enables you to copy content from an XML document and paste it directly into a Visual Basic program.</span></span>  
  
 <span data-ttu-id="1d655-126">Visual Basic コンパイラでは、XML コメント リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XComment.%23ctor%2A>コンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="1d655-126">The Visual Basic compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d655-127">例</span><span class="sxs-lookup"><span data-stu-id="1d655-127">Example</span></span>  
 <span data-ttu-id="1d655-128">次の例では、「これは、コメント」テキストを含む XML コメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="1d655-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d655-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d655-129">See Also</span></span>  
 <xref:System.Xml.Linq.XComment>  
 [<span data-ttu-id="1d655-130">XML 要素リテラル</span><span class="sxs-lookup"><span data-stu-id="1d655-130">XML Element Literal</span></span>](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="1d655-131">XML リテラル</span><span class="sxs-lookup"><span data-stu-id="1d655-131">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="1d655-132">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="1d655-132">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
