---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: cb80f4b39bee128790b311732adf1202dbbc6993
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601726"
---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="197a1-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="197a1-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="197a1-103">コンテンツが段落としてフォーマットされているを指定します。</span><span class="sxs-lookup"><span data-stu-id="197a1-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="197a1-104">構文</span><span class="sxs-lookup"><span data-stu-id="197a1-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="197a1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="197a1-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="197a1-106">段落のテキストです。</span><span class="sxs-lookup"><span data-stu-id="197a1-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="197a1-107">コメント</span><span class="sxs-lookup"><span data-stu-id="197a1-107">Remarks</span></span>  
 <span data-ttu-id="197a1-108">`<para>`タグをタグ内で使用するように[\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)、 [\<解説 >](../../../visual-basic/language-reference/xmldoc/remarks.md)、または[\<返します >](../../../visual-basic/language-reference/xmldoc/returns.md)、テキストに構造を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="197a1-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="197a1-109">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="197a1-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="197a1-110">例</span><span class="sxs-lookup"><span data-stu-id="197a1-110">Example</span></span>  
 <span data-ttu-id="197a1-111">この例では、`<para>`については、「解説」セクションに分割するタグ、 `UpdateRecord` 2 つの段落にメソッドです。</span><span class="sxs-lookup"><span data-stu-id="197a1-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="197a1-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="197a1-112">See Also</span></span>  
 [<span data-ttu-id="197a1-113">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="197a1-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
