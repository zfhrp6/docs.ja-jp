---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 556c00fa761a1bce5e922a304706c78893550901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599607"
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="5e8e1-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e8e1-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="5e8e1-103">説明内のテキストがコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="5e8e1-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e8e1-104">構文</span><span class="sxs-lookup"><span data-stu-id="5e8e1-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e8e1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5e8e1-105">Parameters</span></span>  
  
|<span data-ttu-id="5e8e1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5e8e1-106">Parameter</span></span>|<span data-ttu-id="5e8e1-107">説明</span><span class="sxs-lookup"><span data-stu-id="5e8e1-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="5e8e1-108">コードとして指定するテキストです。</span><span class="sxs-lookup"><span data-stu-id="5e8e1-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e8e1-109">コメント</span><span class="sxs-lookup"><span data-stu-id="5e8e1-109">Remarks</span></span>  
 <span data-ttu-id="5e8e1-110">`<c>`タグを使用する方法を示す説明内のテキストは、コードとしてマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e8e1-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="5e8e1-111">複数行をコードとして指定する場合は、[\<code>](../../../visual-basic/language-reference/xmldoc/code.md) タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="5e8e1-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="5e8e1-112">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="5e8e1-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e8e1-113">例</span><span class="sxs-lookup"><span data-stu-id="5e8e1-113">Example</span></span>  
 <span data-ttu-id="5e8e1-114">この例では、`<c>`ことを示す概要 セクションにタグ`Counter`コードに示します。</span><span class="sxs-lookup"><span data-stu-id="5e8e1-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5e8e1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e8e1-115">See Also</span></span>  
 [<span data-ttu-id="5e8e1-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="5e8e1-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
