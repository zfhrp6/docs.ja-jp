---
title: "1 次元配列 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
caps.latest.revision: 18
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
ms.openlocfilehash: cc42640715274b89c4c4a12ced8c0ae6af603318
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="cfbd6-102">1 次元配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="cfbd6-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="cfbd6-103">次の例のように、5 つの整数の 1 次元配列を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 <span data-ttu-id="cfbd6-104">[!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cfbd6-104">[!code-cs[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="cfbd6-105">この配列は、`array[0]` から `array[4]` の要素を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-105">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="cfbd6-106">[new](../../../csharp/language-reference/keywords/new.md) 演算子を使用して、配列を作成し、配列要素を既定値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-106">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="cfbd6-107">この例では、すべての配列要素はゼロに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-107">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="cfbd6-108">同じ方法では、文字列要素を格納する配列を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-108">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="cfbd6-109">例:</span><span class="sxs-lookup"><span data-stu-id="cfbd6-109">For example:</span></span>  
  
 <span data-ttu-id="cfbd6-110">[!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="cfbd6-110">[!code-cs[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]</span></span>  
  
## <a name="array-initialization"></a><span data-ttu-id="cfbd6-111">配列の初期化</span><span class="sxs-lookup"><span data-stu-id="cfbd6-111">Array Initialization</span></span>  
 <span data-ttu-id="cfbd6-112">宣言時に配列を初期化することができます。この場合、初期化リスト内の要素の数によって次元が既に提供されているので、次元指定子は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-112">It is possible to initialize an array upon declaration, in which case, the rank specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="cfbd6-113">例:</span><span class="sxs-lookup"><span data-stu-id="cfbd6-113">For example:</span></span>  
  
 <span data-ttu-id="cfbd6-114">[!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="cfbd6-114">[!code-cs[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]</span></span>  
  
 <span data-ttu-id="cfbd6-115">文字列の配列は、同じ方法で初期化できます。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-115">A string array can be initialized in the same way.</span></span> <span data-ttu-id="cfbd6-116">配列の各要素が曜日の名前で初期化される文字列配列の宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-116">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
  
 <span data-ttu-id="cfbd6-117">[!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="cfbd6-117">[!code-cs[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]</span></span>  
  
 <span data-ttu-id="cfbd6-118">宣言時に配列を初期化する場合は、次のショートカットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-118">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 <span data-ttu-id="cfbd6-119">[!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="cfbd6-119">[!code-cs[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]</span></span>  
  
 <span data-ttu-id="cfbd6-120">初期化せずに配列変数を宣言できますが、配列をこの変数に割り当てるときに、`new` 演算子を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-120">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="cfbd6-121">例:</span><span class="sxs-lookup"><span data-stu-id="cfbd6-121">For example:</span></span>  
  
 <span data-ttu-id="cfbd6-122">[!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="cfbd6-122">[!code-cs[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]</span></span>  
  
 <span data-ttu-id="cfbd6-123">C# 3.0 で暗黙的に型指定される配列が導入されます。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-123">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="cfbd6-124">詳細については、「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-124">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="cfbd6-125">値の型と参照型の配列</span><span class="sxs-lookup"><span data-stu-id="cfbd6-125">Value Type and Reference Type Arrays</span></span>  
 <span data-ttu-id="cfbd6-126">次の配列の宣言を検討してみます。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-126">Consider the following array declaration:</span></span>  
  
 <span data-ttu-id="cfbd6-127">[!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="cfbd6-127">[!code-cs[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]</span></span>  
  
 <span data-ttu-id="cfbd6-128">このステートメントの結果は、`SomeType` が値型か参照型かによって決まります。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-128">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="cfbd6-129">値型の場合、ステートメントはそれそれが型 `SomeType` である 10 個の要素の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-129">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="cfbd6-130">`SomeType` が参照型の場合、ステートメントは、それぞれが null 参照に初期化される 10 個の要素の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-130">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="cfbd6-131">値型と参照型の詳細については、「[型](../../../csharp/language-reference/keywords/types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfbd6-131">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfbd6-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfbd6-132">See Also</span></span>  
 <span data-ttu-id="cfbd6-133"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="cfbd6-133"><xref:System.Array></span></span>   
 <span data-ttu-id="cfbd6-134">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cfbd6-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="cfbd6-135">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="cfbd6-135">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="cfbd6-136">[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="cfbd6-136">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="cfbd6-137">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="cfbd6-137">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

