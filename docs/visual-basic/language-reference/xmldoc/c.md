---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e57cae8fd4b93fee59992d717135ad7d3d78be5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="17b73-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17b73-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="17b73-103">説明内のテキストがコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="17b73-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17b73-104">構文</span><span class="sxs-lookup"><span data-stu-id="17b73-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17b73-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17b73-105">Parameters</span></span>  
  
|<span data-ttu-id="17b73-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17b73-106">Parameter</span></span>|<span data-ttu-id="17b73-107">説明</span><span class="sxs-lookup"><span data-stu-id="17b73-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="17b73-108">コードとして指定するテキストです。</span><span class="sxs-lookup"><span data-stu-id="17b73-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17b73-109">コメント</span><span class="sxs-lookup"><span data-stu-id="17b73-109">Remarks</span></span>  
 <span data-ttu-id="17b73-110">`<c>`タグを使用する方法を示す説明内のテキストは、コードとしてマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="17b73-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="17b73-111">複数行をコードとして指定する場合は、[\<code>](../../../visual-basic/language-reference/xmldoc/code.md) タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="17b73-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="17b73-112">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="17b73-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17b73-113">例</span><span class="sxs-lookup"><span data-stu-id="17b73-113">Example</span></span>  
 <span data-ttu-id="17b73-114">この例では、`<c>`ことを示す概要 セクションにタグ`Counter`コードに示します。</span><span class="sxs-lookup"><span data-stu-id="17b73-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="17b73-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="17b73-115">See Also</span></span>  
 [<span data-ttu-id="17b73-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="17b73-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
