---
title: '&lt;返します&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
ms.openlocfilehash: effc55bd65ae6c54575b7931529499505a9523cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="0ab9c-102">&lt;返します&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ab9c-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="0ab9c-103">プロパティまたは関数の戻り値を指定します。</span><span class="sxs-lookup"><span data-stu-id="0ab9c-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ab9c-104">構文</span><span class="sxs-lookup"><span data-stu-id="0ab9c-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ab9c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0ab9c-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="0ab9c-106">戻り値の説明。</span><span class="sxs-lookup"><span data-stu-id="0ab9c-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ab9c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="0ab9c-107">Remarks</span></span>  
 <span data-ttu-id="0ab9c-108">使用して、`<returns>`タグを戻り値を記述するメソッドの宣言をコメントにします。</span><span class="sxs-lookup"><span data-stu-id="0ab9c-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="0ab9c-109">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="0ab9c-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ab9c-110">例</span><span class="sxs-lookup"><span data-stu-id="0ab9c-110">Example</span></span>  
 <span data-ttu-id="0ab9c-111">この例では、`<returns>`何かを説明するタグ、`DoesRecordExist`関数が返される。</span><span class="sxs-lookup"><span data-stu-id="0ab9c-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0ab9c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ab9c-112">See Also</span></span>  
 [<span data-ttu-id="0ab9c-113">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="0ab9c-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
