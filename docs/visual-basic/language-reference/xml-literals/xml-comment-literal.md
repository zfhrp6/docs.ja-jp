---
title: "XML コメント リテラル (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralComment
dev_langs:
- VB
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
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
ms.openlocfilehash: ab896399b664c658710c24d9799218ff3d81aecc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="xml-comment-literal-visual-basic"></a><span data-ttu-id="11561-102">XML コメント リテラル (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11561-102">XML Comment Literal (Visual Basic)</span></span>
<span data-ttu-id="11561-103">リテラルを表す、<xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment>。</span><span class="sxs-lookup"><span data-stu-id="11561-103">A literal representing an <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11561-104">構文</span><span class="sxs-lookup"><span data-stu-id="11561-104">Syntax</span></span>  
  
```  
<!-- content -->  
```  
  
## <a name="parts"></a><span data-ttu-id="11561-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="11561-105">Parts</span></span>  
  
|<span data-ttu-id="11561-106">用語</span><span class="sxs-lookup"><span data-stu-id="11561-106">Term</span></span>|<span data-ttu-id="11561-107">定義</span><span class="sxs-lookup"><span data-stu-id="11561-107">Definition</span></span>|  
|---|---|  
|`<!--`|<span data-ttu-id="11561-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="11561-108">Required.</span></span> <span data-ttu-id="11561-109">XML コメントの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="11561-109">Denotes the start of the XML comment.</span></span>|  
|`content`|<span data-ttu-id="11561-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="11561-110">Required.</span></span> <span data-ttu-id="11561-111">XML コメントに表示されるテキストです。</span><span class="sxs-lookup"><span data-stu-id="11561-111">Text to appear in the XML comment.</span></span> <span data-ttu-id="11561-112">一連の&2; つのハイフン (-) または終了タグの横にあるハイフンを使用して end を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="11561-112">Cannot contain a series of two hyphens (--) or end with a hyphen adjacent to the closing tag.</span></span>|  
|`-->`|<span data-ttu-id="11561-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="11561-113">Required.</span></span> <span data-ttu-id="11561-114">XML コメントの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="11561-114">Denotes the end of the XML comment.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="11561-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="11561-115">Return Value</span></span>  
 <span data-ttu-id="11561-116"><xref:System.Xml.Linq.XComment>オブジェクト</xref:System.Xml.Linq.XComment>。</span><span class="sxs-lookup"><span data-stu-id="11561-116">An <xref:System.Xml.Linq.XComment> object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11561-117">コメント</span><span class="sxs-lookup"><span data-stu-id="11561-117">Remarks</span></span>  
 <span data-ttu-id="11561-118">ドキュメントの内容を含まない XML コメント リテラルドキュメントに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="11561-118">XML comment literals do not contain document content; they contain information about the document.</span></span> <span data-ttu-id="11561-119">XML コメントのセクションでは、「-->」シーケンスで終了します。</span><span class="sxs-lookup"><span data-stu-id="11561-119">The XML comment section ends with the sequence "-->".</span></span> <span data-ttu-id="11561-120">これは、次の点を意味します。</span><span class="sxs-lookup"><span data-stu-id="11561-120">This implies the following points:</span></span>  
  
-   <span data-ttu-id="11561-121">組み込み式の区切り記号が有効な XML コメントの内容であるので、XML コメント リテラルで、組み込み式を使用できません。</span><span class="sxs-lookup"><span data-stu-id="11561-121">You cannot use an embedded expression in an XML comment literal because the embedded expression delimiters are valid XML comment content.</span></span>  
  
-   <span data-ttu-id="11561-122">XML コメントのセクションでは入れ子にできないため`content`「-->」の値を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="11561-122">XML comment sections cannot be nested, because `content` cannot contain the value "-->".</span></span>  
  
 <span data-ttu-id="11561-123">XML コメント リテラルは、変数に割り当てることができますか、XML 要素リテラルに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="11561-123">You can assign an XML comment literal to a variable, or you can include it in an XML element literal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11561-124">XML リテラルは、行継続文字を使用せず複数の行にまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="11561-124">An XML literal can span multiple lines without using line continuation characters.</span></span> <span data-ttu-id="11561-125">この機能を使用すると、XML ドキュメントからコンテンツをコピーして貼り付けに直接、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プログラムです。</span><span class="sxs-lookup"><span data-stu-id="11561-125">This feature enables you to copy content from an XML document and paste it directly into a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program.</span></span>  
  
 <span data-ttu-id="11561-126">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラでは、XML コメント リテラルを変換への呼び出しに、<xref:System.Xml.Linq.XComment.%23ctor%2A>コンス トラクター</xref:System.Xml.Linq.XComment.%23ctor%2A> 。</span><span class="sxs-lookup"><span data-stu-id="11561-126">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts the XML comment literal to a call to the <xref:System.Xml.Linq.XComment.%23ctor%2A> constructor.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11561-127">例</span><span class="sxs-lookup"><span data-stu-id="11561-127">Example</span></span>  
 <span data-ttu-id="11561-128">次の例では、"This is コメント"テキストを表す XML コメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="11561-128">The following example creates an XML comment that contains the text "This is a comment".</span></span>  
  
 <span data-ttu-id="11561-129">[!code-vb[VbXMLSamples&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="11561-129">[!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11561-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="11561-130">See Also</span></span>  
 <span data-ttu-id="11561-131"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="11561-131"><xref:System.Xml.Linq.XComment></span></span>   
<span data-ttu-id="11561-132"> [XML 要素リテラル](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="11561-132"> [XML Element Literal](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="11561-133"> [XML リテラル](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="11561-133"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="11561-134"> [Visual Basic で XML を作成します。](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span><span class="sxs-lookup"><span data-stu-id="11561-134"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)</span></span>
