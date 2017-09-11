---
title: "&lt;概要&gt;(Visual Basic) |Microsoft ドキュメント"
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
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
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
ms.openlocfilehash: 42321daf092c4b637d2f75fb7f6d7e95201791ba
ms.contentlocale: ja-jp
ms.lasthandoff: 06/01/2017

---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="bc8d4-102">&lt;概要&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc8d4-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="bc8d4-103">メンバーの概要を指定します。</span><span class="sxs-lookup"><span data-stu-id="bc8d4-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc8d4-104">構文</span><span class="sxs-lookup"><span data-stu-id="bc8d4-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc8d4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bc8d4-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="bc8d4-106">オブジェクトの概要です。</span><span class="sxs-lookup"><span data-stu-id="bc8d4-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc8d4-107">コメント</span><span class="sxs-lookup"><span data-stu-id="bc8d4-107">Remarks</span></span>  
 <span data-ttu-id="bc8d4-108">使用して、`<summary>`型または型のメンバーを記述するタグです。</span><span class="sxs-lookup"><span data-stu-id="bc8d4-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="bc8d4-109">使用[\<解説 >](../../../visual-basic/language-reference/xmldoc/remarks.md)型の説明に補足情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="bc8d4-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="bc8d4-110">テキストを`<summary>`タグは、IntelliSense の種類に関する情報の唯一のソースであり、オブジェクト ブラウザーでも表示されます。</span><span class="sxs-lookup"><span data-stu-id="bc8d4-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="bc8d4-111">オブジェクト ブラウザーの詳細については、次を参照してください。[コードの構造を表示する](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code)です。</span><span class="sxs-lookup"><span data-stu-id="bc8d4-111">For information about the Object Browser, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="bc8d4-112">使用してコンパイル[/doc](../../../visual-basic/reference/command-line-compiler/doc.md)してドキュメント コメントをファイルにします。</span><span class="sxs-lookup"><span data-stu-id="bc8d4-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc8d4-113">例</span><span class="sxs-lookup"><span data-stu-id="bc8d4-113">Example</span></span>  
 <span data-ttu-id="bc8d4-114">この例では、`<summary>`を記述するタグ、`ResetCounter`メソッドと`Counter`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="bc8d4-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 <span data-ttu-id="bc8d4-115">[!code-vb[VbVbcnXmlDocComments&#1;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="bc8d4-115">[!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8d4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bc8d4-116">See Also</span></span>  
 [<span data-ttu-id="bc8d4-117">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="bc8d4-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
