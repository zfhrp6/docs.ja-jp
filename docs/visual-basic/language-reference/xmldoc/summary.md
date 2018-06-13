---
title: '&lt;概要&gt;(Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: cf320b61a2ca1c54b22e3c3d31ae51d003366efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602653"
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="f8b31-102">&lt;概要&gt;(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8b31-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="f8b31-103">メンバーの概要を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8b31-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8b31-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8b31-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8b31-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8b31-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="f8b31-106">オブジェクトの概要。</span><span class="sxs-lookup"><span data-stu-id="f8b31-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8b31-107">コメント</span><span class="sxs-lookup"><span data-stu-id="f8b31-107">Remarks</span></span>  
 <span data-ttu-id="f8b31-108">使用して、`<summary>`型または型のメンバーを記述するタグです。</span><span class="sxs-lookup"><span data-stu-id="f8b31-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="f8b31-109">型の説明に補足情報を追加するには、[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8b31-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="f8b31-110">テキスト、`<summary>`タグは、IntelliSense、内の型に関する情報の唯一のソースとオブジェクト ブラウザーにも表示されます。</span><span class="sxs-lookup"><span data-stu-id="f8b31-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="f8b31-111">オブジェクト ブラウザーの詳細については、次を参照してください。[コードの構造を表示する](/visualstudio/ide/viewing-the-structure-of-code)です。</span><span class="sxs-lookup"><span data-stu-id="f8b31-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="f8b31-112">コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="f8b31-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8b31-113">例</span><span class="sxs-lookup"><span data-stu-id="f8b31-113">Example</span></span>  
 <span data-ttu-id="f8b31-114">この例では、`<summary>`を記述するタグ、`ResetCounter`メソッドおよび`Counter`プロパティです。</span><span class="sxs-lookup"><span data-stu-id="f8b31-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f8b31-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8b31-115">See Also</span></span>  
 [<span data-ttu-id="f8b31-116">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="f8b31-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
