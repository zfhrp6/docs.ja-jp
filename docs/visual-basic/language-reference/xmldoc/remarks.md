---
title: "&lt;「解説」&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f70c2d7df190d2ff8187882a9176dbe98984296
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="82c65-102">&lt;「解説」&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82c65-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="82c65-103">メンバーの「解説」セクションをを指定します。</span><span class="sxs-lookup"><span data-stu-id="82c65-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c65-104">構文</span><span class="sxs-lookup"><span data-stu-id="82c65-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82c65-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82c65-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="82c65-106">メンバーの説明。</span><span class="sxs-lookup"><span data-stu-id="82c65-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82c65-107">コメント</span><span class="sxs-lookup"><span data-stu-id="82c65-107">Remarks</span></span>  
 <span data-ttu-id="82c65-108">使用して、`<remarks>`で指定された情報を補足する型に関する情報を追加するタグ[\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)です。</span><span class="sxs-lookup"><span data-stu-id="82c65-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="82c65-109">この情報は、オブジェクト ブラウザーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="82c65-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="82c65-110">オブジェクト ブラウザーの詳細については、次を参照してください。[コードの構造を表示する](/visualstudio/ide/viewing-the-structure-of-code)です。</span><span class="sxs-lookup"><span data-stu-id="82c65-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="82c65-111">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="82c65-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82c65-112">例</span><span class="sxs-lookup"><span data-stu-id="82c65-112">Example</span></span>  
 <span data-ttu-id="82c65-113">この例では、`<remarks>`何かを説明するタグ、`UpdateRecord`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="82c65-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="82c65-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="82c65-114">See Also</span></span>  
 [<span data-ttu-id="82c65-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="82c65-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
