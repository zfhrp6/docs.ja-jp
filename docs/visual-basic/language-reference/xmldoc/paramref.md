---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 763e311dfb46ceeed358c3b3bebd6212d3e2489c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598663"
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="adb67-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adb67-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="adb67-103">単語をパラメーターとして書式設定します。</span><span class="sxs-lookup"><span data-stu-id="adb67-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb67-104">構文</span><span class="sxs-lookup"><span data-stu-id="adb67-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="adb67-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="adb67-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="adb67-106">参照されるパラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="adb67-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="adb67-107">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="adb67-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adb67-108">コメント</span><span class="sxs-lookup"><span data-stu-id="adb67-108">Remarks</span></span>  
 <span data-ttu-id="adb67-109">`<paramref>`タグを使用する単語がパラメーターであることを示します。</span><span class="sxs-lookup"><span data-stu-id="adb67-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="adb67-110">XML ファイルを処理することで、このパラメーターに対して異なる書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="adb67-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="adb67-111">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="adb67-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adb67-112">例</span><span class="sxs-lookup"><span data-stu-id="adb67-112">Example</span></span>  
 <span data-ttu-id="adb67-113">この例では、`<paramref>`タグを参照する、`id`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="adb67-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="adb67-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="adb67-114">See Also</span></span>  
 [<span data-ttu-id="adb67-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="adb67-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
