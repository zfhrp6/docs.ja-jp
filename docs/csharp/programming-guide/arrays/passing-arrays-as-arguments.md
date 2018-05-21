---
title: 引数としての配列の受け渡し (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: d863cdc33a8a1a844aabbea9ba5876614e6e8dba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="cca7e-102">引数としての配列の受け渡し (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="cca7e-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="cca7e-103">配列は、引数としてメソッド パラメーターに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="cca7e-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="cca7e-104">配列は参照型であるため、メソッドは要素の値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="cca7e-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="cca7e-105">1 次元配列を引数として渡す</span><span class="sxs-lookup"><span data-stu-id="cca7e-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="cca7e-106">初期化された 1 次元配列をメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="cca7e-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="cca7e-107">たとえば、次のステートメントは、配列を print メソッドに送信します。</span><span class="sxs-lookup"><span data-stu-id="cca7e-107">For example, the following statement sends an array to a print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 <span data-ttu-id="cca7e-108">次のコードは、print メソッドの実装の一部を示しています。</span><span class="sxs-lookup"><span data-stu-id="cca7e-108">The following code shows a partial implementation of the print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 <span data-ttu-id="cca7e-109">次の例に示すように、一度に新しい配列を初期化して渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="cca7e-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="cca7e-110">例</span><span class="sxs-lookup"><span data-stu-id="cca7e-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cca7e-111">説明</span><span class="sxs-lookup"><span data-stu-id="cca7e-111">Description</span></span>  
 <span data-ttu-id="cca7e-112">次の例では、文字列の配列が初期化され、引数として文字列の `PrintArray` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="cca7e-112">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="cca7e-113">このメソッドは、配列の要素を表示します。</span><span class="sxs-lookup"><span data-stu-id="cca7e-113">The method displays the elements of the array.</span></span> <span data-ttu-id="cca7e-114">次に、値渡しで配列引数を送信することで配列要素の変更が妨げられないことを示すため、メソッド `ChangeArray` と `ChangeArrayElement` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cca7e-114">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cca7e-115">コード</span><span class="sxs-lookup"><span data-stu-id="cca7e-115">Code</span></span>  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="cca7e-116">多次元配列を引数として渡す</span><span class="sxs-lookup"><span data-stu-id="cca7e-116">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="cca7e-117">1 次元配列を渡すのと同じ方法で、初期化された多次元配列をメソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="cca7e-117">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 <span data-ttu-id="cca7e-118">次のコードに、2 次元配列を引数として受け取る print メソッドの宣言の一部を示します。</span><span class="sxs-lookup"><span data-stu-id="cca7e-118">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 <span data-ttu-id="cca7e-119">次の例に示すように、一度に新しい配列を初期化して渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="cca7e-119">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="cca7e-120">例</span><span class="sxs-lookup"><span data-stu-id="cca7e-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cca7e-121">説明</span><span class="sxs-lookup"><span data-stu-id="cca7e-121">Description</span></span>  
 <span data-ttu-id="cca7e-122">次の例では、整数の 2 次元配列が初期化され、`Print2DArray` メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="cca7e-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="cca7e-123">このメソッドは、配列の要素を表示します。</span><span class="sxs-lookup"><span data-stu-id="cca7e-123">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cca7e-124">コード</span><span class="sxs-lookup"><span data-stu-id="cca7e-124">Code</span></span>  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cca7e-125">参照</span><span class="sxs-lookup"><span data-stu-id="cca7e-125">See Also</span></span>  
 [<span data-ttu-id="cca7e-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="cca7e-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cca7e-127">配列</span><span class="sxs-lookup"><span data-stu-id="cca7e-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="cca7e-128">1 次元配列</span><span class="sxs-lookup"><span data-stu-id="cca7e-128">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="cca7e-129">多次元配列</span><span class="sxs-lookup"><span data-stu-id="cca7e-129">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="cca7e-130">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="cca7e-130">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
