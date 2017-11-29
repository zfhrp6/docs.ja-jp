---
title: "&lt;remarks&gt; (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 882bf54988a9ce3120d884df8f29483aba1a0fd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltremarksgt-c-programming-guide"></a><span data-ttu-id="c88a0-102">&lt;remarks&gt; (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c88a0-102">&lt;remarks&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c88a0-103">構文</span><span class="sxs-lookup"><span data-stu-id="c88a0-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c88a0-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c88a0-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="c88a0-105">メンバーの説明。</span><span class="sxs-lookup"><span data-stu-id="c88a0-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c88a0-106">コメント</span><span class="sxs-lookup"><span data-stu-id="c88a0-106">Remarks</span></span>  
 <span data-ttu-id="c88a0-107">\<remarks> タグを使用して、型の情報を追加し、[\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) で指定された情報を補足します。</span><span class="sxs-lookup"><span data-stu-id="c88a0-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md).</span></span> <span data-ttu-id="c88a0-108">この情報はオブジェクト ブラウザー ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c88a0-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="c88a0-109">コンパイル時に [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="c88a0-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c88a0-110">例</span><span class="sxs-lookup"><span data-stu-id="c88a0-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c88a0-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c88a0-111">See Also</span></span>  
 [<span data-ttu-id="c88a0-112">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c88a0-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c88a0-113">ドキュメント コメントとして推奨されるタグ</span><span class="sxs-lookup"><span data-stu-id="c88a0-113">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
