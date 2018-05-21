---
title: '#else (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 662d19f38ce1f3a7a04c9abe27c1f217e3d848f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="else-c-reference"></a><span data-ttu-id="fd32d-102">#else (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="fd32d-102">#else (C# Reference)</span></span>
<span data-ttu-id="fd32d-103">`#else` を使用すると、複合条件付きディレクティブを作成できるため、先行する [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) または (省略可能な) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) ディレクティブの式がいずれも `true` にならない場合は、コンパイラが `#else` と以降の `#endif` の間のすべてのコードを評価します。</span><span class="sxs-lookup"><span data-stu-id="fd32d-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd32d-104">コメント</span><span class="sxs-lookup"><span data-stu-id="fd32d-104">Remarks</span></span>  
 <span data-ttu-id="fd32d-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) が、`#else` の後の次のプリプロセッサ ディレクティブになる必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd32d-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="fd32d-106">`#else` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd32d-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd32d-107">参照</span><span class="sxs-lookup"><span data-stu-id="fd32d-107">See Also</span></span>  
 [<span data-ttu-id="fd32d-108">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="fd32d-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fd32d-109">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fd32d-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fd32d-110">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="fd32d-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
