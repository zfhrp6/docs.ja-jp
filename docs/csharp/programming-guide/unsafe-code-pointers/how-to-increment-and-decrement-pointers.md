---
title: '方法 : ポインターのインクリメントとデクリメント (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: e1c3ac12a126450781d0ce78e788f39c740b5279
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324286"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="b97ef-102">方法 : ポインターのインクリメントとデクリメント (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b97ef-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="b97ef-103">pointer-type\* 型のポインターの [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) でポインターの位置を変更するには、インクリメント演算子 (`++`) とデクリメント演算子 (`--`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="b97ef-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type\*.</span></span> <span data-ttu-id="b97ef-104">インクリメント式とデクリメント式には、次の書式を使用します。</span><span class="sxs-lookup"><span data-stu-id="b97ef-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="b97ef-105">インクリメント演算子とデクリメント演算子は、`void*` 以外のすべての型のポインターに適用できます。</span><span class="sxs-lookup"><span data-stu-id="b97ef-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="b97ef-106">`pointer-type` 型のポインターにインクリメント演算子を適用すると、ポインター変数に格納されているアドレスに [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) が加算されます。</span><span class="sxs-lookup"><span data-stu-id="b97ef-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="b97ef-107">`pointer-type` 型のポインターにデクリメント演算子を適用すると、ポインター変数に格納されているアドレスから `sizeof` (`pointer-type`) が減算されます。</span><span class="sxs-lookup"><span data-stu-id="b97ef-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="b97ef-108">演算がポインターのドメインをオーバーフローしても例外は生成されません。生じる結果は実装によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b97ef-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b97ef-109">例</span><span class="sxs-lookup"><span data-stu-id="b97ef-109">Example</span></span>  
 <span data-ttu-id="b97ef-110">この例では、ポインターを `int` のサイズだけインクリメントして、配列をステップ実行します。</span><span class="sxs-lookup"><span data-stu-id="b97ef-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="b97ef-111">ステップごとに、配列要素のアドレスと内容を表示します。</span><span class="sxs-lookup"><span data-stu-id="b97ef-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
 <span data-ttu-id="b97ef-112">**Value:0 @ Address:12860272**</span><span class="sxs-lookup"><span data-stu-id="b97ef-112">**Value:0 @ Address:12860272**</span></span>  
<span data-ttu-id="b97ef-113">**Value:1 @ Address:12860276**</span><span class="sxs-lookup"><span data-stu-id="b97ef-113">**Value:1 @ Address:12860276**</span></span>  
<span data-ttu-id="b97ef-114">**Value:2 @ Address:12860280**</span><span class="sxs-lookup"><span data-stu-id="b97ef-114">**Value:2 @ Address:12860280**</span></span>  
<span data-ttu-id="b97ef-115">**Value:3 @ Address:12860284**</span><span class="sxs-lookup"><span data-stu-id="b97ef-115">**Value:3 @ Address:12860284**</span></span>  
<span data-ttu-id="b97ef-116">**Value:4 @ Address:12860288**</span><span class="sxs-lookup"><span data-stu-id="b97ef-116">**Value:4 @ Address:12860288**</span></span>   
## <a name="see-also"></a><span data-ttu-id="b97ef-117">参照</span><span class="sxs-lookup"><span data-stu-id="b97ef-117">See Also</span></span>  
 [<span data-ttu-id="b97ef-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b97ef-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b97ef-119">ポインター式</span><span class="sxs-lookup"><span data-stu-id="b97ef-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="b97ef-120">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="b97ef-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="b97ef-121">ポインターの操作</span><span class="sxs-lookup"><span data-stu-id="b97ef-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="b97ef-122">ポインター型</span><span class="sxs-lookup"><span data-stu-id="b97ef-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="b97ef-123">型</span><span class="sxs-lookup"><span data-stu-id="b97ef-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="b97ef-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="b97ef-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="b97ef-125">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="b97ef-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="b97ef-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="b97ef-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
