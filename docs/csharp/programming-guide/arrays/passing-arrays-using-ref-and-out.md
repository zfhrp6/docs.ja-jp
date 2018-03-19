---
title: "ref と out を使用した配列の引き渡し (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f76f63aee0100c6af6bde73c8543b4e7136b1954
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="8c2cd-102">ref と out を使用した配列の引き渡し (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="8c2cd-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="8c2cd-103">すべての [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) パラメーターと同じように、配列型の `out` パラメーターも使用する前に代入される必要があります。つまり、呼び出される側で代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-103">Like all [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="8c2cd-104">例:</span><span class="sxs-lookup"><span data-stu-id="8c2cd-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="8c2cd-105">すべての [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターと同じように、配列型の `ref` パラメーターも、呼び出し側で明示的に代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="8c2cd-106">したがって、呼び出される側で明示的に代入する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="8c2cd-107">配列型の `ref` パラメーターは、呼び出しの結果として変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="8c2cd-108">たとえば、配列に [null](../../../csharp/language-reference/keywords/null.md) 値が代入されたり、別の配列で初期化されたりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="8c2cd-109">例:</span><span class="sxs-lookup"><span data-stu-id="8c2cd-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="8c2cd-110">次の 2 つの例は、メソッドに配列を渡すときに使われる `out` と `ref` の違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c2cd-111">例</span><span class="sxs-lookup"><span data-stu-id="8c2cd-111">Example</span></span>  
 <span data-ttu-id="8c2cd-112">この例では、配列 `theArray` は呼び出し元 (`Main` メソッド) で宣言されて、`FillArray` メソッドで初期化されます。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="8c2cd-113">その後、配列要素は呼び出し元に返されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="8c2cd-114">例</span><span class="sxs-lookup"><span data-stu-id="8c2cd-114">Example</span></span>  
 <span data-ttu-id="8c2cd-115">この例では、配列 `theArray` は呼び出し元 (`Main` メソッド) で初期化された後、`FillArray` パラメーターを使って `ref` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="8c2cd-116">一部の配列要素は、`FillArray` メソッドの中で変更されます。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="8c2cd-117">その後、配列要素は呼び出し元に返されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="8c2cd-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8c2cd-118">参照</span><span class="sxs-lookup"><span data-stu-id="8c2cd-118">See Also</span></span>  
 [<span data-ttu-id="8c2cd-119">ref</span><span class="sxs-lookup"><span data-stu-id="8c2cd-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="8c2cd-120">out パラメーター修飾子</span><span class="sxs-lookup"><span data-stu-id="8c2cd-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [<span data-ttu-id="8c2cd-121">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8c2cd-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8c2cd-122">配列</span><span class="sxs-lookup"><span data-stu-id="8c2cd-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="8c2cd-123">1 次元配列</span><span class="sxs-lookup"><span data-stu-id="8c2cd-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="8c2cd-124">多次元配列</span><span class="sxs-lookup"><span data-stu-id="8c2cd-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="8c2cd-125">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="8c2cd-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
