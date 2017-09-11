---
title: "方法 : ポインターのインクリメントとデクリメント (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
caps.latest.revision: 20
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
ms.openlocfilehash: b474249ed9f7778e44981b292d51f29f46bc420d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="47ea5-102">方法 : ポインターのインクリメントとデクリメント (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="47ea5-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="47ea5-103">pointer-type* 型のポインターの [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) でポインターの位置を変更するには、インクリメント演算子 (`++`) とデクリメント演算子 (`--`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="47ea5-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type*.</span></span> <span data-ttu-id="47ea5-104">インクリメント式とデクリメント式には、次の書式を使用します。</span><span class="sxs-lookup"><span data-stu-id="47ea5-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="47ea5-105">インクリメント演算子とデクリメント演算子は、`void*` 以外のすべての型のポインターに適用できます。</span><span class="sxs-lookup"><span data-stu-id="47ea5-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="47ea5-106">`pointer-type` 型のポインターにインクリメント演算子を適用すると、ポインター変数に格納されているアドレスに [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) が加算されます。</span><span class="sxs-lookup"><span data-stu-id="47ea5-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="47ea5-107">`pointer-type` 型のポインターにデクリメント演算子を適用すると、ポインター変数に格納されているアドレスから `sizeof` (`pointer-type`) が減算されます。</span><span class="sxs-lookup"><span data-stu-id="47ea5-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="47ea5-108">演算がポインターのドメインをオーバーフローしても例外は生成されません。生じる結果は実装によって異なります。</span><span class="sxs-lookup"><span data-stu-id="47ea5-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47ea5-109">例</span><span class="sxs-lookup"><span data-stu-id="47ea5-109">Example</span></span>  
 <span data-ttu-id="47ea5-110">この例では、ポインターを `int` のサイズだけインクリメントして、配列をステップ実行します。</span><span class="sxs-lookup"><span data-stu-id="47ea5-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="47ea5-111">ステップごとに、配列要素のアドレスと内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="47ea5-111">With each step, you display the address and the content of the array element.</span></span>  
  
 <span data-ttu-id="47ea5-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="47ea5-112">[!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]</span></span>  
  
 <span data-ttu-id="47ea5-113">[!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="47ea5-113">[!code-cs[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]</span></span>  
  
 <span data-ttu-id="47ea5-114">**Value:0 @ Address:12860272**</span><span class="sxs-lookup"><span data-stu-id="47ea5-114">**Value:0 @ Address:12860272**</span></span>  
<span data-ttu-id="47ea5-115">**Value:1 @ Address:12860276**</span><span class="sxs-lookup"><span data-stu-id="47ea5-115">**Value:1 @ Address:12860276**</span></span>  
<span data-ttu-id="47ea5-116">**Value:2 @ Address:12860280**</span><span class="sxs-lookup"><span data-stu-id="47ea5-116">**Value:2 @ Address:12860280**</span></span>  
<span data-ttu-id="47ea5-117">**Value:3 @ Address:12860284**</span><span class="sxs-lookup"><span data-stu-id="47ea5-117">**Value:3 @ Address:12860284**</span></span>  
<span data-ttu-id="47ea5-118">**Value:4 @ Address:12860288**</span><span class="sxs-lookup"><span data-stu-id="47ea5-118">**Value:4 @ Address:12860288**</span></span>   
## <a name="see-also"></a><span data-ttu-id="47ea5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="47ea5-119">See Also</span></span>  
 <span data-ttu-id="47ea5-120">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="47ea5-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="47ea5-121">[ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="47ea5-121">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="47ea5-122">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="47ea5-122">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="47ea5-123">[ポインターの操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span><span class="sxs-lookup"><span data-stu-id="47ea5-123">[Manipulating Pointers](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span></span>  
 <span data-ttu-id="47ea5-124">[ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="47ea5-124">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="47ea5-125">[型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="47ea5-125">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="47ea5-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="47ea5-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="47ea5-127">[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="47ea5-127">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="47ea5-128">stackalloc</span><span class="sxs-lookup"><span data-stu-id="47ea5-128">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

