---
title: '#endif (C# リファレンス)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d7e68dd20d914052c3fe5cabcb83abdae100465c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="endif-c-reference"></a><span data-ttu-id="e1f13-102">#endif (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e1f13-102">#endif (C# Reference)</span></span>
<span data-ttu-id="e1f13-103">`#endif` は [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)ディレクティブで始まる、条件付きディレクティブの終了を指定します。</span><span class="sxs-lookup"><span data-stu-id="e1f13-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="e1f13-104">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e1f13-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="e1f13-105">コメント</span><span class="sxs-lookup"><span data-stu-id="e1f13-105">Remarks</span></span>  
 <span data-ttu-id="e1f13-106">`#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1f13-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="e1f13-107">`#endif` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e1f13-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f13-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1f13-108">See Also</span></span>  
 [<span data-ttu-id="e1f13-109">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="e1f13-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e1f13-110">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e1f13-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e1f13-111">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="e1f13-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
