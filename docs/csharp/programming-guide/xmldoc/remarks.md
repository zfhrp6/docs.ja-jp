---
title: "&lt;remarks&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- remarks
- <remarks>
dev_langs:
- CSharp
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cd11865fb0d4c8d21294107542fe39ad7e2b690a
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="ltremarksgt-c-programming-guide"></a><span data-ttu-id="d50a6-102">&lt;remarks&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="d50a6-102">&lt;remarks&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="d50a6-103">構文</span><span class="sxs-lookup"><span data-stu-id="d50a6-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d50a6-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d50a6-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="d50a6-105">メンバーの説明。</span><span class="sxs-lookup"><span data-stu-id="d50a6-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d50a6-106">コメント</span><span class="sxs-lookup"><span data-stu-id="d50a6-106">Remarks</span></span>  
 <span data-ttu-id="d50a6-107">\<remarks> タグを使用して、型の情報を追加し、[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) で指定された情報を補足します。</span><span class="sxs-lookup"><span data-stu-id="d50a6-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md).</span></span> <span data-ttu-id="d50a6-108">この情報はオブジェクト ブラウザー ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="d50a6-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="d50a6-109">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="d50a6-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d50a6-110">例</span><span class="sxs-lookup"><span data-stu-id="d50a6-110">Example</span></span>  
 <span data-ttu-id="d50a6-111">[!code-cs[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d50a6-111">[!code-cs[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d50a6-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d50a6-112">See Also</span></span>  
 <span data-ttu-id="d50a6-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d50a6-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d50a6-114">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="d50a6-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

