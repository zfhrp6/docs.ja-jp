---
title: "#<a name=\"else-c-reference\"></a>else (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#else'
dev_langs:
- CSharp
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 11
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
ms.openlocfilehash: c4b593c757180af22ce512be624e9ac94a2e1bc6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="else-c-reference"></a><span data-ttu-id="9a70f-102">#else (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9a70f-102">#else (C# Reference)</span></span>
<span data-ttu-id="9a70f-103">`#else` を使用すると、複合条件付きディレクティブを作成できるため、先行する [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) または (省略可能な) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) ディレクティブの式がいずれも `true` にならない場合は、コンパイラが `#else` と以降の `#endif` の間のすべてのコードを評価します。</span><span class="sxs-lookup"><span data-stu-id="9a70f-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a70f-104">コメント</span><span class="sxs-lookup"><span data-stu-id="9a70f-104">Remarks</span></span>  
 <span data-ttu-id="9a70f-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) が、`#else` の後の次のプリプロセッサ ディレクティブになる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a70f-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="9a70f-106">`#else` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a70f-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a70f-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a70f-107">See Also</span></span>  
 <span data-ttu-id="9a70f-108">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a70f-108">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9a70f-109">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9a70f-109">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="9a70f-110">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="9a70f-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

