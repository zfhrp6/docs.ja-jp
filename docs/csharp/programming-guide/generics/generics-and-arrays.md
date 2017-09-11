---
title: "ジェネリックと配列 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
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
ms.openlocfilehash: 46cea2733504e56aec5e65a4c9a8b655bc9431cf
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="c1690-102">ジェネリックと配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c1690-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="c1690-103">C# 2.0 以降、下限が 0 の一次元配列は自動的に <xref:System.Collections.Generic.IList%601> を実装します。</span><span class="sxs-lookup"><span data-stu-id="c1690-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="c1690-104">これにより、同じコードで配列や他のコレクション型を反復処理できるジェネリック メソッドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c1690-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="c1690-105">この手法は主に、コレクションのデータを読み込むときに便利です。</span><span class="sxs-lookup"><span data-stu-id="c1690-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="c1690-106"><xref:System.Collections.Generic.IList%601> インターフェイスを使用して配列の要素を追加したり、削除したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c1690-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="c1690-107">このコンテキストの配列で、<xref:System.Collections.Generic.IList%601.RemoveAt%2A> のような、<xref:System.Collections.Generic.IList%601> メソッドを呼び出そうとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c1690-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="c1690-108">次のコード例からは、<xref:System.Collections.Generic.IList%601> 入力パラメーターを受け取る単一のジェネリック メソッドがリストと配列 (この例では、整数の配列) の両方を反復処理できることがわかります。</span><span class="sxs-lookup"><span data-stu-id="c1690-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 <span data-ttu-id="c1690-109">[!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c1690-109">[!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1690-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1690-110">See Also</span></span>  
 <span data-ttu-id="c1690-111"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="c1690-111"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="c1690-112">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1690-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c1690-113">[ジェネリック](../../../csharp/programming-guide/generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1690-113">[Generics](../../../csharp/programming-guide/generics/index.md) </span></span>  
 <span data-ttu-id="c1690-114">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="c1690-114">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 [<span data-ttu-id="c1690-115">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="c1690-115">Generics</span></span>](~/docs/standard/generics/index.md)

