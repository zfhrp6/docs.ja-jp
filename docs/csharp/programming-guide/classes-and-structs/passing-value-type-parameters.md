---
title: "値型パラメーターの引き渡し (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- method parameters [C#], value types
- parameters [C#], value
ms.assetid: 193ab86f-5f9b-4359-ac29-7cdf8afad3a6
caps.latest.revision: 17
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
ms.openlocfilehash: a3377630fc4294831f6b9d66a69377aa42d973f1
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="passing-value-type-parameters-c-programming-guide"></a><span data-ttu-id="dc30b-102">値型パラメーターの引き渡し (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="dc30b-102">Passing Value-Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="dc30b-103">データへの参照を含む[参照型](../../../csharp/language-reference/keywords/reference-types.md)変数とは対照的に、[値型](../../../csharp/language-reference/keywords/value-types.md)変数にはデータが直接含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc30b-103">A [value-type](../../../csharp/language-reference/keywords/value-types.md) variable contains its data directly as opposed to a [reference-type](../../../csharp/language-reference/keywords/reference-types.md) variable, which contains a reference to its data.</span></span> <span data-ttu-id="dc30b-104">値型変数を値渡しでメソッドに渡すと、変数のコピーがメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="dc30b-104">Passing a value-type variable to a method by value means passing a copy of the variable to the method.</span></span> <span data-ttu-id="dc30b-105">メソッド内部で生じるパラメーターに対する変更の影響は、引数の変数に格納されている元のデータには及びません。</span><span class="sxs-lookup"><span data-stu-id="dc30b-105">Any changes to the parameter that take place inside the method have no affect on the original data stored in the argument variable.</span></span> <span data-ttu-id="dc30b-106">呼び出したメソッドでパラメーターの値を変更する場合は、[ref](../../../csharp/language-reference/keywords/ref.md) キーワードまたは [out](../../../csharp/language-reference/keywords/out.md) キーワードを使用して、参照渡しでそのメソッドを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc30b-106">If you want the called method to change the value of the parameter, you must pass it by reference, using the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) keyword.</span></span> <span data-ttu-id="dc30b-107">わかりやすくするために、次の例では `ref` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="dc30b-107">For simplicity, the following examples use `ref`.</span></span>  
  
## <a name="passing-value-types-by-value"></a><span data-ttu-id="dc30b-108">値渡しによる値型の引き渡し</span><span class="sxs-lookup"><span data-stu-id="dc30b-108">Passing Value Types by Value</span></span>  
 <span data-ttu-id="dc30b-109">次の例では、値型のパラメーターを値渡しで渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="dc30b-109">The following example demonstrates passing value-type parameters by value.</span></span> <span data-ttu-id="dc30b-110">変数 `n` を、値渡しでメソッド `SquareIt` に渡します。</span><span class="sxs-lookup"><span data-stu-id="dc30b-110">The variable `n` is passed by value to the method `SquareIt`.</span></span> <span data-ttu-id="dc30b-111">メソッド内で生じた変更が、変数の元の値に影響することはありません。</span><span class="sxs-lookup"><span data-stu-id="dc30b-111">Any changes that take place inside the method have no affect on the original value of the variable.</span></span>  
  
 <span data-ttu-id="dc30b-112">[!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc30b-112">[!code-cs[csProgGuideParameters#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="dc30b-113">変数 `n` は値型です。</span><span class="sxs-lookup"><span data-stu-id="dc30b-113">The variable `n` is a value type.</span></span> <span data-ttu-id="dc30b-114">この変数には、そのデータである値 `5` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dc30b-114">It contains its data, the value `5`.</span></span> <span data-ttu-id="dc30b-115">`SquareIt` を呼び出すと、`n` の内容がパラメーター `x` にコピーされ、このパラメーターがメソッド内で 2 乗されます。</span><span class="sxs-lookup"><span data-stu-id="dc30b-115">When `SquareIt` is invoked, the contents of `n` are copied into the parameter `x`, which is squared inside the method.</span></span> <span data-ttu-id="dc30b-116">ただし、`Main` 内の `n` の値は、`SquareIt` メソッドを呼び出した後でも以前の値と同じままです。</span><span class="sxs-lookup"><span data-stu-id="dc30b-116">In `Main`, however, the value of `n` is the same after calling the `SquareIt` method as it was before.</span></span> <span data-ttu-id="dc30b-117">メソッド内で生じた変更の影響は、ローカル変数 `x` にのみ及びます。</span><span class="sxs-lookup"><span data-stu-id="dc30b-117">The change that takes place inside the method only affects the local variable `x`.</span></span>  
  
## <a name="passing-value-types-by-reference"></a><span data-ttu-id="dc30b-118">参照渡しによる値型の引き渡し</span><span class="sxs-lookup"><span data-stu-id="dc30b-118">Passing Value Types by Reference</span></span>  
 <span data-ttu-id="dc30b-119">次の例は、`ref` パラメーターとして引数を渡す点を除いて上記の例と同じです。</span><span class="sxs-lookup"><span data-stu-id="dc30b-119">The following example is the same as the previous example, except that the argument is passed as a `ref` parameter.</span></span> <span data-ttu-id="dc30b-120">基になる引数 `n` の値は、メソッド内で `x` が変更されると変わります。</span><span class="sxs-lookup"><span data-stu-id="dc30b-120">The value of the underlying argument, `n`, is changed when `x` is changed in the method.</span></span>  
  
 <span data-ttu-id="dc30b-121">[!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc30b-121">[!code-cs[csProgGuideParameters#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_2.cs)]</span></span>  
  
 <span data-ttu-id="dc30b-122">この例では、`n` の値が渡されるのではなく、`n` への参照が渡されています。</span><span class="sxs-lookup"><span data-stu-id="dc30b-122">In this example, it is not the value of `n` that is passed; rather, a reference to `n` is passed.</span></span> <span data-ttu-id="dc30b-123">つまり、パラメーター `x` は [int](../../../csharp/language-reference/keywords/int.md) ではなく、`int` への参照 (この場合は `n` への参照) となります。</span><span class="sxs-lookup"><span data-stu-id="dc30b-123">The parameter `x` is not an [int](../../../csharp/language-reference/keywords/int.md); it is a reference to an `int`, in this case, a reference to `n`.</span></span> <span data-ttu-id="dc30b-124">したがって、メソッド内で `x` が 2 乗された場合、`x` の参照先である `n` が実際に2乗されます。</span><span class="sxs-lookup"><span data-stu-id="dc30b-124">Therefore, when `x` is squared inside the method, what actually is squared is what `x` refers to, `n`.</span></span>  
  
## <a name="swapping-value-types"></a><span data-ttu-id="dc30b-125">値型のスワップ</span><span class="sxs-lookup"><span data-stu-id="dc30b-125">Swapping Value Types</span></span>  
 <span data-ttu-id="dc30b-126">引数の値を変更する一般的な例としてスワップ メソッドがあります。この方法では、2 つの変数をメソッドに渡してから、メソッドにより変数の中身を交換します。</span><span class="sxs-lookup"><span data-stu-id="dc30b-126">A common example of changing the values of arguments is a swap method, where you pass two variables to the method, and the method swaps their contents.</span></span> <span data-ttu-id="dc30b-127">スワップ メソッドへの引数の引き渡しは、参照渡しで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc30b-127">You must pass the arguments to the swap method by reference.</span></span> <span data-ttu-id="dc30b-128">このようにしないと、メソッド内でパラメーターのローカル コピーどうしが交換され、呼び出し元のメソッドでは変更が行われません。</span><span class="sxs-lookup"><span data-stu-id="dc30b-128">Otherwise, you swap local copies of the parameters inside the method, and no change occurs in the calling method.</span></span> <span data-ttu-id="dc30b-129">次の例では、整数値が入れ替えられます。</span><span class="sxs-lookup"><span data-stu-id="dc30b-129">The following example swaps integer values.</span></span>  
  
 <span data-ttu-id="dc30b-130">[!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc30b-130">[!code-cs[csProgGuideParameters#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_3.cs)]</span></span>  
  
 <span data-ttu-id="dc30b-131">`SwapByRef` メソッドを呼び出す場合は、次の例に示すように呼び出しで `ref` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="dc30b-131">When you call the `SwapByRef` method, use the `ref` keyword in the call, as shown in the following example.</span></span>  
  
 <span data-ttu-id="dc30b-132">[!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="dc30b-132">[!code-cs[csProgGuideParameters#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-value-type-parameters_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc30b-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc30b-133">See Also</span></span>  
 <span data-ttu-id="dc30b-134">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="dc30b-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="dc30b-135">[パラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="dc30b-135">[Passing Parameters](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md) </span></span>  
 [<span data-ttu-id="dc30b-136">参照型パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="dc30b-136">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)

