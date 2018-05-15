---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
ms.openlocfilehash: 76e0e8d4757f29bb5df82ea1482beff3dd43c0e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="e06f0-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e06f0-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="e06f0-103">型パラメーターの名前と説明を定義します。</span><span class="sxs-lookup"><span data-stu-id="e06f0-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06f0-104">構文</span><span class="sxs-lookup"><span data-stu-id="e06f0-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e06f0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e06f0-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e06f0-106">型パラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="e06f0-106">The name of the type parameter.</span></span> <span data-ttu-id="e06f0-107">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="e06f0-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="e06f0-108">型パラメーターの説明です。</span><span class="sxs-lookup"><span data-stu-id="e06f0-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e06f0-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e06f0-109">Remarks</span></span>  
 <span data-ttu-id="e06f0-110">使用して、`<typeparam>`型パラメーターのいずれかを記述するには、ジェネリック型またはジェネリック メンバー宣言のコメント内のタグ。</span><span class="sxs-lookup"><span data-stu-id="e06f0-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="e06f0-111">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="e06f0-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e06f0-112">例</span><span class="sxs-lookup"><span data-stu-id="e06f0-112">Example</span></span>  
 <span data-ttu-id="e06f0-113">この例では、`<typeparam>`を記述するタグ、`id`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="e06f0-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e06f0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e06f0-114">See Also</span></span>  
 [<span data-ttu-id="e06f0-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="e06f0-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
