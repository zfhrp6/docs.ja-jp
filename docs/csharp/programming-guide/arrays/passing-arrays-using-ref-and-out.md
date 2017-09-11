---
title: "ref と out を使用した配列の引き渡し (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 16
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
ms.openlocfilehash: 58fc359881295a9e6627ac1269ef17aa298009c7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="cac08-102">ref と out を使用した配列の引き渡し (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="cac08-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="cac08-103">すべての [out](../../../csharp/language-reference/keywords/out.md) パラメーターと同じように、配列型の `out` パラメーターも使用する前に代入される必要があります。つまり、呼び出される側で代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac08-103">Like all [out](../../../csharp/language-reference/keywords/out.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="cac08-104">例:</span><span class="sxs-lookup"><span data-stu-id="cac08-104">For example:</span></span>  
  
 <span data-ttu-id="cac08-105">[!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cac08-105">[!code-cs[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]</span></span>  
  
 <span data-ttu-id="cac08-106">すべての [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターと同じように、配列型の `ref` パラメーターも、呼び出し側で明示的に代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cac08-106">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="cac08-107">したがって、呼び出される側で明示的に代入する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cac08-107">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="cac08-108">配列型の `ref` パラメーターは、呼び出しの結果として変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cac08-108">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="cac08-109">たとえば、配列に [null](../../../csharp/language-reference/keywords/null.md) 値が代入されたり、別の配列で初期化されたりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="cac08-109">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="cac08-110">例:</span><span class="sxs-lookup"><span data-stu-id="cac08-110">For example:</span></span>  
  
 <span data-ttu-id="cac08-111">[!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="cac08-111">[!code-cs[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]</span></span>  
  
 <span data-ttu-id="cac08-112">次の 2 つの例は、メソッドに配列を渡すときに使われる `out` と `ref` の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="cac08-112">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cac08-113">例</span><span class="sxs-lookup"><span data-stu-id="cac08-113">Example</span></span>  
 <span data-ttu-id="cac08-114">この例では、配列 `theArray` は呼び出し元 (`Main` メソッド) で宣言されて、`FillArray` メソッドで初期化されます。</span><span class="sxs-lookup"><span data-stu-id="cac08-114">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="cac08-115">その後、配列要素は呼び出し元に返されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac08-115">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 <span data-ttu-id="cac08-116">[!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="cac08-116">[!code-cs[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="cac08-117">例</span><span class="sxs-lookup"><span data-stu-id="cac08-117">Example</span></span>  
 <span data-ttu-id="cac08-118">この例では、配列 `theArray` は呼び出し元 (`Main` メソッド) で初期化された後、`FillArray` パラメーターを使って `ref` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="cac08-118">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="cac08-119">一部の配列要素は、`FillArray` メソッドの中で変更されます。</span><span class="sxs-lookup"><span data-stu-id="cac08-119">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="cac08-120">その後、配列要素は呼び出し元に返されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="cac08-120">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 <span data-ttu-id="cac08-121">[!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="cac08-121">[!code-cs[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac08-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="cac08-122">See Also</span></span>  
 <span data-ttu-id="cac08-123">[ref](../../../csharp/language-reference/keywords/ref.md) </span><span class="sxs-lookup"><span data-stu-id="cac08-123">[ref](../../../csharp/language-reference/keywords/ref.md) </span></span>  
 <span data-ttu-id="cac08-124">[out パラメーター修飾子](../../../csharp/language-reference/keywords/out-parameter-modifier.md) </span><span class="sxs-lookup"><span data-stu-id="cac08-124">[out parameter modifier](../../../csharp/language-reference/keywords/out-parameter-modifier.md) </span></span>  
 <span data-ttu-id="cac08-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cac08-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cac08-126">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="cac08-126">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="cac08-127">[1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="cac08-127">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="cac08-128">[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="cac08-128">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="cac08-129">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="cac08-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

