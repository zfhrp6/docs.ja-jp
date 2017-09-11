---
title: "配列での foreach の使用 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], foreach
- foreach statement [C#], using with arrays
ms.assetid: 5f2da2a9-1f56-4de5-94cc-e07f4f7a0244
caps.latest.revision: 14
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
ms.openlocfilehash: a1d0b704233b110b5f499b8186a4a901f9b5408f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="using-foreach-with-arrays-c-programming-guide"></a><span data-ttu-id="e31fb-102">配列での foreach の使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e31fb-102">Using foreach with Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="e31fb-103">C# には、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントも用意されています。</span><span class="sxs-lookup"><span data-stu-id="e31fb-103">C# also provides the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span> <span data-ttu-id="e31fb-104">このステートメントでは、配列または任意の列挙可能なコレクションの要素の反復処理を簡単に、また安全に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e31fb-104">This statement provides a simple, clean way to iterate through the elements of an array or any enumerable collection.</span></span> <span data-ttu-id="e31fb-105">`foreach` ステートメントは、配列またはコレクション型の列挙子から返される順序で要素を処理します。これは通常、ゼロ番目の要素から最後の要素までです。</span><span class="sxs-lookup"><span data-stu-id="e31fb-105">The `foreach` statement processes elements in the order returned by the array or collection type’s enumerator, which is usually from the 0th element to the last.</span></span> <span data-ttu-id="e31fb-106">たとえば、次のコードは `numbers` という配列を作成し、`foreach` ステートメントで配列内の反復処理を行います。</span><span class="sxs-lookup"><span data-stu-id="e31fb-106">For example, the following code creates an array called `numbers` and iterates through it with the `foreach` statement:</span></span>  
  
 <span data-ttu-id="e31fb-107">[!code-cs[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e31fb-107">[!code-cs[csProgGuideArrays#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="e31fb-108">多次元配列を使用する場合は、同じメソッドを使用して配列要素を反復処理できます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e31fb-108">With multidimensional arrays, you can use the same method to iterate through the elements, for example:</span></span>  
  
 <span data-ttu-id="e31fb-109">[!code-cs[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="e31fb-109">[!code-cs[csProgGuideArrays#29](../../../csharp/programming-guide/arrays/codesnippet/CSharp/using-foreach-with-arrays_2.cs)]</span></span>  
  
 <span data-ttu-id="e31fb-110">ただし、多次元配列では、入れ子になった [for](../../../csharp/language-reference/keywords/for.md) ループを使用した方が配列要素をより厳密に制御できます。</span><span class="sxs-lookup"><span data-stu-id="e31fb-110">However, with multidimensional arrays, using a nested [for](../../../csharp/language-reference/keywords/for.md) loop gives you more control over the array elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e31fb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="e31fb-111">See Also</span></span>  
 <span data-ttu-id="e31fb-112"><xref:System.Array></span><span class="sxs-lookup"><span data-stu-id="e31fb-112"><xref:System.Array></span></span>   
 <span data-ttu-id="e31fb-113">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e31fb-113">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e31fb-114">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="e31fb-114">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="e31fb-115">[1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="e31fb-115">[Single-Dimensional Arrays](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md) </span></span>  
 <span data-ttu-id="e31fb-116">[多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="e31fb-116">[Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) </span></span>  
 [<span data-ttu-id="e31fb-117">ジャグ配列</span><span class="sxs-lookup"><span data-stu-id="e31fb-117">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)

