---
title: "参照型パラメーターの引き渡し (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- method parameters [C#], reference types
- parameters [C#], reference
ms.assetid: 9e6eb65c-942e-48ab-920a-b7ba9df4ea20
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 282929d82822f81f12dae91d2f422da51a0f43e5
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="passing-reference-type-parameters-c-programming-guide"></a><span data-ttu-id="b575f-102">参照型パラメーターの引き渡し (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b575f-102">Passing Reference-Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="b575f-103">[型参照](../../../csharp/language-reference/keywords/reference-types.md)の変数には、そのデータは直接含まれず、そのデータへの参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b575f-103">A variable of a [reference type](../../../csharp/language-reference/keywords/reference-types.md) does not contain its data directly; it contains a reference to its data.</span></span> <span data-ttu-id="b575f-104">値で参照型パラメーターを渡す場合、クラス メンバーの値など、参照先オブジェクトに属するデータを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="b575f-104">When you pass a reference-type parameter by value, it is possible to change the data belonging to the referenced object, such as the value of a class member.</span></span> <span data-ttu-id="b575f-105">ただし、参照自体の値を変更することはできません。たとえば、同じ参照を使用して、新しいクラスのメモリを割り当て、ブロックの外側で永続化させることはできません。</span><span class="sxs-lookup"><span data-stu-id="b575f-105">However, you cannot change the value of the reference itself; for example, you cannot use the same reference to allocate memory for a new class and have it persist outside the method.</span></span> <span data-ttu-id="b575f-106">これを行うには、[ref](../../../csharp/language-reference/keywords/ref.md) または [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) キーワードを使用してパラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="b575f-106">To do that, pass the parameter using the [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) keyword.</span></span> <span data-ttu-id="b575f-107">わかりやすくするために、次の例では `ref` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b575f-107">For simplicity, the following examples use `ref`.</span></span>  
  
## <a name="passing-reference-types-by-value"></a><span data-ttu-id="b575f-108">値渡しによる参照型の引き渡し</span><span class="sxs-lookup"><span data-stu-id="b575f-108">Passing Reference Types by Value</span></span>  
 <span data-ttu-id="b575f-109">次の例では、参照型のパラメーター `arr` を値渡しで `Change` メソッドに渡す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b575f-109">The following example demonstrates passing a reference-type parameter, `arr`, by value, to a method, `Change`.</span></span> <span data-ttu-id="b575f-110">このパラメーターは `arr` への参照であるため、配列要素の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="b575f-110">Because the parameter is a reference to `arr`, it is possible to change the values of the array elements.</span></span> <span data-ttu-id="b575f-111">ただし、別のメモリ位置へのパラメーターの再割り当ては、メソッドの内部でのみ機能し、元の変数 `arr` には影響しません。</span><span class="sxs-lookup"><span data-stu-id="b575f-111">However, the attempt to reassign the parameter to a different memory location only works inside the method and does not affect the original variable, `arr`.</span></span>  
  
 [!code-csharp[csProgGuideParameters#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_1.cs)]  
  
 <span data-ttu-id="b575f-112">前の例では、`ref` パラメーターなしで参照型の配列 `arr` がメソッドに渡されています。</span><span class="sxs-lookup"><span data-stu-id="b575f-112">In the preceding example, the array, `arr`, which is a reference type, is passed to the method without the `ref` parameter.</span></span> <span data-ttu-id="b575f-113">このような場合は、`arr` を指す参照のコピーがメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="b575f-113">In such a case, a copy of the reference, which points to `arr`, is passed to the method.</span></span> <span data-ttu-id="b575f-114">出力は、メソッドが配列要素のコンテンツを変更できることを示しています。この場合は `1` から `888` に変更します。</span><span class="sxs-lookup"><span data-stu-id="b575f-114">The output shows that it is possible for the method to change the contents of an array element, in this case from `1` to `888`.</span></span> <span data-ttu-id="b575f-115">ただし、`Change` メソッド内で [new](../../../csharp/language-reference/keywords/new.md) 演算子を使用して新しいメモリ領域を割り当てると、変数 `pArray` が新しい配列を参照します。</span><span class="sxs-lookup"><span data-stu-id="b575f-115">However, allocating a new portion of memory by using the [new](../../../csharp/language-reference/keywords/new.md) operator inside the `Change` method makes the variable `pArray` reference a new array.</span></span> <span data-ttu-id="b575f-116">このため、この後のすべての変更が、`Main` の内部で作成される元の配列 `arr` に影響しません。</span><span class="sxs-lookup"><span data-stu-id="b575f-116">Thus, any changes after that will not affect the original array, `arr`, which is created inside `Main`.</span></span> <span data-ttu-id="b575f-117">実際、この例では、2 つの配列が作成されます。1 つは `Main` の内部で、もう 1 つは `Change` メソッド内で作成されます。</span><span class="sxs-lookup"><span data-stu-id="b575f-117">In fact, two arrays are created in this example, one inside `Main` and one inside the `Change` method.</span></span>  
  
## <a name="passing-reference-types-by-reference"></a><span data-ttu-id="b575f-118">参照渡しによる参照型の引き渡し</span><span class="sxs-lookup"><span data-stu-id="b575f-118">Passing Reference Types by Reference</span></span>  
 <span data-ttu-id="b575f-119">次の例は、前の例と同じですが、`ref` キーワードがメソッド ヘッダーと呼び出しに追加されている点が異なります。</span><span class="sxs-lookup"><span data-stu-id="b575f-119">The following example is the same as the previous example, except that the `ref` keyword is added to the method header and call.</span></span> <span data-ttu-id="b575f-120">メソッドで行われるすべての変更が、呼び出し元のプログラム内の元の変数に影響します。</span><span class="sxs-lookup"><span data-stu-id="b575f-120">Any changes that take place in the method affect the original variable in the calling program.</span></span>  
  
 [!code-csharp[csProgGuideParameters#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_2.cs)]  
  
 <span data-ttu-id="b575f-121">メソッド内で行われるすべての変更は、`Main` の元の配列に影響します。</span><span class="sxs-lookup"><span data-stu-id="b575f-121">All of the changes that take place inside the method affect the original array in `Main`.</span></span> <span data-ttu-id="b575f-122">実際、元の配列は `new` 演算子を使用して再割り当てされます。</span><span class="sxs-lookup"><span data-stu-id="b575f-122">In fact, the original array is reallocated using the `new` operator.</span></span> <span data-ttu-id="b575f-123">したがって、`Change` メソッドを呼び出した後、`arr` へのすべての参照が、`Change` メソッドで作成された 5 つの要素を持つ配列を指します。</span><span class="sxs-lookup"><span data-stu-id="b575f-123">Thus, after calling the `Change` method, any reference to `arr` points to the five-element array, which is created in the `Change` method.</span></span>  
  
## <a name="swapping-two-strings"></a><span data-ttu-id="b575f-124">2 つの文字列のスワップ</span><span class="sxs-lookup"><span data-stu-id="b575f-124">Swapping Two Strings</span></span>  
 <span data-ttu-id="b575f-125">文字列のスワップは、参照渡しで参照型パラメーターを渡す良い例です。</span><span class="sxs-lookup"><span data-stu-id="b575f-125">Swapping strings is a good example of passing reference-type parameters by reference.</span></span> <span data-ttu-id="b575f-126">例では、2 つの文字列 `str1` と `str2` が `Main` で初期化され、`ref` キーワードで変更されたパラメーターとして `SwapStrings` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="b575f-126">In the example, two strings, `str1` and `str2`, are initialized in `Main` and passed to the `SwapStrings` method as parameters modified by the `ref` keyword.</span></span> <span data-ttu-id="b575f-127">2 つの文字列は、メソッド内と `Main` 内でスワップされます。</span><span class="sxs-lookup"><span data-stu-id="b575f-127">The two strings are swapped inside the method and inside `Main` as well.</span></span>  
  
 [!code-csharp[csProgGuideParameters#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-reference-type-parameters_3.cs)]  
  
 <span data-ttu-id="b575f-128">この例では、呼び出し元のプログラム内の変数に影響を与えるため、参照渡しでパラメーターを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b575f-128">In this example, the parameters need to be passed by reference to affect the variables in the calling program.</span></span> <span data-ttu-id="b575f-129">メソッド ヘッダーと、メソッドの呼び出しの両方から `ref` キーワードを削除すると、呼び出し元プログラムで変更は行われません。</span><span class="sxs-lookup"><span data-stu-id="b575f-129">If you remove the `ref` keyword from both the method header and the method call, no changes will take place in the calling program.</span></span>  
  
 <span data-ttu-id="b575f-130">文字列の詳細については、「[文字列](../../../csharp/language-reference/keywords/string.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b575f-130">For more information about strings, see [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b575f-131">参照</span><span class="sxs-lookup"><span data-stu-id="b575f-131">See Also</span></span>  
 [<span data-ttu-id="b575f-132">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b575f-132">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b575f-133">パラメーターの引き渡し</span><span class="sxs-lookup"><span data-stu-id="b575f-133">Passing Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)  
 [<span data-ttu-id="b575f-134">ref と out を使用した配列の引き渡し</span><span class="sxs-lookup"><span data-stu-id="b575f-134">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)  
 [<span data-ttu-id="b575f-135">ref</span><span class="sxs-lookup"><span data-stu-id="b575f-135">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="b575f-136">in</span><span class="sxs-lookup"><span data-stu-id="b575f-136">in</span></span>](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
 [<span data-ttu-id="b575f-137">out</span><span class="sxs-lookup"><span data-stu-id="b575f-137">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
 [<span data-ttu-id="b575f-138">参照型</span><span class="sxs-lookup"><span data-stu-id="b575f-138">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)
