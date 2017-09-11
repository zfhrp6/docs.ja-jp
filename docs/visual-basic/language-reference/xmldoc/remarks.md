---
title: "&lt;「解説」&gt; (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: c1b2c48dc3247935f703ff4107f29829c494a305
ms.contentlocale: ja-jp
ms.lasthandoff: 06/01/2017

---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="2aa6f-102">&lt;「解説」&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2aa6f-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="2aa6f-103">メンバーの「解説」セクションをを指定します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aa6f-104">構文</span><span class="sxs-lookup"><span data-stu-id="2aa6f-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2aa6f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2aa6f-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="2aa6f-106">メンバーの説明。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2aa6f-107">コメント</span><span class="sxs-lookup"><span data-stu-id="2aa6f-107">Remarks</span></span>  
 <span data-ttu-id="2aa6f-108">使用して、`<remarks>`で指定された情報を補足すると、型に関する情報を追加するタグ[\<概要 >](../../../visual-basic/language-reference/xmldoc/summary.md)します。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="2aa6f-109">この情報は、オブジェクト ブラウザーで表示されます。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="2aa6f-110">オブジェクト ブラウザーの詳細については、次を参照してください。[コードの構造を表示する](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)です。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-110">For information about the Object Browser, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="2aa6f-111">使用してコンパイル[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)してドキュメント コメントをファイルにします。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aa6f-112">例</span><span class="sxs-lookup"><span data-stu-id="2aa6f-112">Example</span></span>  
 <span data-ttu-id="2aa6f-113">この例では、`<remarks>`何かを説明するタグ、`UpdateRecord`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="2aa6f-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 <span data-ttu-id="2aa6f-114">[!code-vb[VbVbcnXmlDocComments&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2aa6f-114">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa6f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="2aa6f-115">See Also</span></span>  
 [<span data-ttu-id="2aa6f-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="2aa6f-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
