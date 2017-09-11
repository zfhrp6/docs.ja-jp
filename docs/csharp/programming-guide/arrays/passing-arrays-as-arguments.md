---
title: "引数としての配列の受け渡し (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
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
ms.openlocfilehash: 5e83c0c119bc1448be76f83416098158c7f5d684
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="0bf69-102">引数としての配列の受け渡し (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="0bf69-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="0bf69-103">配列は、引数としてメソッド パラメーターに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0bf69-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="0bf69-104">配列は参照型であるため、メソッドは要素の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0bf69-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="0bf69-105">1 次元配列を引数として渡す</span><span class="sxs-lookup"><span data-stu-id="0bf69-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="0bf69-106">初期化された 1 次元配列をメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0bf69-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="0bf69-107">たとえば、次のステートメントは、配列を print メソッドに送信します。</span><span class="sxs-lookup"><span data-stu-id="0bf69-107">For example, the following statement sends an array to a print method.</span></span>  
  
 <span data-ttu-id="0bf69-108">[!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bf69-108">[!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]</span></span>  
  
 <span data-ttu-id="0bf69-109">次のコードは、print メソッドの実装の一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="0bf69-109">The following code shows a partial implementation of the print method.</span></span>  
  
 <span data-ttu-id="0bf69-110">[!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bf69-110">[!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]</span></span>  
  
 <span data-ttu-id="0bf69-111">次の例に示すように、一度に新しい配列を初期化して渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0bf69-111">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 <span data-ttu-id="0bf69-112">[!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bf69-112">[!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf69-113">例</span><span class="sxs-lookup"><span data-stu-id="0bf69-113">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0bf69-114">説明</span><span class="sxs-lookup"><span data-stu-id="0bf69-114">Description</span></span>  
 <span data-ttu-id="0bf69-115">次の例では、文字列の配列が初期化され、引数として文字列の `PrintArray` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="0bf69-115">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="0bf69-116">このメソッドは、配列の要素を表示します。</span><span class="sxs-lookup"><span data-stu-id="0bf69-116">The method displays the elements of the array.</span></span> <span data-ttu-id="0bf69-117">次に、値渡しで配列引数を送信することで配列要素の変更が妨げられないことを示すため、メソッド `ChangeArray` と `ChangeArrayElement` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0bf69-117">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0bf69-118">コード</span><span class="sxs-lookup"><span data-stu-id="0bf69-118">Code</span></span>  
 <span data-ttu-id="0bf69-119">[!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bf69-119">[!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]</span></span>  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="0bf69-120">多次元配列を引数として渡す</span><span class="sxs-lookup"><span data-stu-id="0bf69-120">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="0bf69-121">1 次元配列を渡すのと同じ方法で、初期化された多次元配列をメソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="0bf69-121">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 <span data-ttu-id="0bf69-122">[!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bf69-122">[!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]</span></span>  
  
 <span data-ttu-id="0bf69-123">次のコードに、2 次元配列を引数として受け取る print メソッドの宣言の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="0bf69-123">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 <span data-ttu-id="0bf69-124">[!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bf69-124">[!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]</span></span>  
  
 <span data-ttu-id="0bf69-125">次の例に示すように、一度に新しい配列を初期化して渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0bf69-125">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 <span data-ttu-id="0bf69-126">[!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bf69-126">[!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf69-127">例</span><span class="sxs-lookup"><span data-stu-id="0bf69-127">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0bf69-128">説明</span><span class="sxs-lookup"><span data-stu-id="0bf69-128">Description</span></span>  
 <span data-ttu-id="0bf69-129">次の例では、整数の 2 次元配列が初期化され、`Print2DArray` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="0bf69-129">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="0bf69-130">このメソッドは、配列の要素を表示します。</span><span class="sxs-lookup"><span data-stu-id="0bf69-130">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0bf69-131">コード</span><span class="sxs-lookup"><span data-stu-id="0bf69-131">Code</span></span>  
 <span data-ttu-id="0bf69-132">[!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="0bf69-132">[!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bf69-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="0bf69-133">See Also</span></span>  
 <span data-ttu-id="0bf69-134">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bf69-134">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0bf69-135">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="0bf69-135">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="0bf69-136">[1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="0bf69-136">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="0bf69-137">[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="0bf69-137">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="0bf69-138">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="0bf69-138">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

