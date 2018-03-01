---
title: "#else (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c3468d35a6e45c06f46fe8671708ce01a3cc7b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="else-c-reference"></a><span data-ttu-id="52abc-102">#else (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="52abc-102">#else (C# Reference)</span></span>
<span data-ttu-id="52abc-103">`#else` を使用すると、複合条件付きディレクティブを作成できるため、先行する [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) または (省略可能な) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) ディレクティブの式がいずれも `true` にならない場合は、コンパイラが `#else` と以降の `#endif` の間のすべてのコードを評価します。</span><span class="sxs-lookup"><span data-stu-id="52abc-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52abc-104">コメント</span><span class="sxs-lookup"><span data-stu-id="52abc-104">Remarks</span></span>  
 <span data-ttu-id="52abc-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) が、`#else` の後の次のプリプロセッサ ディレクティブになる必要があります。</span><span class="sxs-lookup"><span data-stu-id="52abc-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="52abc-106">`#else` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52abc-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52abc-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="52abc-107">See Also</span></span>  
 [<span data-ttu-id="52abc-108">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="52abc-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="52abc-109">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="52abc-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="52abc-110">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="52abc-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
