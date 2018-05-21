---
title: '#endif (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 1686e706ce5cae3b2eaa28a7e1c89b5694b2be88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="endif-c-reference"></a><span data-ttu-id="b013d-102">#endif (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b013d-102">#endif (C# Reference)</span></span>
<span data-ttu-id="b013d-103">`#endif` は [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)ディレクティブで始まる、条件付きディレクティブの終了を指定します。</span><span class="sxs-lookup"><span data-stu-id="b013d-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="b013d-104">たとえば、オブジェクトに適用された</span><span class="sxs-lookup"><span data-stu-id="b013d-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="b013d-105">コメント</span><span class="sxs-lookup"><span data-stu-id="b013d-105">Remarks</span></span>  
 <span data-ttu-id="b013d-106">`#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b013d-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="b013d-107">`#endif` の使用例については、「[#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b013d-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b013d-108">参照</span><span class="sxs-lookup"><span data-stu-id="b013d-108">See Also</span></span>  
 [<span data-ttu-id="b013d-109">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b013d-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b013d-110">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b013d-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b013d-111">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="b013d-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
