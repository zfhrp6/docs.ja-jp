---
title: "多次元配列 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
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
ms.openlocfilehash: 0203046e2038e97cf791141f6863fd8940b22ea4
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="3731a-102">多次元配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="3731a-102">Multidimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="3731a-103">配列は 1 つ以上の配列を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="3731a-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="3731a-104">たとえば、次の宣言は、4 行と 2 列の 2 次元の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="3731a-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 <span data-ttu-id="3731a-105">[!code-cs[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3731a-105">[!code-cs[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="3731a-106">次の宣言は、4、2、3 の 3 次元配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="3731a-106">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 <span data-ttu-id="3731a-107">[!code-cs[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="3731a-107">[!code-cs[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]</span></span>  
  
## <a name="array-initialization"></a><span data-ttu-id="3731a-108">配列の初期化</span><span class="sxs-lookup"><span data-stu-id="3731a-108">Array Initialization</span></span>  
 <span data-ttu-id="3731a-109">次の例に示すように、宣言時に配列を初期化することができます。</span><span class="sxs-lookup"><span data-stu-id="3731a-109">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 <span data-ttu-id="3731a-110">[!code-cs[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="3731a-110">[!code-cs[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]</span></span>  
  
 <span data-ttu-id="3731a-111">また、順位を指定せずに配列を初期化することもできます。</span><span class="sxs-lookup"><span data-stu-id="3731a-111">You also can initialize the array without specifying the rank.</span></span>  
  
 <span data-ttu-id="3731a-112">[!code-cs[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="3731a-112">[!code-cs[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]</span></span>  
  
 <span data-ttu-id="3731a-113">初期化せずに配列変数を宣言する場合、`new` 演算子を使用して配列を変数に代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3731a-113">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="3731a-114">`new` の使用を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="3731a-114">The use of `new` is shown in the following example.</span></span>  
  
 <span data-ttu-id="3731a-115">[!code-cs[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="3731a-115">[!code-cs[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]</span></span>  
  
 <span data-ttu-id="3731a-116">次の例では、特定の配列要素に値を代入します。</span><span class="sxs-lookup"><span data-stu-id="3731a-116">The following example assigns a value to a particular array element.</span></span>  
  
 <span data-ttu-id="3731a-117">[!code-cs[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="3731a-117">[!code-cs[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]</span></span>  
  
 <span data-ttu-id="3731a-118">同様に、次の例では、特定の配列要素の値を取得して、それを変数 `elementValue` に代入します。</span><span class="sxs-lookup"><span data-stu-id="3731a-118">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 <span data-ttu-id="3731a-119">[!code-cs[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="3731a-119">[!code-cs[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]</span></span>  
  
 <span data-ttu-id="3731a-120">次のコード例では、配列要素を既定値に初期化します (ジャグ配列を除く)。</span><span class="sxs-lookup"><span data-stu-id="3731a-120">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 <span data-ttu-id="3731a-121">[!code-cs[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="3731a-121">[!code-cs[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3731a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3731a-122">See Also</span></span>  
 <span data-ttu-id="3731a-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3731a-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3731a-124">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="3731a-124">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="3731a-125">[1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="3731a-125">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 [<span data-ttu-id="3731a-126">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="3731a-126">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

