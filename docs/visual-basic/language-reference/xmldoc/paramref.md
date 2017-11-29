---
title: '&lt;paramref&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3bf3d4f04997a03f442cf7fd2a1586604198d3fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="5762f-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5762f-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="5762f-103">単語をパラメーターとして書式設定します。</span><span class="sxs-lookup"><span data-stu-id="5762f-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5762f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5762f-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5762f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5762f-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5762f-106">参照されるパラメーターの名前です。</span><span class="sxs-lookup"><span data-stu-id="5762f-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="5762f-107">名前は二重引用符 (" ") で囲みます。</span><span class="sxs-lookup"><span data-stu-id="5762f-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5762f-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5762f-108">Remarks</span></span>  
 <span data-ttu-id="5762f-109">`<paramref>`タグを使用する単語がパラメーターであることを示します。</span><span class="sxs-lookup"><span data-stu-id="5762f-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="5762f-110">XML ファイルを処理することで、このパラメーターに対して異なる書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="5762f-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="5762f-111">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="5762f-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5762f-112">例</span><span class="sxs-lookup"><span data-stu-id="5762f-112">Example</span></span>  
 <span data-ttu-id="5762f-113">この例では、`<paramref>`タグを参照する、`id`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="5762f-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5762f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5762f-114">See Also</span></span>  
 [<span data-ttu-id="5762f-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="5762f-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
