---
title: '&lt;例&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8c09ab934ee7457fdff39a63c58f2546cda4d643
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598551"
---
# <a name="ltexamplegt-visual-basic"></a><span data-ttu-id="a2f9b-102">&lt;例&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2f9b-102">&lt;example&gt; (Visual Basic)</span></span>
<span data-ttu-id="a2f9b-103">メンバーの例を指定します。</span><span class="sxs-lookup"><span data-stu-id="a2f9b-103">Specifies an example for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f9b-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2f9b-104">Syntax</span></span>  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2f9b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2f9b-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="a2f9b-106">コード例の説明です。</span><span class="sxs-lookup"><span data-stu-id="a2f9b-106">A description of the code sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2f9b-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a2f9b-107">Remarks</span></span>  
 <span data-ttu-id="a2f9b-108">`<example>`タグを使用して、メソッド、またはその他のライブラリ メンバーを使用する方法の例を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a2f9b-108">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="a2f9b-109">一般的に、[\<code>](../../../visual-basic/language-reference/xmldoc/code.md) タグが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2f9b-109">This commonly involves using the [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) tag.</span></span>  
  
 <span data-ttu-id="a2f9b-110">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="a2f9b-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2f9b-111">例</span><span class="sxs-lookup"><span data-stu-id="a2f9b-111">Example</span></span>  
 <span data-ttu-id="a2f9b-112">この例では、`<example>`タグを含める例を使用するために、`ID`フィールドです。</span><span class="sxs-lookup"><span data-stu-id="a2f9b-112">This example uses the `<example>` tag to include an example for using the `ID` field.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a2f9b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2f9b-113">See Also</span></span>  
 [<span data-ttu-id="a2f9b-114">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="a2f9b-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
