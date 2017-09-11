---
title: "#<a name=\"endif-c-reference\"></a>endif (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#endif'
dev_langs:
- CSharp
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 9
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
ms.openlocfilehash: e4c37657a1ca81b7e5403e58123cf630a224b8ec
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="endif-c-reference"></a><span data-ttu-id="9141c-102">#endif (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9141c-102">#endif (C# Reference)</span></span>
<span data-ttu-id="9141c-103">`#endif` は [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)ディレクティブで始まる、条件付きディレクティブの終了を指定します。</span><span class="sxs-lookup"><span data-stu-id="9141c-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="9141c-104">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9141c-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="9141c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="9141c-105">Remarks</span></span>  
 <span data-ttu-id="9141c-106">`#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9141c-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="9141c-107">`#endif` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9141c-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9141c-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="9141c-108">See Also</span></span>  
 <span data-ttu-id="9141c-109">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9141c-109">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9141c-110">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9141c-110">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="9141c-111">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="9141c-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

