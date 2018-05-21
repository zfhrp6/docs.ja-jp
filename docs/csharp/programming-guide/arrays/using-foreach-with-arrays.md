---
title: 配列での foreach の使用 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
ms.openlocfilehash: 8511d9dd3b7155d2f6bca229f264071b54ed173b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="9a797-102">配列での foreach の使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9a797-102">Using foreach with Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="9a797-103">C# には、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントも用意されています。</span><span class="sxs-lookup"><span data-stu-id="9a797-103">C# also provides the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="9a797-104">このステートメントでは、配列または任意の列挙可能なコレクションの要素の反復処理を簡単に、また安全に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9a797-104">This statement provides a simple, clean way to iterate through the elements of an array or any enumerable collection.</span></span> <span data-ttu-id="9a797-105">`foreach` ステートメントは、配列またはコレクション型の列挙子から返される順序で要素を処理します。これは通常、ゼロ番目の要素から最後の要素までです。</span><span class="sxs-lookup"><span data-stu-id="9a797-105">The `foreach` statement processes elements in the order returned by the array or collection type’s enumerator, which is usually from the 0th element to the last.</span></span> <span data-ttu-id="9a797-106">たとえば、次のコードは `numbers` という配列を作成し、`foreach` ステートメントで配列内の反復処理を行います。</span><span class="sxs-lookup"><span data-stu-id="9a797-106">For example, the following code creates an array called `numbers` and iterates through it with the `foreach` statement:</span></span>  
  
 [!code-csharp[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]  
  
 <span data-ttu-id="9a797-107">多次元配列を使用する場合は、同じメソッドを使用して配列要素を反復処理できます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="9a797-107">With multidimensional arrays, you can use the same method to iterate through the elements, for example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]  
  
 <span data-ttu-id="9a797-108">ただし、多次元配列では、入れ子になった [for](../../../csharp/language-reference/keywords/for.md) ループを使用した方が配列要素をより厳密に制御できます。</span><span class="sxs-lookup"><span data-stu-id="9a797-108">However, with multidimensional arrays, using a nested [for](../../../csharp/language-reference/keywords/for.md) loop gives you more control over the array elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a797-109">参照</span><span class="sxs-lookup"><span data-stu-id="9a797-109">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="9a797-110">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9a797-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9a797-111">配列</span><span class="sxs-lookup"><span data-stu-id="9a797-111">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="9a797-112">1 次元配列</span><span class="sxs-lookup"><span data-stu-id="9a797-112">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="9a797-113">多次元配列</span><span class="sxs-lookup"><span data-stu-id="9a797-113">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="9a797-114">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="9a797-114">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
