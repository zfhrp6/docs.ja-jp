---
title: '&lt;「解説」&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 6e4e280760b9238fdc403ac5fe586743334e4c69
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598198"
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="a5aa9-102">&lt;「解説」&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5aa9-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="a5aa9-103">メンバーの「解説」セクションをを指定します。</span><span class="sxs-lookup"><span data-stu-id="a5aa9-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5aa9-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5aa9-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a5aa9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a5aa9-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="a5aa9-106">メンバーの説明。</span><span class="sxs-lookup"><span data-stu-id="a5aa9-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5aa9-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a5aa9-107">Remarks</span></span>  
 <span data-ttu-id="a5aa9-108">使用して、`<remarks>`で指定された情報を補足する型に関する情報を追加するタグ[\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)です。</span><span class="sxs-lookup"><span data-stu-id="a5aa9-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="a5aa9-109">この情報は、オブジェクト ブラウザーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5aa9-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="a5aa9-110">オブジェクト ブラウザーの詳細については、次を参照してください。[コードの構造を表示する](/visualstudio/ide/viewing-the-structure-of-code)です。</span><span class="sxs-lookup"><span data-stu-id="a5aa9-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="a5aa9-111">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="a5aa9-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5aa9-112">例</span><span class="sxs-lookup"><span data-stu-id="a5aa9-112">Example</span></span>  
 <span data-ttu-id="a5aa9-113">この例では、`<remarks>`何かを説明するタグ、`UpdateRecord`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a5aa9-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a5aa9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5aa9-114">See Also</span></span>  
 [<span data-ttu-id="a5aa9-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="a5aa9-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
